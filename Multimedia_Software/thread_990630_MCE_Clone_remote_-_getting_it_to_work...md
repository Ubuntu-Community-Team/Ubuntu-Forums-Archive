---
title: "MCE Clone remote - getting it to work.."
date: 2008-11-22
forum: Multimedia Software
---

### Post by hornetster on 2008-11-22
Hi, am trying to get a clone MCE USB Remote working with MythTv. Don't know a lot about it (mythtv, or remotes...) but am trying.... 
Have installed lirc, and the remote DOES sort of work ie pressing up and down and a few other keys gets a reaction even at the command line (previous commands, etc). BUT, there is no /dev/lirc0 which I am assuming there should be, and if I run irrecord I get:
[I]root@boss:/etc/lirc# irrecord myrecord

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)[/I]

And these modules are running by default:

[I]root@boss:/etc/lirc# lsmod |grep lirc
lirc_mceusb            16736  0 
lirc_dev               19892  1 lirc_mceusb
usbcore               148848  11 lirc_mceusb,dldrusb,gspca_spca561,zd1211rw,gspca_main,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd[/I]

Am running MythBuntu Control Centre, but unsure what I should be selecting in relation to the remotes...
ie should I select Windows Media Centre remotes or something else....
The remote comes up in dmesg as:

[I][ 9355.079366] input: HOLTEK     PC receiver  as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input8
[ 9355.112814] input,hidraw2: USB HID v1.10 Keyboard [HOLTEK     PC receiver ] on usb-0000:00:1a.0-2
[ 9355.151730] input: HOLTEK     PC receiver  as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.1/input/input9
[ 9355.221687] input,hiddev96,hidraw3: USB HID v1.10 Mouse [HOLTEK     PC receiver ] on usb-0000:00:1a.0-2
[10850.263491] usbcore: registered new interface driver lirc_mceusb
[10850.264567] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2[/I]

Any help appreciated....
John.

---

### Post by fenian on 2008-11-23
In Mythbuntu Control center>Infrared Devices
Check Enable Remote Control
Choose Windows Media Center Remotes (New Version Phillips et. al)
Some of the specialty buttons may not do anything in Myth but the basic ones (Play,Pause,Up,Down,Forward,Back,volume,mute,etc...,should work)

---

