---
title: "Memory usage shown in &quot;Machine Status&quot; not accurate?"
date: 2011-03-27
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-03-27
Hello there,

When I open Mythfrontend, and view the System Information (Information Center > System), it shows the following for memory under the "Machine Status"

RAM: 2.0 GB total, 1.9 GB used, 68 MB (or 3.38%) free.

However, when I check Task Manager (under Xubuntu Desktop) it shows my memory usage as 15% (this is with Mythfrontend and firefox open).

So, my questions are these:

1.  Which is accurate?
2.  Why is there a difference between the two (like an 84% difference)?
3.  Is this issue fixed (or changed) in newer versions? I'm currently running 0.23-fixes (the default in the Mythbuntu 10.10 installation)
4.  Do I need to worry about memory (in other words, will this affect recording and transposing afterwards)?

Thanks, and have a great day:)
Patrick.

---

### Post by LowSky on 2011-03-28
> **PatrickD-52761 said:**
> 

1.  Which is accurate?

Technically both
> **PatrickD-52761 said:**
> 2.  Why is there a difference between the two (like an 84% difference)?
Task Manager accounts for Ram used by current programs, Mythfrontend is accounting for RAM that is also being cached. Cached information is only being saved on RAM because you may have used a program recently and closed it. Caching the data means that program can open quicker later.

> **PatrickD-52761 said:**
> 3.  Is this issue fixed (or changed) in newer versions? I'm currently running 0.23-fixes (the default in the Mythbuntu 10.10 installation)
Nope still around.. not really a problem to worry about

> **PatrickD-52761 said:**
> 4.  Do I need to worry about memory (in other words, will this affect recording and transposing afterwards)?

No, RAM use is based on availability and need. When people add more memory the "speed increase" they see is from the ability to cache more. 2Gb is fine on a Linux machine. Now if you run out of RAM the machine can always use SWAP on the hard drive. Not as fast but useful if needed. So don't worry.

---

