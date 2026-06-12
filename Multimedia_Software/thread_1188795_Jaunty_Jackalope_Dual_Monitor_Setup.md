---
title: "Jaunty Jackalope Dual Monitor Setup?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by Si Deacon on 2009-06-16
Hi all,

I've tried in vain to get two monitors working off a Matrox g550 agp card.
I posted a thread on this subject but it soon ran dry.

A two (or more) monitor setup is such an invaluable aid for 'newbies' like me, particularly when working from a guide or tutorial.

I'm happy to replace the video card if necessary to achieve this.

Can anyone suggest a setup that is certain to work and relatively easy to implement?

---

### Post by SteveDee on 2009-06-16
> **Si Deacon said:**
> Hi all,

I've tried in vain to get two monitors working off a Matrox g550 agp card.
I posted a thread on this subject but it soon ran dry.

A two (or more) monitor setup is such an invaluable aid for 'newbies' like me, particularly when working from a guide or tutorial.

I'm happy to replace the video card if necessary to achieve this.

Can anyone suggest a setup that is certain to work and relatively easy to implement?

Well its not too difficult to get a second screen (TV) working with an Nvidia graphics card as there is an application for configuration: nvidia-settings (gui name "NVIDIA X Server Settings").
I'm using an Nvidia/GeForce 7300LE with the version 180 driver.

---

### Post by NcScZ on 2009-06-16
The nvidia-settings will allow you to set up dual monitors very easy. BUT using dual monitors has caused problems on my AMD Athlon 64 X2 Dual Core system. The set up & configuration is very easy compared to earlier UBUNTU releases for setting up the dual screens. 

But I have a problem with the system locking up when using dual monitors. When it does lock, there is no disk activity, it will not respond to any keyboard input & is not accessible via a network ssh connection. A similar system using a Intel P4 processor does not have the same problems. So if you are using something other than the AMD 64 X2 the nvidia cards work very well. If you have to purchase one, I have seen them as low as $29 (buy.com).

The same system will run flawlessly using Ubuntu & a single monitor or using WinXP (single or dual monitor). The video card is GeForce 7300 SE / 7200 GS. I borrowed a different NVIDIA card from co-worker but it had the same results.

I am currently using the 180.60 driver & have tried the different drivers available thru the repositories. There is a later driver (V185.18.14)  at nvidia.com but an install of that was unsuccessfull and I ran out of time to try and debug. So for the moment I am forced back onto XP until time permits me to seek a solution.

---

### Post by Si Deacon on 2009-06-16
Thanks for the contributions,

NVIDIA seems to crop up a lot in multi-display threads, I'll look further along that path I think.

---

