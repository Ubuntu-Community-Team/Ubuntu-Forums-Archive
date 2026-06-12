---
title: "Enabling visual effects for linux"
date: 2009-08-03
forum: Multimedia Software
---

### Post by Hell's Quookie on 2009-08-03
I've tried everything. I'm running Ubuntu Jaunty Jackelope on 8GB. The graphics card is 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03). I have the compiz config settings manager and have looked up this issue with several other forums. Seriously no idea why nothing is working. Would greatly appreciate some help....

---

### Post by pastalavista on 2009-08-03
> **Hell's Quookie said:**
> I've tried everything. I'm running Ubuntu Jaunty Jackelope on 8GB. The graphics card is 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03). I have the compiz config settings manager and have looked up this issue with several other forums. Seriously no idea why nothing is working. Would greatly appreciate some help....

By "nothing is working" do you mean you can't enable visual effects in System> Preferences> Appearance? Do you have anything in System> Administration> Hardware Drivers enabled? Is 8GB ram or HD?

---

### Post by Hell's Quookie on 2009-08-03
Yes, I still can't enable the visual effects and it's an 8GB hard drive.

---

### Post by pastalavista on 2009-08-03
Integrated graphics on a computer old enough to have a hard drive that small probably isn't powerful enough for visual effects. You didn't answer about any restricted hardware drivers. Also, have you enabled third-party software in your software resources? (sys->admin menu)

---

### Post by Hell's Quookie on 2009-08-03
it's a fairly new computer, Vista crashed so I loaded Linux. Broadcom B43 wireless driver is enabled.

---

### Post by pastalavista on 2009-08-03
Ah, then it must be an SSD? Anyway, this [bug post]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094") might help. Launchpad is the first place you should check if you suspect you have a bug.

---

