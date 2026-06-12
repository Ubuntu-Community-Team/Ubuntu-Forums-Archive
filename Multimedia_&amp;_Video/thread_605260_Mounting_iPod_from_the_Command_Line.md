---
title: "Mounting iPod from the Command Line"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by mthmchris on 2007-11-06
Alright, so for whatever reason my iPod's been a pain, and I want to mount it from the command line.

Just for the record, my iPod has very low battery right now.  I don't know if that's important or not.

So I want to do the sudo mount /dev/sdb2 /media/ipod/ command, but it says that sdb2 doesn't exists.  So I try dmseg to try to find the name of the ipod, but all I get is this:

chris@Toshiba:~$ sudo dmesg | tail
[   58.100000] usb 1-1: configuration #1 chosen from 1 choice
[   58.116000] input: USB-compliant keyboard as /class/input/input9
[   58.120000] input: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.0-1
[   58.144000] input: USB-compliant keyboard as /class/input/input10
[   58.144000] input,hiddev96: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.0-1
[  375.724000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[  375.900000] usb 2-2: configuration #1 chosen from 1 choice
[  375.916000] input: Logitech Optical USB Mouse as /class/input/input11
[  375.916000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-2
[  578.584000] usb 2-2: USB disconnect, address 2

Now, the weird thing for me is that my iPod is plugged in but my mouse is not.  Also, in gparted it doesn't recognize that my iPod is plugged in.  Any ideas?

---

### Post by Qinjuehang on 2007-11-06
If I'm not wrong, Ipod's have some security thing that only enables it on one computer. Maybe it doesn't recognise Ubuntu as your old computer?

---

### Post by mthmchris on 2007-11-06
I've used it on this computer before, on Ubuntu, on many occasions.  Hmm...

---

### Post by mthmchris on 2007-11-06
wtf

I do this again:

chris@Toshiba:~$ sudo dmesg | tail
[   29.760000] Bluetooth: RFCOMM TTY layer initialized
[   29.760000] Bluetooth: RFCOMM ver 1.8
[   33.900000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   33.900000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   33.900000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   34.516000] NET: Registered protocol family 17
[   36.272000] NET: Registered protocol family 10
[   36.272000] lo: Disabled Privacy Extensions
[   36.272000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   47.204000] eth0: no IPv6 routers present

Is there no way to get the name of the device?

---

