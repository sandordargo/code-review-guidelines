## Items to be checked in a code review

Reviewing code is difficult, and in fact, it's a very broad task. According to my bosses, I'm considered a good code reviewer, but still, I think my effectiveness could be improved a lot. I think that following checklists, just in most of the cases, can be a huge help.

Now obviously, some of those checklists and/or tasks will be language specific. However what makes a review a good one are most of the time the same concepts, regardless of the language used.

These lists are mostly here to give you some ideas, they are far from complete. Feel free to use them, update them, personalize them or just let them inspire you to come up with completely new ones.

I think that one reviewer shouldn't use them all, but maybe just a few. But if you have separate checklists, it's easy to share the tasks.

Please, consider that not all the checklists are there to be used for all the code reviews. If the pull request is a really small bugfix, just correcting an off-by-one in a condition, it will not require checking the design of the whole domain.

### Full process checklist

This one focuses on some foundational characteristics of a pull request. I didn't add to the list, but you should make sure that the new commits don't break the compilation or the tests. Your Continuous Integration pipeline should take care of this, but in case not. Don't forget about it. Otherwise, check these.

* Are new unit/regression tests added?
* Are there new compiler warnings?
* Does the change functionally make sense?
* Are there a lot of dependencies?
* Are the commit message clean?
* ...

### SOLID (object-oriented design) principles checklist
In order to verify the sanity of the design, it's worth to go through the SOLID principles. Most probably it's worth to expand this items, into sublists helping to verify each principle.

* Single responsibility principles
* Open/closed principle
* Liskov substitution principle
* Interface segregation principle
* Dependency inversion principle


### Security checklist
Your application might or might not be security-critical. As soon as it's hacked once or it fails because of some messy input, it will become one... This checklist if usable, should be heavily language dependent, I give you one for C++. A colleague of mine extracted mainly from this [talk on secure programming practices at the NDC Security Conference at 2018](https://www.youtube.com/watch?v=Jh0G_A7iRac)

* Is external input handled properly?
* Are C-style interfaces used?
* Is the `new` operator superfluously used instead of stack allocation?
* Are there lots of (error-prone) size calculations?
* Are pointers used a lot?
* Are shared_ptrs used a lot?
* Are there any threads?
...

### Testing best practices checklist
I hope we all agree that testing is part of a developer's job and if we had a discussion on testing it would be about the different way to do it, not whether we should do it or not. Bad news is that there is no one way fits for all - still I'd advise you to follow the cycle of Test Driven development. Good news is that hopefully on a project there is a common understanding on at least what should be done. If there is none, step in and advocate for testing, gather articles, studies and convince. You'll be much more respected.
Here a few points to clarify in regards of the testing part:

* Are there enough unit tests?
* Are there enough non-regression tests?
* Do tests test one thing?
* Do they have assertions? (A test might have multiple assertions, still logically they assert one thing)
* Are they readable?
* How dates are used? (Fixed vs. generated)
* ...

### Code readability checklist
We - developers - are all authors. If we do an impeccable job, [our code will read like a prose](). I don't say that always reach this goal for the whole codebase, but we should aim for that. The code reviewer has a huge responsibility here. If you are reading a pull request, please think about the following questions:

* Are names meaningful?
* Are classes/functions small enough?
* Does the code "read like a prose"?
* Is the code well-formatted?
* Is there duplicated code?
* ...

### Resource handling checklist, a.k.a. [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization)
This last one is rather language specific. It's not only for C++, but mostly. If you are a C++ developer and you ever fought against dangling pointers, memory leaks and nasty core dumps. You know what I mean. For a non-expert it can be really difficult to spot these issues, but following a helpful checklist  might help you both in pointing out the problematic lines and both in developing the RAII expertise.

* Is object ownership clarified?
* Are objects properly destroyed/ is the memory correctly deallocated?
* Are new fields properly handled?
* Are Fields correctly initialized in the constructors?
* Are comparision operators updated?
* ...
