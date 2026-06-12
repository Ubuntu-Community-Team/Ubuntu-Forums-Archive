---
title: "No sound after mute and unmute"
date: 2011-08-09
forum: Multimedia Software
---

### Post by Vojta_prasil on 2011-08-09
Hi guys,
I'd like to ask you for help with my sound issue. Everything worked fine until I tried mute volume. When I unmute volume again I don't hear anything.

I've got the same problem in the past on Ubuntu 10 and I solved it by reinstallation newer version (11.04). Now I'd like to find a bit smarter solution than stupid compete reinstallation. 

I've checked all devices in alsamixer and none seems to be muted or set to 0 volume.

Next thing I've tried was removing and reinstallation alsa* packages but it still does not work /-:

here is result of alsa-info script

[http://www.alsa-project.org/db/?f=7ee6508832b2e9e30437b0955577502b71801438]("http://www.alsa-project.org/db/?f=7ee6508832b2e9e30437b0955577502b71801438")

Thanks in advance for any help
Vojta

---

### Post by SnickerSnack on 2012-02-07
Did you find a solution to this?  I have the same problem, though I haven't tried anything to fix it yet.

The only info I could find was this: [http://ubuntuforums.org/showthread.php?t=1905657](http://ubuntuforums.org/showthread.php?t=1905657)

As far as I can tell, pressing the mute button on the keyboard mutes both the alsa and pulse mixers, while pressing again only unmutes the alsa mixer, leaving no sound coming out of the speakers.  The same happens when muting/unmuting the alsa mixer via the gui.  This may be a problem with alsa communicating with pulse rather than with xfce.

Edit: You might want to keep an eye on this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818)

Edit: Solution found in post #3 of this thread: [https://bugs.launchpad.net/xfce4-volumed/+bug/883485/](https://bugs.launchpad.net/xfce4-volumed/+bug/883485/)

The solution in post #2 also reportedly works.

---

