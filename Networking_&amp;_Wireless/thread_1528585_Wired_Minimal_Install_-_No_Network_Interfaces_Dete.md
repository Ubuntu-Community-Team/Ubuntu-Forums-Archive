---
title: "Wired Minimal Install - No Network Interfaces Detected"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by BLaZuRE on 2010-07-10
I'm trying to do a minimal install via a USB flash drive.  Everything was good until it tried to recognize my network (wired)>  It showed "No Network Interfaces Detected".

I wish to do a minimal install since I want to install the programs I want myself.  Plus, I have a small flash drive.

I'm using an Atheros AR8151 PCI-E as my card (as shown by Windows).  I also have a wireless, though I don't care much about that, wired will probably be easier.

Through the command shell, I can see Ethernet Controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0).

So ... it's being recognized but not detected?

When I do plug the Ethernet cable in, I don't get the lights on during Linux installation but they do come on in Windows.

Any ideas?  If I need some additional driver, can I somehow add it to the minimal installation?

It lists my wireless Card as a Network controller, if that makes any difference.

---

### Post by BLaZuRE on 2010-07-11
So, I was looking through the log file and found that i82365 could not be loaded, a PCMCIA controller.  I'm **assuming** this is separate from the NIC and interfaces between the bus and the NIC.

Anyway, no idea whether it's because it couldn't find the drivers or because the controller was incorrectly identified.  But I'm pretty sure this is why I can't get my network card to work.


More help is appreciated and needed.

---

### Post by BLaZuRE on 2010-07-11
Would this do better under the Installation & Upgrades forum?

---

### Post by BLaZuRE on 2010-07-14
Anyone?

---

### Post by Joe Awsome on 2010-07-14
I have the same thing or something reasonably close going on. I've been trying to do a minimal install on an old laptop but for some reason I can't connect to my network using DHCP or something. I keep trying the autoconfig option but it never picks up. I have to use a PCMCIA ethernet adapter to connect. Is ubuntu not detecting this thing right and expecting me to use the onboard phonejack (fat chance, we ditched our land-line ages ago)? Wut is the issue with the minimal install?

---

### Post by BLaZuRE on 2010-07-17
bump

---

### Post by BLaZuRE on 2010-10-08
My solution:
When at GRUB load menu, press 'e' for edit
Delete 'quiet and splash'
Replace with 'nomodeset'

Works *yay* ... and it only took 3 months to casually stumble on an article that said that.

---

