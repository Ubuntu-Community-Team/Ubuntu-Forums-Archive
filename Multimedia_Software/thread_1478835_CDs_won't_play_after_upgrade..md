---
title: "CDs won't play after upgrade."
date: 2010-05-10
forum: Multimedia Software
---

### Post by Ulfgeir on 2010-05-10
Hey gang,

I recently upgraded from 9.10 to 10.04, and everything is fine with the exception that discs of any kind (CD, DVD, blank CD, etc) aren't being recognized by the system.

I have two optical drives, one a basic CD/DVD player and the other a CD/DVD burner, and both are giving the same results. The disc will spin up and the drive light comes on, but as far as Gnome is concerned, nothing is in the tray.

Both drives appear under "Computer" along with my hard disk and USB pen drives, but the media inserted never pops up as recognized under Rhythmbox, Banshee, or Brasero. It's like nothing is even in the tray.

After searching around, I read that fstab is no longer supposed to contain a mount point entry for the CDROM, but that such an entry is left remaining if you upgrade rather than doing a fresh install. It was suggested in one of these threads that commenting out the line concerned with the CDROM would solve this very issue, which apparently several people have tangled with.

So I commented out the line related to the CDROM in fstab and rebooted, but the problem persists.  Any other ideas, guys?

---

### Post by Ulfgeir on 2010-05-11
I never was able to fix this issue.  I finally just decided to do a fresh install and see if that resolved the problem, but even after wiping the drive and putting a new install of 10.04 (only Kubuntu this time, for a change of pace) I still got the same results.

So I'm just going to wash my hands of Lucid for the time being, and I've re-installed 9.10, which always worked great for me.  I might give 10.04 another shot once further updates have been released.

---

### Post by jacrider on 2010-05-11
I ended up doing the same thing ... 9.10 has been working well for me, so I re-installed and will wait until this gets fixed.

This sounds like a common problem.

---

### Post by Ulfgeir on 2010-06-08
Okay, it's been a month since I last attempted to solve this issue, and I've decided to give 10.04 another try.  My drives starting working fine again when I went back to 9.10, so this definitely isn't a hardware problem.  I've now done a fresh install of 10.04, not just the upgrade, and I'm using GNOME as my GUI.

I figured after a month's worth of updates this problem might have been resolved, but even after bringing my install completely up to date, the problem with discs not mounting persists just like it did before.  I also searched around on the forums here and couldn't find any new solutions offered.

Has anyone figured out how to fix this?  I'm resolved to stick with 10.04 this time, so switching back is not an option.  Any help is appreciated guys.


EDIT: I've also noticed a new symptom.  If I leave a music CD in the tray and reboot, a 'music disc' icon does appear on the desktop.  But if I try to launch Rhythmbox to see if it will play, the program takes nearly 30 seconds to launch -- much longer than usual.  And it's window only appears after the 'music disc' icon disappears.  So the icon is there on boot up if the disc is left in the tray, but disappears in response to launching Rhythmbox.  I've also tried double-clicking on the desktop icon for the disc, but nothing happens.  And if I remove the disc and re-insert it, no icon appears at all.

---

### Post by jjloupe on 2010-06-09
Myself and others are having this problem, but no one has had an answer.

---

### Post by Ulfgeir on 2010-06-10
I've submitted the problem to launchpad, and after I followed a couple of their diagnostic steps, they decided it might be a problem either with the kernel or drivers.  Now they want me to follow a few more steps to help further diagnose the problem, so hopefully we'll have a solution available in the near future.

[https://bugs.launchpad.net/bugs/591243](https://bugs.launchpad.net/bugs/591243)

---

### Post by Ulfgeir on 2010-06-30
The most recent updates for 10.04 seem to have resolved this issue for me.  My discs are mounting normally again.

---

### Post by ankit singh on 2010-06-30
mine still a problem,cd's aren't mounting.However they show unusual behaviour if mounted.They tray comes out in midst of any operation.

---

