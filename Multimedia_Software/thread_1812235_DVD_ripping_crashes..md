---
title: "DVD ripping crashes."
date: 2011-07-26
forum: Multimedia Software
---

### Post by VeeDubb on 2011-07-26
I'm sure this is posted and answered elsewhere, but every search I've tried has resulted in such a flood of hits that I can't seem to filter it down to something useful.

I'm running 11.04 64bit, and every single DVD ripping/converting program I've tried to use, fails.

At first, I thought it might be related to memory issues, because it's such a memory intensive process, but 10 passes with memtest found no errors. 

I've tried handbreak, dvd-rip, and several others, and I get the same results every time:  The process starts, it gets partway through (anywhere from 2%-25%) and then it crashes.  Each program provides different crash reports, but ultimately, none of them are useful.  Usually it's not much more than a segfault.

This is with multiple disks, which all play just fine through any media app I want, and around the time 11.04 came out, I was able to rip DVDs just fine.

Where do I go from here?

---

### Post by orange2k on 2011-07-26
Maybe the problem is that youre using the unstable Ubuntu release...

You said yourself that in 11.04 you had no problems...

---

### Post by 4Orbs on 2011-07-26
Two possibilities: overheating or maybe you don't have enough free-space remaining in your /home partition. The dvd rippers I have used, all of them recommend at least 10 gb free-space.

---

### Post by VeeDubb on 2011-07-26
> **orange2k said:**
> Maybe the problem is that youre using the unstable Ubuntu release...

You said yourself that in 11.04 you had no problems...

I'm still running 11.04.  When I first upgraded to 11.04, it worked great.  Now, a few months later, it does not work.  That means that if it's a software issue it's something I've installed or updated since the original upgrade to 11.04.  Unfortunately, I can't think of anything I've installed that should cause a problem.

> **4Orbs said:**
> Two possibilities: overheating or maybe you don't have enough free-space remaining in your /home partition. The dvd rippers I have used, all of them recommend at least 10 gb free-space.

I'll put up some monitors to keep an eye on the heat, but I don't think that's it because the system doesn't crash; just the DVD ripping.  As for free space, I have 564.4GB of free space in my home partition, and 126.3GB in /

---

### Post by rthaski on 2011-07-26
hey guys. I am having trouble creating a dvd iso from any software I have. So far I have tried Devede, Bombono and K3 all keep freezing up. I have used devede in the past, even as early as yesterday, but now it just keeps freezing up. Any Ideas would be greatly appreciated. I am using Ubuntu 10.10. Thanks

---

### Post by 4Orbs on 2011-07-26
@VeeDubb - Maybe check your Software Sources to make sure all the repositories are for Natty rather than Maverick (or other).

---

### Post by VeeDubb on 2011-07-27
I got it fixed after some playing with sensors.  I noticed that when it failed, mem usage was only at ~37%, and varied from crash to crash.

However, every time it failed, CPU usage was 97% on all 4 cores.  

I went back into my bios settings and disabled my** very conservativ**e overclocking, and it all works fine now.  Sadly, that tells me that things are not well with my CPU, but at least I can rip again.  It just takes a tiny bit longer.

---

