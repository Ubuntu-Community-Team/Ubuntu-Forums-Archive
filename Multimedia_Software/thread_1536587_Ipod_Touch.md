---
title: "Ipod Touch"
date: 2010-07-22
forum: Multimedia Software
---

### Post by changlinn on 2010-07-22
Wife bought an iPod touch due to wanting to needing a big screen for listening to lectures and some of the Apps available being good for her studies and recommended for our kids.
Trying to get it to work on either of out eepc's running completely up to date 10.04 though and it won't work in Rhythmbox or gtkpod. It does however show up on the desktop as ipod, and it shows up in Rhythmbox, however id your right click it in rb and select properties rb crashes, and you can paste music to it from the library. There currently isn't any music on it, and I have activated it via itunes from a windows pc. It is running firmware 3.1.2 iPod 3.1.2, it had B528 in one of the apple files on the device (device id iirc)

I tried running through this guide ([http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html) ) on my ubuntu pc same specs as hers, but that seemed to break it further, it no longer worked in Rhythmbox and gtkpod although has the device can't do anything with it
Anyone got any ideas on how to get this thing to work?

Below are some outputs
mount-a
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
snip..
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fiona/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fiona)

dmesg|tail
[134749.006525] hub 1-0:1.0: over-current change on port 1
[134749.108090] hub 1-0:1.0: over-current change on port 2
[134749.212102] hub 1-0:1.0: over-current change on port 3
[134749.557096] usb 1-3: new high speed USB device using ehci_hcd and address 9
[135008.326377] rhythmbox[19124]: segfault at 0 ip b2c7d8f6 sp bf9c3e40 error 4 in libipod.so[b2c78000+10000]
[136025.958992] usb 1-3: USB disconnect, address 9
[136633.636110] usb 1-3: new high speed USB device using ehci_hcd and address 10
[136663.933275] usb 1-3: USB disconnect, address 10
[136675.564096] usb 1-3: new high speed USB device using ehci_hcd and address 11


lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 05ac:1293 Apple, Inc.
Bus 001 Device 002: ID 13d3:5125 IMC Networks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by changlinn on 2010-07-23
I think part of the problem was with the ipod, I deleted iTunesDB of the device and it ran through a setup on my ubuntu pc, but rhythmbox was still no go, removed that file again and tried windows with itunes and it worked.
Would still prefer to get this working in Ubuntu though.

---

