---
title: "Tips on getting a generic webcam to work"
date: 2008-10-17
forum: Multimedia Software
---

### Post by redpants on 2008-10-17
I have Ubuntu 8.04 installed and working great and decided to see if I could get my el-cheapo generic webcam to work on it.  I plugged it in to the usb port and nothing happened, and at that point I realized that I have no idea how to install a device in Linux if it doesn't automatically recognize...

So, I really don't even know where to start.  When I say generic, I mean REALLY generic (can't find any model numbers on it or anything), so I don't know if there is any sort of linux support at all for my device.  This is the kind I purchased:

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=180295950100](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=180295950100)

Could someone point me in the right direction on how to install this thing, assuming it is even possible?

Thanks!

---

### Post by kostkon on 2008-10-19
> **redpants said:**
> I have Ubuntu 8.04 installed and working great and decided to see if I could get my el-cheapo generic webcam to work on it.  I plugged it in to the usb port and nothing happened, and at that point I realized that I have no idea how to install a device in Linux if it doesn't automatically recognize...
Nothing is supposed to happen... 

First of all, have you tested it with *Cheese* (*Applications -> Graphics -> Cheese*)? This is the first application you should run to check if a webcam is recognised by the system and working.

If it working OK, then you can then test it with other applications that you want to use it with, e.g. *Flash*, *Skype*, etc.

---

### Post by redpants on 2008-10-23
Doesn't appear to recognize in Cheese.  I just get the color bars.

---

### Post by redpants on 2008-10-23
I cracked it open and this is what was on the chip:

CNLTF
LT-168G

A google search came up with plenty of Windows drivers, but I couldn't find any for linux.

Also, when I type lsusb it is listed as Microdia.

---

### Post by redpants on 2008-10-27
Any ideas?

---

### Post by misaelrod on 2009-02-19
> **redpants said:**
> I cracked it open and this is what was on the chip:

CNLTF
LT-168G

A google search came up with plenty of Windows drivers, but I couldn't find any for linux.

Also, when I type lsusb it is listed as Microdia.
redpants, I have the exact same cam and problem. Did you find any resolution? Thanks in advance.

---

### Post by Roving Sign on 2009-02-19
Does adjusting the User Priviliges make any difference...?

There is a checkbox that references webcams...

System > Adminsitration > Users and Groups

---

