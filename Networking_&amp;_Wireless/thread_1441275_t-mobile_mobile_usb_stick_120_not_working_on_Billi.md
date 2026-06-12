---
title: "t-mobile mobile usb stick 120 not working on Billion 7402GXL"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by cyy02 on 2010-03-28
Greetings, 
 
I have rencently bought a t-mobile dongle (USB stick 120) and wish to plug it in to my 3G router (Billion 7402GXL) which once worked well with 3 mobile broadband dongle, but now it always shows "3G Card not found"...
 
I have used the following information in setup:
 
Profile port:3G
Mode: Automatic
Tel No.: *99#
APN: general.t-mobile.uk
username: t-mobile
password: **[COLOR=red]tm ---------- not sure about it, only see ** on screen, I just guessed from internet sources that it could be tm.[/COLOR]**
[COLOR=black]PIN: blank[/COLOR]
 
Does anyone have an idea about this? I would really appreciate your help here!
 
Many thanks.

---

### Post by alexfish on 2010-03-28
which version of Ubuntu are you using

if this is a zte device then you need to eject the device if it appears on the desktop also should be ready to use if plugged in at boot time

have you tried it without the router first

also

my settings for tmobile UK are

Username  User
Password  mms

what does  dmesg  command show from the terminal when it is plugged into the router

regards

alexfish

---

### Post by 3xscreen on 2010-03-29
Hi CYY02, the parameters you have set are correct but I suspect Billion don't yet have support for the T-Mobile USB stick 120 dongle (which is a ZTE MF626).

I have a Billion BiPAC 7402NX rather than your model but had the same issue. I solved it by buying an unlocked Huawei E272 on eBay, putting the Sim card in that and copying your parameters.

I hope the above helps. 

regards, Scott

---

