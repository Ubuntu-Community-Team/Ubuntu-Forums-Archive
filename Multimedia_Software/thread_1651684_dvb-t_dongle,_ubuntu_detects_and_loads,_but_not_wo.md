---
title: "dvb-t dongle, ubuntu detects and loads, but not working"
date: 2010-12-23
forum: Multimedia Software
---

### Post by skreamz on 2010-12-23
hi all,

I hope someone can help :p

I acquired a dvb-t turner and have been trying to get mythtv, me-tv or even kaffine to use it, but no of them seem to be able to detect it. when i plugged it in, i ran System->Administration->Additional Drivers, which install firmware from my card. which seems to load up fine, but the programs cant seem to see it.

I'm using ubuntu 10.10 64bit.

info from lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:0015 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 046d:c229 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c228 Logitech, Inc. 
Bus 001 Device 003: ID 05e3:0607 Genesys Logic, Inc. 
Bus 001 Device 002: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and info from dmesg | grep -i dvb

[    2.478803] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[    2.479035] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.1/input/input2
[    2.479082] generic-usb 0003:15A4:9016.0001: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:12.2-4/input1
[   17.383235] WARNING: You're using an experimental version of the DVB stack. As the driver
[   17.870578] usbcore: registered new interface driver dvb_usb_af9015


any help, would be grateful.

---

### Post by skreamz on 2010-12-24
first and last bump till after xmas :p

merry xmas all

---

