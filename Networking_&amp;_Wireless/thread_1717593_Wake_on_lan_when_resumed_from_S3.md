---
title: "Wake on lan when resumed from S3"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by Debianforce on 2011-03-30
Hi there :)
Trying out the newest 10.10 "Maverick Meerkat". works like a charm and is lightning fast.

I'm going to let the machine run as my home fileserver together with Samba as the file sharing software. 

Hardware: AthlonII 3000mhz, 4GB ram. Asus mainboard. Integrated NIC and VGA / HDMI and so on..2 SATA disks. Completely new PC. 


Now I just have one problem, witch I'm also trying to **document** because there really are no good FAQ's for this. 

Namely:
Create your own linux home fileserver, and make it sleep when not in use so it don't disturb you with it's fan noise, together with WOL and acpi support from your bios and suspend in linux. One can even save some money on the powerbill :-D 
You just wake it up with Magic Packet software from other clients.

This works even without display, keyboard and mouse. Just a network cable and a power cord connected when configuration is done. 



The problem comes when waking up the machine from S3 sleep. With Magic Packet software(WOL). 

The machine wake's up, the disks are spinning up, fans are running, but nothing more. 
No network activity, no ping, no display, no nothing. Not even mouse or keyboard.
To get it up again, I need to turn it off, then back on with the power button on the chassis.

What actually happens when I wake it up with WOL from sleepmode? 
What does the network card drivers do in ubuntu? 
Is something disabled there, for WOL stuff? 
Could this be a bug related to the BIOS from Asus also?

---

