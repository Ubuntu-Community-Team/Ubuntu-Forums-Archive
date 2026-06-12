---
title: "D-Link DWA-140 on Ubuntu 9.10 (kernel 2.6.31-20)"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by toyman61 on 2010-03-28
I have installed Ubuntu 9.10 (kernel 2.6.31-20) 64-bits on my stationary PC. 
Earlier I have run XP SP3 with a D-Link DWA-140 USB Adapter at 300 Mbps connecting to my D-Link DIR-655 router.

When I tried to start up my DWA-140 on Ubuntu at first it didn't work. Blacklisting the rt2800usb-driver solved that problem.

But the adapter and the router is capable of giving me IEEE 802.11n-connection (300 Mbps) under XP, but in Ubuntu I only get 54 Mbps (equal to IEEE 802.11g). 

Do I have to wait for Ubuntu 10.4, or is there a simple way for me to achieve this on my installed platform?  If possible I do not want to recompile the driver...

---

### Post by toyman61 on 2010-03-30
Downloading the newest driver from RaLink, compiled, built and installed it.
Shut my computer down last night, and started it again today.

Now I'm happy: I have 270 Mbps speed reported in Network Manager.. :-)
(But I had to compile it... :-(( ).

---

### Post by Mattias on 2010-04-01
Toyman 
what driver did you download and do you have verB2 of the DWA-140 ?. I am getting really frustrated with this device, please help
/Mattias

---

### Post by jandante on 2010-05-07
I can't find it either.

I've tried the different howto's and compiled and "modbroped" my way through the manuals. but i can't get it to work

it doesn't even show up in nm or anything...

the tech guy in the store said it would work in ubuntu but no luck AGAIN

i"ve had the linksys wusb100 and another d-link until now and now the dwa-140 => nothing works apparently on ubuntu...

---

### Post by toyman61 on 2010-11-24
Updated to Ubuntu 10.04 (kernel 2.6.32-25) and suddenly the bit rate was back to 54 Mbps again. Recompiled and loaded the newest driver from Ralink, but still the same.. 
I have asked Ralink on mail about this, but I have so far got no answer.. :-(

---

