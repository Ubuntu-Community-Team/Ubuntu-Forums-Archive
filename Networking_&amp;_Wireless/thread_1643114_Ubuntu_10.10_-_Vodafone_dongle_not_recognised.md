---
title: "Ubuntu 10.10 - Vodafone dongle not recognised?"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by glitterbump on 2010-12-11
Hi all, I'm new to this so please forgive me if I'm in the wrong place!
We recently got a new mini PC which came pre-installed with Ubuntu 10.10, so far, so good.
Today, we invested in a Vodafone broadband dongle (model number: K3570-Z/K3571-Z). I've installed the dongle on our old XP machine, with no problems, however, Ubuntu won't even recognise that it's plugged in. 
What am I doing wrong? We've had the new machine for 3 days, so I'm really new to all of it and haven't learnt how to use the command prompt yet, so I'm hoping someone has some advice for a complete beginner.
I can't understand why it's not recognising that somethings plugged in, because from what I've found, you need usb_modeswitch in over for the dongle to be recognised as a modem.
I'm very confused and really need some help please!!
Many thanks

---

### Post by yellerKat on 2010-12-11
Hi, here's a [LINK]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu") to Vodafone's Betavine open source development site. Hope it helps.

---

### Post by glitterbump on 2010-12-11
Hi yellerKat, I've installed the Betavine download (Ubuntu.tgz) etc, and still not recognized.

---

### Post by glitterbump on 2010-12-11
Ok, I'm not sure if this helps at all, but I've found out something under the command 'lsusb'.
I *think* the Vodafone device is known as **ID 19d2:1008 ONDA Communication S.p.A.  **not sure if this will help anyone. I'm just trying to work out how to update the driver (if that's my problem)

---

### Post by yellerKat on 2010-12-11
Just dug out old Vodafone dongle! If you left-click on the network connections in the notification area do you see: "New Mobile Broadband (GSM) connection..."?

---

### Post by glitterbump on 2010-12-11
yellerKat - No!
I have found out that the device is recognised under a device manager thingy I downloaded, but still can't get it to work.
I've installed the Betavine software, and when I load that up it says "select a device" then two options,
1: "known devices" (no devices found)
2: "custom device settings" - no idea what the custom settings would be.
Interestingly, (well!) in the device manager, under USB EHCI CONTROLLER, there are 5 USB Vodafone interfaces, not entirely sure why but I'm wondering if this is part of the problem.

---

### Post by Jack44 on 2011-01-21
Hi Glitterbump,

I had exactly the same problem with the same modem on 9.1 10.04. I found that this:

[www.sakis3g.org](www.sakis3g.org)

got it working without too much trouble. 
I had exactly the same problem with the Betavine software too,

Hope this helps (a month later)

---

