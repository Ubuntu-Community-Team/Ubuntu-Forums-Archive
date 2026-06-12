---
title: "ubuntu freezes"
date: 2011-07-15
forum: Multimedia Software
---

### Post by mr alex on 2011-07-15
I have been running Ubuntu successfully as my sole operating system since 2006 with amazing results... that is until I build my latest pc. ever since I've had ubuntu has frozen with nothing in particular prompting it, the screen just locks and I have to hard boot to start it up again.

I have an AMD 64bit processor witch used the onboard graphics card, I have recently bought an ATI Radeon HD 5450 card but the symptoms are still there in exactly the same way. I am completely lost with how to address this problem, does anyway have any advice or similar problems??

Many thanks!

---

### Post by dabl on 2011-07-15
First, don't hard reset.  Use Alt-SysRq R S E I U B (the so-called magic sysrq reset).  It's much better for your filesystem.


Try disabling Desktop Effects, for starters, and see if the freeze behavior stops.

Run "top" in a terminal window, and put it where you can see it.  When the system "freezes", observe which process is using all the CPU resources (probably it will be xorg).


Finally, Ubuntu wiki:  [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

