---
title: "Canon Vixia HF R400 not auto-detected on 14.04"
date: 2014-04-27
forum: Multimedia Software
---

### Post by angelsguitar on 2014-04-27
Hi all.

I'm having some problems with a Canon Vixia HF R400 on Lubuntu 14.04.  I remember it used to automatically get detected on Lubuntu 12.04 (a window will pop up asking me what to do) and I could mount it and transfer my videos to the hard drive.  Now it doesn't show up when I plug it in.

lsusb shows this:
```
Bus 001 Device 007: ID 04a9:326a Canon, Inc
```

Here's the output of dmesg:
```
[ 1224.751956] usb 1-1.4: new high-speed USB device number 8 using ehci-pci
[ 1224.838699] usb 1-1.4: New USB device found, idVendor=04a9, idProduct=326a
[ 1224.838704] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1224.838708] usb 1-1.4: Product: Canon Video Camera
[ 1224.838710] usb 1-1.4: Manufacturer: CANON Inc.
[ 1224.838713] usb 1-1.4: SerialNumber: C200000000000000000000028E3B3B00
```

I tried installing mtpfs, mtp-tools but nothing.  I already have gvfs-backends and its dependencias installed.

Any help would be greatly appreciated.

---

### Post by angelsguitar on 2014-04-27
OK, I finally could transfer the videos using [gphoto2]("http://www.gphoto.org/doc/manual/using-gphoto2.html").  But still can't find a way to make it get detected as soon as I plug it to my computer.

---

