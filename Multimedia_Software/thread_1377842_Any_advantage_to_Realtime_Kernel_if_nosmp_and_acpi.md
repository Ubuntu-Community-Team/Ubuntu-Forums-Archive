---
title: "Any advantage to Realtime Kernel if nosmp and acpi=0ff?"
date: 2010-01-10
forum: Multimedia Software
---

### Post by VideoRoy on 2010-01-10
Just got Studio 9.10 running and the RT kernel installed.  I have a Prescott P4 3.2ghz (hyperthreading) and i encountered what looks like a common freeze problem.  I am guessing my cpu will not be supported in the RT kernel since it is pretty old now.

I added nosmp acpi=off during boot at the Grub2 menu and it booted fine and I was able to capture some video great.

My questions is, if I remove the smp support by using the nosmp option, do I still benefit from the RT kernel or would I do just as well with the generic kernel I have installed?

Eventually I will upgrade do a new system board and processor but for now I just got some life back in this one by switching to Linux :D

---

### Post by VideoRoy on 2010-01-10
The RT kernel has been running pretty well all day with "nosmp acpi=off".  Update Manager just updated the standard kernel so I am going to test that one out and see if it really makes a difference whether I use the RT kernel or not.

I do most video editing and not much audio wondering if that makes a difference for the kernel.  I have seen lots of posts about people needing RT for audio work.

---

### Post by markbuntu on 2010-01-11
The rt patch basically changes the kernel scheduling parameters. This allows audio apps to gain high priority and faster response from the system so they do not glitch or drop out when used in a live environment. 

If you are not doing any live recording or performance this may not be absolutely necessary for your work.

---

### Post by VideoRoy on 2010-01-11
> **markbuntu said:**
> The rt patch basically changes the kernel scheduling parameters. This allows audio apps to gain high priority and faster response from the system so they do not glitch or drop out when used in a live environment. 

If you are not doing any live recording or performance this may not be absolutely necessary for your work.

Thanks for the reply markbuntu!  I am kind of thinking along those same lines.  I have to say regardless of the kernel I am running Ubuntu has really put some life back into my old P4 3.2ghz computer.  I have been using it for years on XP and Pinnacle Studio but I really trying to get the same work done on linux.

Speed will not be my issue for now!

---

