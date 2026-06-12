---
title: "ATI Xorg downgrade?"
date: 2010-09-04
forum: Multimedia Software
---

### Post by Virtual62 on 2010-09-04
Hi

 I just installed a fresh copy of lucid lynx and Im having issues with the Catalyst Control Center as my ATI graphics card cannot be recognized by it. Apparently the new flgrx drivers are not compatible with my graphics card:

**02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV516  [Radeon X1300/X1550 Series] [1002:7183]**

Although I have seen a post on a related thread, which suggested i should download an older version of the driver, I encountered issues with installing it as my existing version of Xorg is 7.6 and the driver is only compatible for up to 7.4

I would like to know the following:

1. is it possible to remove the existing xorg core with out any risks of ubuntu crashing
2. is it possible to install an older version of xorg? if so how?


if anyone can help me with this issue, it would be much appreciated

---

### Post by sagi456 on 2010-09-27
I have the same problem. I also tried using the open source drivers and they partially work, but I still cannot use compiz no matter what I do. And "yes" I have tried disabling kms with radeon modeset=0 but when I do so it doesn't change anything..

Does anyone has a clue on how to fix it??

---

### Post by Mark Phelps on 2010-09-27
> **sagi456 said:**
> I have the same problem. I also tried using the open source drivers and they partially work, but I still cannot use compiz no matter what I do. And "yes" I have tried disabling kms with radeon modeset=0 but when I do so it doesn't change anything..

Does anyone has a clue on how to fix it??

You've hihacked a thread dealing with something totally unrelated to your problem -- which has absolutely nothing to do with downgrading the version of X-server.

If you want responses, you need to start your own thread with a proper title -- and stop hijacking other people's threads.

---

### Post by sagi456 on 2010-09-30
> **Mark Phelps said:**
> You've hihacked a thread dealing with something totally unrelated to your problem -- which has absolutely nothing to do with downgrading the version of X-server.

If you want responses, you need to start your own thread with a proper title -- and stop hijacking other people's threads.


No I don't think I have. I have exactly the same problem as Virtual62. I only added the fact that, since the ATI Linux proprietary driver didn't work for me, I have also tried the Open source drivers - which appearantly are not efficient enough in my case[SIZE=2][/SIZE]...

I am also interested in a possible XORG downgrade solution...

---

### Post by Yellow Pasque on 2010-09-30
Xorg downgrade worked with jaunty/9.04, but it won't work on newer buntus. Try something else..

---

