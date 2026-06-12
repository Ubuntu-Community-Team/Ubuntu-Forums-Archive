---
title: "Starting X locks system"
date: 2008-07-16
forum: Multimedia Software
---

### Post by tm.winston on 2008-07-16
I recently put together what is hopefully to be a silent PC for my wife to browse on, watch MythTV, DVD's and do her emailing.  However, I have a slight problem; starting X locks the system to the point that I have to hit the power button.

I have tried Xubuntu, Ubuntu and Kubutu 8.04, all have the same problem.  I have Kubuntu 8.04 installed, via the alternative CD.  Curiously, Kubuntu 7.10 runs fine until patched, then X locks it up as well.  The machine is up and running like a top currently, with no X running, so I'm reasonably certain that the hardware is stable.  Windows XP ran on it for a couple days.  (I was hoping the issue wasn't related to *buntu.)

I have attached all the files I could think to that might help anyone help me.  logs.tar.bz2 contains dmesg, kdm.log, messages, syslog, Xorg.0.log and Xorg.0.log.old.  I thank you, in advance, for taking the time to look at this issue for me.  And, let me know if there is anything more I need to do.

---

### Post by tm.winston on 2008-07-17
Perhaps, more information is in order?

The machine is based on Via's C3 processor and uses an integrated Via VT8623 video "card."  The machine will boot normally, KDM even starts, it will draw the login screen, and if you're really fast, you can actually log in and KDE starts to load before the machine locks up.  If you do nothing the machine will lock up with the KDM login screen up.  I had thought it might have been something else that had nothing to do with X that just happened to finish loading at about that same time.  However, the machine will boot without X and run just fine for days now.  Also, I booted without X and launched X using "startx" and once again the machine locked up.

Any guidance anyone can offer, either in how to troubleshoot my issue, or possibly how to spiff up my post so it gets more people's attention would be greatly appreciated.

---

### Post by tm.winston on 2008-07-18
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514)

It appears to be a known bug.  Anyone have any idea what my chances are of finding a decent fix?

---

