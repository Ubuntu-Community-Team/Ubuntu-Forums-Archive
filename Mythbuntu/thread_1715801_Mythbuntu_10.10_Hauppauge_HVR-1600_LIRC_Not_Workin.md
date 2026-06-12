---
title: "Mythbuntu 10.10 Hauppauge HVR-1600 LIRC Not Working"
date: 2011-03-27
forum: Mythbuntu
---

### Post by chewtoy11 on 2011-03-27
I recently upgraded to Mythbuntu 10.10 (x64) from Mythbuntu 9.04 (x64).  By upgrade, I actually mean performed a clean install and then imported my recordings and database.

I tried enabling LIRC support and selecting the "Hauppauge TV card" option in the Mythbuntu Command Center.  No complaints upon doing this, except the remote never becomes responsive.  I've tried running irw, but I never get ANY signs of activity -- the prompt just sits there until I Ctrl-C out of irw.  I'm using the default Hauppauge remote (the super-common gray one with the red, green, blue, and yellow buttons).  More specifically, I'm using a Logitech Harmony 520 remote which is programmed to emulate that remote.  Batteries are fresh, and the remote worked perfectly until the upgrade.

Out of the box, it worked fine on Mythbuntu 9.04.

I'm guessing this is an LIRC driver difference, but don't know where to begin to resolve it.  When I look in the /etc/hardware.conf file, there is a reference to a /dev/lirc0 device, which does NOT exist.  There is a /dev/lircd device, but modifying the hardware.conf to point to that doesn't work either.

I saw something about switching to the lirc_zilog driver, instead of lirc_i2c -- but I know my system has always used lirc_i2c in the past.

Any ideas or links that outline the specific problem and fix would be greatly appreciated.

Here is a rundown of the system (in case there is a known hardware incompatibility):

Intel DG41TY Motherboard
Intel Pentium E5200 (Dual-core)
2GB DDR-2 RAM
Seagate 1TB SATA-II Drive
Hauppauge HVR-1600 PCI (not Express) card
XFX Nvidia GeForce 9400 PCIe
Soundblaster Live! PCI (using digital coax output)

---

### Post by chewtoy11 on 2011-03-27
Sorry, I did actually find the solution, but can confirm for other HVR-1600 owners that this worked for me!

[http://ubuntuforums.org/showpost.php?p=10059393&postcount=20](http://ubuntuforums.org/showpost.php?p=10059393&postcount=20)

Following this post verbatim got my system up and working!

---

