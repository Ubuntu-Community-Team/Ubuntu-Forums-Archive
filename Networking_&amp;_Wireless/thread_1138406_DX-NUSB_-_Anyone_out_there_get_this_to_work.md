---
title: "DX-NUSB - Anyone out there get this to work?"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by geoffmcc on 2009-04-26
Hello.

Anyone out there using DX-NUSB (Dynex) 

Please help, I searched forums by model # as well as google for model # and ubuntu (and model # & linux) with no help

Thank You

Edit : 

Sorry I am using the latest version of ubuntu 9.04

---

### Post by geoffmcc on 2009-04-26
UPDATE:

Ok. I found my cd and found that the drivers are bcm43xx64 (as i use 64 edition)

Now searching around to find out if i can use the b43 drivers for this device


EDIT: 

Anyone have any tips for me. 
To be more clear this is what i have done so far

I installed Ndiswrapper and Ndiswrapper-tools (or whatever it was)
I copied the files bcmwlhigh5.inf and bcmwlhigh5.sys 

ran ndiswrapper -i bcmwlhigh5.inf and it runs
from this point still no light on usb device. i try modprobe bcmwlhigh5 but fails

so i run ndiswrapper (forget whatever option shows installed drivers) and i get

bcmwlhigh5 : driver installed
	device (050D:D321) present

if i unplug the usb device i get

bcmwlhigh5 : driver installed



so i feel im getting close, just trying to figure out what to do next

---

