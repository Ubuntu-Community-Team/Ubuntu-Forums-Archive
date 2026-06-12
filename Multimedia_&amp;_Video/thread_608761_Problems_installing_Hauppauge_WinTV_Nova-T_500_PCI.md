---
title: "Problems installing Hauppauge WinTV Nova-T 500 PCI on gutsy 7.10"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by DannyBoy99 on 2007-11-10
Hi all, 

I am a real beginner with Ubuntu and am struggling to install my Hauppauge WinTV Nova-T 500 PCI card. I have followed the instructions on [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI) to the letter, but at the end when I use the command: sudo modprobe dvb-usb-dib0700 all I see in dmesg is the following: 

[  162.540000] dib0700: loaded with support for 5 different device-types
[  162.540000] usbcore: registered new interface driver dvb_usb_dib0700

I am expecting some entries identifying my card I assume?

In device manager I see the card as an unknown device under SBx00 PCI to PCI bridge (I assume its the TV card as the vendor is Hauppage). I have rebooted and cold booted but still the same...

Any help would be greatly appreciated, but please take it slow as I only have very basic Linux skills!

---

