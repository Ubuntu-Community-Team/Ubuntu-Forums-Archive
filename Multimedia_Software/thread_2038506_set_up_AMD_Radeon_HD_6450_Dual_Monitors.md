---
title: "set up AMD Radeon HD 6450 Dual Monitors"
date: 2012-08-06
forum: Multimedia Software
---

### Post by RogerMon on 2012-08-06
Hi Everyone,

I'm a seasoned Windows developer just starting into Ubuntu.  After some doing, I've got Ubuntu running on my workstation, but the video doesn't work right.  It is split across the two monitors and the mouse clicking is way off.  When I start up with the "nomodeset" option.  The GUI comes up okay on one monitor, but it's the wrong one.  

I've looked around and found a couple threads about setting up video, but I'm hoping someone can help with my video card and dual monitors.

I'll appreciate all help.


Thanks,

Roger

---

### Post by QIII on 2012-08-06
Please see the ATI wiki in my signature and look for the section in the table of contents called "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)".

You can then use the Catalyst Control Center to properly configure your monitors.

---

### Post by RogerMon on 2012-08-11
Hi,

I finally got some time this morning to get back to Ubuntu.  I installed the proprietary driver and that works.  It says I must mirror the two monitors, due to resolution incompatibilities, but I'm okay with that!  

Thanks for your help.

Roger :)

---

### Post by RogerMon on 2012-08-11
Well actually, It is not fixed.  It only booted up correctly, once.  I can't get it to boot at all without the proprietary driver.  I found that by adding the nomodeset argument to GRUB temporarily , allows a correct boot with usable video.  So, I followed the instructions to permanently change the GRUB configuration.  But after booting it STILL finds no usable file system.

Here's the kicker.  When I open the GRUB file at boot time I see the nomodeset argument in the file. typing Ctl-X brings up a good boot without changing anything.  But if I let GRUB go on its own.  I get the no file system error.

I suppose I can interrupt GRUB every time I boot into Ubuntu, but I shouldn't have to do that.

If anyone has any ideas, I'd like to hear them.

Thanks,

Roger

---

