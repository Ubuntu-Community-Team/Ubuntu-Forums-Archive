---
title: "DVI -&gt; USB DisplayLink detected as CD drive instead of displaylink"
date: 2011-10-12
forum: Multimedia Software
---

### Post by _glook on 2011-10-12
Hey all,

I'm currently running kubuntu natty on a MacBook Pro 6,2. I've already got two monitors and would like to attach a third one, but the issue is that the USB DisplayLink device that I have is detected as a CD Rom drive. When you plug it in for the first time on Mac and Windows machines, it thinks you've plugged in a CD Drive with a CD in it with a Windows setup file. If you are on Windows and you run the setup file, it will install all the DisplayLink drivers and asks you to restart. If you restart and subsequently unplug and then plug the device back in, it will no longer be detected as a cd drive but as a displaylink device and add a new monitor, as would be functional.

This is all well and good for Windows, but it is a pain when I'm trying to use udlfb on Linux. Does anyone know of any workarounds for Linux?

When I run "lsusb", I get:
```
Bus 001 Device 010: ID 17e9:02a7 Newnham Research
```like you would expect. But when I run "dmesg", I get:
```
[ 3132.270092] usb 1-1.4: new high speed USB device using ehci_hcd and address 10
[ 3132.385972] scsi4 : usb-storage 1-1.4:2.0
[ 3133.379224] scsi scan: INQUIRY result too short (5), using 36
[ 3133.379234] scsi 4:0:0:0: CD-ROM                                           PQ: 0 ANSI: 0
[ 3133.381622] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 3133.381845] sr 4:0:0:0: Attached scsi CD-ROM sr1
[ 3133.382251] sr 4:0:0:0: Attached scsi generic sg3 type 5
```

---

