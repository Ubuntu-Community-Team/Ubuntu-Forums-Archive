---
title: "USB Audio (Not connected)"
date: 2008-07-03
forum: Multimedia Software
---

### Post by putrid on 2008-07-03
Hello. 
I purchased a [_USB Sound Adapter_]("http://www.dealextreme.com/details.dx/sku.5831"), since my original soundcard is defect.
i plugged it in, change the options on *System - Preferences - Sounds* to **USB Audio** and it worked well.
however; after a few hours, I rebooted the computer. And since then, it wont "connect". The (red) lights turns on when i plug it in, but still: *USB Audio (Not connected)*. I cant remember if there was a green light on it when it worked. I'm pretty sure the red light was on while it was working. [SIZE="1"](I *suppose* it the red one = Power, and the green = "connected")[/SIZE]

I found it by using the *lsusb* command..:
```
 $ lsusb
Bus 004 Device 005: ID 2001:3a03 D-Link Corp. [hex] 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 018: ID 046d:c30f Logitech, Inc. 
[COLOR="Red"]Bus 002 Device 017: ID 1130:f211 Tenx Technology, Inc.[/COLOR] 
Bus 002 Device 006: ID 03eb:0902 Atmel Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000
```  

Ive tried several reboots. Tried plugging it in before, and after logging in. Tried several USB ports

I'm running Ubuntu-Hardy
Been searching a while now, but i cant seem to find anyone who has brought up this problem before.. strange.. :S

Anyone got a clue what I should try next?
[SIZE="1"](I know, i know.. my English is bad enough)[/SIZE]

[IMG]http://www.dealextreme.com/productimages/sku_5831_4.jpg[/IMG]

---

### Post by kaligus on 2008-07-24
I would appreciate some help here too.

This device has proven difficult on a single sound device system and impossible on multiple device systems.

I did have it working on this box (SB live (pci), nvidia ck804 (onboard), tenx usb-audio) in two versions of windows and 2 live-cd's but NEVER with pulse audio anywhere near the system.

My single card system has no issues with the tenx under windows, but is playback only under gutsy.

---

