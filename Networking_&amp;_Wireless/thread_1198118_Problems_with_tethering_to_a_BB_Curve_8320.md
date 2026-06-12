---
title: "Problems with tethering to a BB Curve 8320"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by monkeythumpa on 2009-06-27
I am on Jaunty trying to connect to T-Mobile through my Blackberry. I am using Berry4All and it is getting on the network, I am getting an IP. My problem is that I can't access the Web or ping any servers while connected. I have disables mass storage on the phone and blacklisted berry_charge. BUT MY PHONE KEEPS CHARGING. OK, so I rename the berry_charge kernal and restart. Still no help on accessing the Web and my phone is still charging.

I have run "route" and everything is disabled, wired and wireless. Is that part of the problem? How does networking know to suck the data through the USB instead of the ethernet or wireless connection?

---

### Post by jlb.think on 2010-01-18
First make sure you are running berry4all as root, and if you are already please post your berry4all log here so we can look at it.

From inside your berry4all directory try:

sudo python bbtether.py tmobile -v

And then post the results here

---

