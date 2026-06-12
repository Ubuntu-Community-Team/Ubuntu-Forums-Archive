---
title: "Xubuntu 15.04 cannot recognize SOME DVDs"
date: 2015-05-06
forum: Multimedia Software
---

### Post by orionds on 2015-05-06
I know there are many posts on DVDs not being read but this a strange, new quirk I found **ONLY for Xubuntu 15.04** (don't know about the other flavors but will try later). The "affected" DVDs **can ALL be recognized in Xubuntu 14.04**.

Since installing Xubuntu 15.04, I have come across 4 to 5 brand new original DVD movies that could not be recognized. If I **reboot with the DVD left in the DVD drive**, the DVD is recognized and shows in the file manager. However, if I eject the DVD and re-insert it - no go - the DVD is again not recognized.

However, to make matters worse, I have come across 2 DVDs that could not be recognized even with rebooting. But, again, in Xubuntu 14.04, these two and all the other "problem" DVDs could be recognized.

So far, in Xubuntu 15.04, I have had this **recognition problem with about** **10% of the DVDs** I inserted.

For the record, I have libdvdread4 installed and have also run the install-css.sh script. The xubuntu-restricted-extras have also been installed. I did exactly the same in Xubuntu 14.04 and all DVDs have been recognized flawlessly. Perhaps, it's the long-term support that makes the difference. This said, I am completely puzzled that **only 15.04 should have this DVD flaw on all the PCs and notebooks** I installed it on (I run a small network in a library).

Have any other Xubuntu 15.04 users had this problem too? You may have to insert maybe up to 20 DVDs to test this.

I am posting this here mainly to bring this to the attention to whoever might read this so that this flaw is not passed on to the following versions of Xubuntu (and possibly even the other flavours).

Of course, if someone has a solution, I would really like to hear it. Many thanks in advance.

---

### Post by kc1di on 2015-05-06
Try using upstart to boot into 15.04 instead of systemd.  If it works with upstart then the problem lies with systemd and you should file a bug report about it.
you can boot with upstart by going to advanced option on the boot screen and selecting boot with upstart.

---

### Post by VMC on 2015-05-06
I've had the same issues, and also some usb flash memory not being recognized. I never thought of booting with just upstart. I'll try that.

---

### Post by orionds on 2015-05-06
I think I did try booting with upstart but can't remember if this worked with the problem DVDs. I will try this again tomorrow when I return to work as the DVDs are there and then post back here with the result.

---

### Post by orionds on 2015-05-06
I tried booting with upstart and the problem DVD still could not be recognized. I then booted into Xubuntu 14.04 and the DVD was recognized.

There were several before this too, so this is not an isolated occurrence.

I would like as many people as possible who have experienced this DVD recognition problem in 15.04 to post here. Thanks.

---

### Post by orionds on 2015-05-06
Just tried with Lubuntu 15.04 - ran the install-css.sh script, installed the lubuntu-restricted-extras, but still no go. When I inserted a "good" DVD, it was recognized but the otherwise-good-in-14.04 problem DVD would not show in Lubuntu 15.04.

Unless, there is something different about the other 15.04 flavours, this DVD bug is in 15.04 or maybe even the newer linux kernel.

---

### Post by kc1di on 2015-05-08
You should report it as a bug on launch pad.

---

### Post by orionds on 2015-05-09
Yes, I will be doing this.

---

### Post by orionds on 2015-05-09
I just posted the bug in Launchpad and also in the answers section of Launchpad to see if anyone might have a solution. One comment there asked why I did not just use 14.04. I replied that it was part of my long-term research for hardware and software planning at the school where I volunteer. So, in case someone may be wondering why here too, here is the explanation / reply I gave:

> I have dual boot on my own PCs / netbooks as well as those that I help to maintain in the small network in my school's library.

The machines all have different hardware configurations and I have tried 15.04 on almost all of them. For those that run stably, I let 15.04 keep running, otherwise I make 14.04 the default boot in grub. So far, 15.04 and 14.04 are running well for the needs of the students that come in.

For the one or two machines where frequent access to DVDs is needed, 14.04 (Trusty) is the default boot.

I try each new version of Ubuntu that comes out to test them and if they prove better than the previous version allowing us to do everything that we need then I make the switch complete.

These tests are also for future development and expansion e.g. tablets and the potential of convergence. This will help us decide our hardware evolution in the future for learning and education - whether to go the tablet route but also allowing the use of a mouse and keyboard, which we have found are vital for student work. The conventional tablet apps and touch keyboard don't cut it when it comes to more complex work and assignments.

Ubuntu / Xubuntu and Lubuntu, in long run too, helps us to keep costs down without having e.g. taking the Apple route while keeping our freedom, so to say.

So, the use and testing of 15.04 is part of our long-term planning as well as here, in this case, contributing to finding bugs for the developers to improve the OS.

I posted the question here to help alert other users to this problem and to share insights / possible solutions. So, I am also posting in the Ubuntu forums.

Overall, I really like 15.04 - it boots faster and shuts down a whole lot faster (like 2 to 3 seconds). It also runs, at least to me, software faster and more smoothly. For example, I am still using (right now) two single-core PCs at home and, for the first time, I have been able to play a full hd (1080p) mp4 or mkv movie smoothly in SM Player and this is was not possibly in previous versions of Xubuntu or Lubuntu. Oh yes, the speed up seems to apply to the Gimp too.

---

### Post by VMC on 2015-05-09
What's the launchpad bug link so we can comment.

---

### Post by markdtuckwell on 2015-11-30
Did you manage to solve this issue?

I have installed Ubuntu 15.04 and I am unable to mount ~20% of commercial DVDs. They can all be opened by other operating systems (Windows 7 in this case) and standalone DVD players.

---

