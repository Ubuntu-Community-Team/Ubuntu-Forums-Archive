---
title: "Kaiser Baas Tuner not recognised"
date: 2010-07-16
forum: Multimedia Software
---

### Post by nelo69 on 2010-07-16
Hey Guys and Girls

I have recently purchased a Kaiser Baas tuner card with a model number of KBA01010, it does not matter which package I use non of them can see the tuner card. I have tried kaffine and myTV, but ultimately I would like to get this device working with my mythtv installation.

I have followed alot of threads suggesting updated firmware etc but still no luck. By the output from the dmesg I am guessing the firware on the card is different from past cards.


When I connect it to my ubuntu 10.04 I get the following in the dmesg

[ 1701.608026] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 1701.745594] usb 1-4: configuration #1 chosen from 1 choice
[ 1701.766059] af9015: tuner id:177 not supported, please report!
[ 1701.771134] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[ 1701.771430] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:02.2/usb1/1-4/1-4:1.1/input/input6
[ 1701.771577] generic-usb 0003:15A4:9016.0003: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:02.2-4/input1

When I run lsusb i get
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone help me with this??

---

### Post by nelo69 on 2010-08-10
h

---

