---
title: "Asus Xonar Essence ST"
date: 2010-05-29
forum: Multimedia Software
---

### Post by bingcrosby on 2010-05-29
Hello everyone,

According to the alsa website, this card (PCI version) will have driver support in ALSA 1.0.22 or kernel 2.6.33, and I believe Lucid comes with this version of ALSA.

I'm interested if this driver is a advanced as the one for the STX (PCI-E version) as it has been available since ALSA 1.0.20 or kernel 2.6.30.  In particular, does the ST driver have the ability to choose headphone impedance,  the ability to switch the DAC from a sharp to slow roll-off, and also alter the oversampling rate from 64x to 128x?

Any comments and experiences would be greatly appreciated.

Thanks.

---

### Post by drewster1829 on 2010-08-03
Hey, I have the Asus Xonar Essence ST, and it worked out of the box with Alsa 1.0.22, but it didn't have controls to change headphone impedance, changing the DAC rolloff, nor for changing the oversampling rate.

However, Alsa 1.0.23 does.  Here's a [link]("http://ubuntuforums.org/showthread.php?p=6589810") to an upgrade script and instructions for upgrading to 1.0.23.

Then you can use alsamixer in the console to change these settings.

Be careful, though...you might have to troubleshoot when running it, and it could break your sound.  Be sure and backup your system first.  Note that this script will ONLY work on a non-customized kernel.

You'll have to reinstall it every time you upgrade the kernel (in order to install the kernel module).  For me, it worked the first time, but the second time (after a kernel upgrade) it broke it.  I'm working on fixing it right now, and that thread (over 100 pages of replies) has LOTS of troubleshooting information.

Btw, I'm using Ubuntu Lucid (10.04) AMD-64.  Good luck...the Asus Xonar Essence ST is an AWESOME soundcard. :p

Edit:  It didn't work after the kernel upgrade because I didn't recompile with the script, I just tried to install it.  Following the instructions from the BEGINNING made it work perfectly.  Also, all three options are now in alsamixer.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=165365&stc=1&d=1280851912[/IMG]

---

### Post by xwindowsfan on 2011-08-28
what I want to know is, has anybody got the ST Control Center software working under Linux, maybe it's possible with Wine?

any solution for Linux to adjust the card's settings, such as bit rate/depth?

it looks like an awesome card and I will most likely buy one but I'm a lil hesitant because of all the controls I loose out on including the EQ ect.

thanks much.

---

