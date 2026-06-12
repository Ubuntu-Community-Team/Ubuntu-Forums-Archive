---
title: "WLAN-Device not activated"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by Jayke on 2006-06-27
I recently booted my laptop using the Ubuntu Dapper Desktop CD in live-CD mode, and to my surprise nearly everything was working as I had hoped, even the native widescreen resolution managed to kick in. What seemed a bit more problematic however was the WLAN-Card. I was not expecting it to manage to connect to the network automaticly, since I use WPA-PSK, but I was a bit surprised to open Network Manager and find that the device was listed as not activated. I pressed the Activate button, but after I closed and re-opened the Manager GUI, it was still listed as not activated.

Since I couldn't find any settings for WPA-keys, I guess one reason the device is not left active is that it cannot find any networks to connect to, although this seems a bit odd. Since the device is listed in the Network Manager it seemed logical that it was found and correctly initialized. Still, my question is simply, why is the WLAN-card not activated? What can I do about it?

For the record, the wireless device does not appear under the "Network tools" application.

---

### Post by mozetti on 2006-06-27
We won't be able to help until you tell us what make/model the WLAN card is. If you know the chipset being used (broadcom 43<whatever>, atmel, prism, etc), then that's even better.  From there, people on the forums will be able to tell you if it's supposed to be supported natively or if you need ndiswrapper, and if anyone has experince (good or bad) with the card.

---

### Post by Jayke on 2006-06-27
Well, finding out which specific card this is could be a bit difficult, since the device is only listed as "ASUS Network Adapter" in the Windows device manager. Still, the following was listed as the driver:

BCMWL5.SYS, Broadcom Corporation, 3.1

I will try see if I can find out anything more specific.


EDIT: I found the following on linux-laptop.net:

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by mozetti on 2006-06-29
If you still need help, replay back here. Also search the forums, and the Wiki for "Broadcom drivers"

For example, I used [this thread](http://ubuntuforums.org/showthread.php?t=190967) to get my Broadcom card working.

---

