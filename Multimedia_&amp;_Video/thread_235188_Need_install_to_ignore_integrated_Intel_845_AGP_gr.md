---
title: "Need install to ignore integrated Intel 845 AGP graphics"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by DaveTheBatMan on 2006-08-12
Hi --

I've been trying off-and-on to get the 6.06LTS desktop to install on my PC. I have a Gigabyte motherboard with integrated Intel 845 AGP graphics. I also have a Radeon 9250 PCI graphics card, and have my BIOS set to "use the PCI graphics first" (that is how the BIOS phrases any reference to 'disable onboard graphics').

When I try to install 6.06LTS WITHOUT the PCI card (with the BIOS set to use the onboard AGP first), it works. When I have the PCI card in, and the BIOS set to use IT first, the install freezes.

I've tried specifying various resolutions, safe mode(s), etc., and it ALWAYS locks up (at different places), but I *have* been able to glean a BIT of information.

Apparently, the install (incorrectly) LOADS (or tries to load) the AGP drivers, then loads (or tries to load) the PCI drivers, then ultimately craps out.

So, the root of the problem is that the install is *incorrectly* trying to access-and-use BOTH the (disabled) onboard AGP and the (enabled) PCI card.

How can I get Ubuntu installed on my system?  Obviously, I need some sort of way to tell Ubuntu installer to ignore the integrated Intel AGP and use the Radeon 9250 PCI, but I don't know how...  ?

(My system is working fine with 4 other, different OS's installed, by the way.)

Thanks a mil!

[email]DaveTheBatMan@Yahoo.com[/email]

---

### Post by tseliot on 2006-08-13
Unplug your ATI card and install Ubuntu.

Then follow this guide (which works also on ATI cards):
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

