---
title: "Ati catalyst drivers and hibernation"
date: 2010-10-10
forum: Multimedia Software
---

### Post by dpeter on 2010-10-10
Hi all,
I'm having problems with resuming from hibernation. By the end of resume process, before displaying login window (my screen is locked) my laptop spends a lot of time on reading disk and whole computer really slows down. When I manage to login to system (usually it takes some time to display login window) it keeps reading it for some time. You can compare it to the situation when system runs out of memory and starts using swap.
What's more, with every resume from hibernation it's worse - my computer spends more and more time on reading disk. What I have observed is that after every resume amount of swap memory that is in use increases (I use ```
free -m
``` command).
The same thing happens when I resume from suspended state.

I know that this issue is caused by video driver. I have ATI Radeon HD 3740 card and I'm using catalyst drivers, 10.9 version. It is version with some fixes because original one was broken by some kernel updates (here is more info: [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)). When I used open source drivers resuming from hibernation was really fast:)

I use uswsusp as sleep module (configured in /etc/pm/config.d/00sleep_module). I tried tuxonice too but I got impression that it was even worse :(
I hibernate my machine either from kde's menu or from console:
```
sudo s2disk
```
but effect is always the same.
How can I fix it? Hibernation is very important for me...

My system:
ThinkPad R500, ATI Radeon HD 3470
Kubuntu 10.04 64 bit

---

### Post by mekanix on 2011-01-09
I don't have an answer, but I would like one as well.

---

