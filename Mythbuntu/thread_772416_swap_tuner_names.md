---
title: "swap tuner names"
date: 2008-04-28
forum: Mythbuntu
---

### Post by thusgaard on 2008-04-28
Hi

I just mounted a second tuner. This gives me a new and unexpected problem. 

The new tuner is detected as /dev/video0 (the address of the old tuner).
The old tuner is now known as /dev/video1.

For my purpose I need /dev/video1 to become /dev/video0 and /dev/video0 to become /dev/video1. 

If this is not possible how do I get all of my programs to move from one tuner to the other. 

Kind regards J;-)

---

### Post by justanotherhack on 2008-04-28
Just a wild guess without checking it... but couldn't you just rewrite the entries in the database?

---

### Post by thusgaard on 2008-04-28
> **justanotherhack said:**
> Just a wild guess without checking it... but couldn't you just rewrite the entries in the database?

Probably, but how? And wouldn't that be quite a task for a linux (and myth) n00b?

I could also just swap the 2 tuners and would probably solve the problem, but the other solution would be nice too. 

Another guess is that the tuners can be mounted and unmounted like harddisks, and if this is true I know the solution, but how to make it permanent.

J;-)

---

