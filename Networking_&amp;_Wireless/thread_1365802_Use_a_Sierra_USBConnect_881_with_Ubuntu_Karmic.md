---
title: "Use a Sierra USBConnect 881 with Ubuntu Karmic?"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Breath! on 2009-12-27
I've been trying to use a USBConnect 881 in Ubuntu Karmic, but to no avail. Ubuntu recognizes that it's a Sierra broadband card, and I can set it up for AT&T Data Connect, but when I choose AT&T Data Connect 1, it tries to connect but then imideietly afterward it says GSM Network disconnected.

What's wrong?

---

### Post by thepurist on 2010-01-13
same here. karmic remix 9.10 w/ sierra usbconnect 881 has same problem here. NetworkManager recognizes the card but it disconnects right away during handshake. the driver segfaults, usb device is removed, and then reloaded.

268 Jan 13 00:23:33 system76-netbook kernel: [ 2933.738600] sierra 2-1:1.0: Sierra USB modem converter detected
   5269 Jan 13 00:23:33 system76-netbook kernel: [ 2933.739628] usb 2-1: Sierra USB modem converter now attached to ttyUSB0
   5270 Jan 13 00:23:33 system76-netbook kernel: [ 2933.739930] usb 2-1: Sierra USB modem converter now attached to ttyUSB1
   5271 Jan 13 00:23:33 system76-netbook kernel: [ 2933.740212] usb 2-1: Sierra USB modem converter now attached to ttyUSB2
   5272 Jan 13 00:24:03 system76-netbook kernel: [ 2963.520251] usb 2-1: USB disconnect, address 37
   5273 Jan 13 00:24:03 system76-netbook kernel: [ 2963.522269] sierra ttyUSB0: Sierra USB modem converter now disconnected 
   5274 Jan 13 00:24:03 system76-netbook kernel: [ 2963.522513] sierra ttyUSB1: Sierra USB modem converter now disconnected 
   5275 Jan 13 00:24:03 system76-netbook kernel: [ 2963.522881] sierra ttyUSB2: Sierra USB modem converter now disconnected 
   5276 Jan 13 00:24:03 system76-netbook kernel: [ 2963.522985] sierra 2-1:1.0: device disconnected
   5277 Jan 13 00:24:03 system76-netbook kernel: [ 2963.554743] modem-manager[3047]: segfault at 4554535d ip 009e3a9a sp bfd
   5278 Jan 13 00:24:08 system76-netbook kernel: [ 2968.868300] usb 2-1: new full speed USB device using uhci_hcd and addres
   5279 Jan 13 00:24:08 system76-netbook kernel: [ 2969.034516] usb 2-1: configuration #1 chosen from 1 choice
   5280 Jan 13 00:24:08 system76-netbook kernel: [ 2969.043347] usb-storage: probe of 2-1:1.0 failed with error -5
   5281 Jan 13 00:24:08 system76-netbook kernel: [ 2969.228116] usb 2-1: USB disconnect, address 38
   5282 Jan 13 00:24:10 system76-netbook kernel: [ 2970.708128] usb 2-1: new full speed USB device using uhci_hcd and addres
   5283 Jan 13 00:24:10 system76-netbook kernel: [ 2970.868620] usb 2-1: configuration #1 chosen from 1 choice
   5284 Jan 13 00:24:10 system76-netbook kernel: [ 2970.873465] sierra 2-1:1.0: Sierra USB modem converter detected
   5285 Jan 13 00:24:10 system76-netbook kernel: [ 2970.874677] usb 2-1: Sierra USB modem converter now attached to ttyUSB0
   5286 Jan 13 00:24:10 system76-netbook kernel: [ 2970.874951] usb 2-1: Sierra USB modem converter now attached to ttyUSB1
   5287 Jan 13 00:24:10 system76-netbook kernel: [ 2970.87523.......

---

