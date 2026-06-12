---
title: "Ubuntu 14.10 on NUC incorrectly detecting monitor size"
date: 2015-01-22
forum: Multimedia Software
---

### Post by axe87 on 2015-01-22
Hardware: NUC D54250WYKH, HD Graphics 5000, HDMI connection
Monitor: Samsung SyncMaster 2494HM

I've just installed Ubuntu 14.10 on a new NUC and it's clear that the monitor is not being detected correctly. The first sign of a problem was that the window is cropped / slightly zoomed so that the Unity menu bars are off the screen. I fixed this by setting the monitor "image Size" to "Just Scan" instead of "Wide". The other noticeable issue is that the definition of images on the screen is not clear.

When I check the display settings in system settings the monitor size is detected as 7" and not 24". Digging deeper (I checked /var/log/Xorg.0.log) it looks like the EDID settings are not being returned correctly from the device.

My old system (AMD 64, with RADEON graphics card, DVI connection) running 14.10 recognizes the monitor fine.

I'm wondering if this is an HDMI issue as I've seen elsewhere ([https://bbs.archlinux.org/viewtopic.php?id=171374](https://bbs.archlinux.org/viewtopic.php?id=171374)) or graphics processor / driver. Not sure where to look next.

---

### Post by oldfred on 2015-01-22
That is the very new Broadwell chip.

But 14.10 should have a new enough kernel, but perhaps you need the very newest kernel & drivers using a ppa as discussed below.

 Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

---

### Post by axe87 on 2015-01-22
Oldrfred, thanks but the D54250WYKH is still with the Haswell chip.

I just tried plugging in to my 46" Sony TV. The resolution is definitely better (not quite perfect) and no issue with the cropping. However the NUC did think that the Sony was a 72" TV.

I've seen in various placed that displayport may be a better bet than HDMI. May be I'll try and get a displayport cable.

---

### Post by oldfred on 2015-01-22
This is now all older info, but some may still apply.

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

---

### Post by philhughes on 2015-01-23
If you are not already doing so, you could try using a DVI connection at the monitor with the HDMI at the NUC.

---

### Post by axe87 on 2015-01-24
Progress, it seems I needed to change the AV mode on the monitor to off, as per here [http://www.overclock.net/t/579884/samsung-2494hm-resolution-problems#post_7519751](http://www.overclock.net/t/579884/samsung-2494hm-resolution-problems#post_7519751). This addresses the cropping problem and resolution and colours now look pretty good.

However, the display still shows up as being 7". This is good enough for now.

Intel support pointed to some Intel linus drivers, but there not yet available for 14.10.

---

