---
title: "Using modem in Huawei CDMA phone"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by zammi on 2006-06-10
Sorry I couln't mension that this is a Dial-Up modem issue. 

And another thing I noticed is, the ti_usb_3410_5052 driver coming with the kernel is 0.9 but the latest is 2.6-1.1. I tried to compile it but couldn't as the usb-serial.h is missing in the kernel source. :-( ..

One last thing , I'm going to go back to Breezy and try ....

-----

I'm using the modem comes in Huawei wireless terminal CDMA phone in windows. It uses the drivers from "Texas Instruments".

In Linux (Ubuntu) this suppose to use "ti_usb_3410_5052" driver. 
I'm getting following error in system messages, when I try to use this in Linux.

Please help me to set up this modem:

Error Msg:

[4297143.901000] usb 1-2: new full speed USB device using uhci_hcd and address 6
[4297144.048000] ti_usb_3410_5052 1-2:1.0: TI USB 3410 1 port adapter converter detected
[4297144.676000] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[4297144.800000] usb 1-2: device firmware changed
[4297144.800000] ti_usb_3410_5052: probe of 1-2:1.0 failed with error -5
[4297144.800000] usb 1-2: USB disconnect, address 6
[4297144.902000] usb 1-2: new full speed USB device using uhci_hcd and address 7
[4297145.071000] usb 1-2: configuration #1 chosen from 2 choices
[4297145.073000] ti_usb_3410_5052 1-2:1.0: TI USB 3410 1 port adapter converter detected
[4297145.073000] ti_usb_3410_5052: probe of 1-2:1.0 failed with error -5

Thanks in Advance,
Zammi

---

### Post by zammi on 2006-06-11
Could anyone help me on this...

BTW: I got a link that I should try before try Badger
[http://enterprise.linux.com/article.pl?sid=06/03/08/2138237&tid=20&tid=100](http://enterprise.linux.com/article.pl?sid=06/03/08/2138237&tid=20&tid=100)

---

### Post by zammi on 2006-06-11
I think I myself found the solution. This is related to "usbserial" driver issue.
1. I inserted the usb cable and let system to load ti_usb_3410_5052...and found the ProductId(Say: 9999) and VendorId (Say 111). Them removed the usb cable.
2. Probe the usb serial this way: modprobe usbserial vendor=0x111 product=0x9999
3. Inserted the usb cable...
4. This time it didn't fire any error... when probing ti_usb_3410_5052, and created /dev/ttyUSB0 instead.

This part is over. But still my problem is not over. Now this has become a usual dial-up issue as others having...Cannot connect to internet yet...

Can anybody tell me how to automate the 2nd step above (Let system to automatically probe usbserial with correct VendorId/ProductId), when I inserted the modem cable.

---

