---
title: "ATI R300 driver on Ubuntu 8.10"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Cali30us on 2009-02-09
This seems to be a problem that affects many others, so I'm hoping someone can help shed some light on this.  My aim is to get Ubuntu 8.10 to work with my video card (ATI Radeon 9500 Pro) so that I can eventually install Compiz (and get those cool video effects).  I have an Asus mb w/ AMD Athlon XP 2400+ CPU.
 
After performing a fresh install of Ubuntu, the generic ATI driver leaves me with a display resolution that I don't want and the only refresh rate is 60Hz (flickers on my CRT). The monitor is listed as Unknown, and clicking on Detect Displays does nothing to change this (I have an NEC Accusync 95F 19" multisync monitor).  Hardware Drivers lists nothing.  I tried installing all ~250 Security and Recommended updates for Ubuntu, but this had no effect.
 
I found [Bug #284408]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408"), dated Oct-08, which says fglrx-installer version 8.543 doesn't work with R300-based adapters (like mine), and to just use the generic driver.
 
But then I found the [ATI Catalyst 9.1 driver]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"), dated 1-29-09, whose [Release Notes ]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf")say "This release of ATI Catalyst™ Linux introduces support for the following new operating system: Ubuntu 8.10 production support."  They provide [installation instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf"), but I found the best instructions at the [Ubuntu Intrepid Installation Guide ]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")for ATI drivers.
 
After following those instructions, though, I still get errors at startup, basically "No Screens Found".  I'm attaching my Xorg.0.log and xorg.conf files so you can see just what's going on.
 
If anyone has an idea how to get this working, I, and the others in the same boat, would be very appreciative.  I'm new to Linux, so it might just be a simple error on my part.
 
Thanks!

---

### Post by DeusEx on 2009-03-26
hello,
I have found that with my Radeon 9500 card the open source radeon drivers work better than the proprietary ones for compiz. Although the TV-out is somewhat troublesome.

---

### Post by Benanov on 2009-04-09
I've had decent result with the FLOSS driver as well until a recent update pushed me back to Mesa. :(

I'm going to try 9.04 beta and see if that's any better.

---

