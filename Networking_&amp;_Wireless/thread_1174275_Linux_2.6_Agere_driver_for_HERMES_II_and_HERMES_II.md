---
title: "Linux 2.6 Agere driver for HERMES II and HERMES II.5 chipsets"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by pe1dnn on 2009-05-30
I have an old laptop that can barely run XP (Celeron 600, 192 MB memory) so I wanted to try Ubuntu. That works great, except there was no driver for my SpeedTouch 110 Wireless Lan card. I still have an Agere driver that more or less worked for the 2.4 kernel but is not functional in the 2.6 kernel.
 
There was a driver by Andrey Borzenkov based on an earlier Agere driver ( 7.1.8 ) that compiled with a few minor changes (for Ubuntu 9.04), but NetworkManager could not make a connection.
 
Using the changes from Andrey's version and the Linux 2.4 Agere driver version 7.22 I build a new driver for Linux 2.6 that runs in Ubuntu 9.04. I also fixed a few problems and added some robustness. NetworkManager works now, as does wpa_supplicant and the iwconfig/iwlist tools.
 
The driver should be able to handle the following cards:
 
HERMES II Card
 
PCMCIA Info: "Agere Systems" "Wireless PC Card Model 0110"
Manufacture ID: 0156,0003
 
HERMES II.5 Card
 
PCMCIA Info: "Linksys" "WCF54G_Wireless-G_CompactFlash_Card"
Manufacture ID: 0156,0004
 
I was only able to test the first. Maybe there are more cards that should work. Note that HERMES I based cards are not supported, but here is an orrinoco driver for that one so that card should work out of the box.
 
The driver can be downloaded from [http://home.kpn.nl/pe1dnn/linux/](http://home.kpn.nl/pe1dnn/linux/)
 
A readme is included with background information and simple usage instructions. The Agere source is licensed under a BSD type license.
 
I hope it is useful for others but at least it works for me.
 
Kind regards,
 
Henk - PE1DNN.

Edit: the driver has been adapted, it now compiles clean with the 2.6.31 kernel; it also still compiles clean in Ubuntu 9.04.

---

### Post by pe1dnn on 2009-09-21
Bump: Linux kernel 2.6.31 is now supported.

---

