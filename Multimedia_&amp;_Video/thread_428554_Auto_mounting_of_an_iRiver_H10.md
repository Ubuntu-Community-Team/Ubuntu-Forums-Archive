---
title: "Auto mounting of an iRiver H10"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by z0phi3l on 2007-04-30
I need to get my H10 mounted, and usable in AmaroK

I already have EasyH10 installed but for the life of me can't get my system to recognize when I plug it into the USB port.

Suggestions?

---

### Post by z0phi3l on 2007-04-30
Bump :(

---

### Post by z0phi3l on 2007-04-30
last bump :(

---

### Post by dmizer on 2007-04-30
don't know ... but my h10 has been auto mounting with no problem since breezy.

try plugging in the iriver, and wait for about 2 or 3 minutes.  then post the output of the following:
```
dmesg | tail
```

---

### Post by z0phi3l on 2007-04-30
Here's what I got:

```
[   48.424517] Bluetooth: L2CAP ver 2.8
[   48.424523] Bluetooth: L2CAP socket layer initialized
[   48.428658] Bluetooth: RFCOMM socket layer initialized
[   48.428672] Bluetooth: RFCOMM TTY layer initialized
[   48.428675] Bluetooth: RFCOMM ver 1.8
[  241.632193] kjournald starting.  Commit interval 5 seconds
[  241.633002] EXT3 FS on sdb1, internal journal
[  241.633012] EXT3-fs: mounted filesystem with ordered data mode.
[  794.933133] usb 1-6: new high speed USB device using ehci_hcd and address 7
[  797.331582] usb 1-6: configuration #128 chosen from 1 choice

```

---

### Post by dmizer on 2007-05-01
humm ... everything looks fine.  you didn't kill your hal daemon by chance did you?  or in other words, do cd's or dvd's auto play?

tell me a bit more about your configuration ... what gui are you using?

hald and pmount should take care of this for you.  you might want to make sure the hald services are running.
```
ps -e | grep hald
```

---

### Post by z0phi3l on 2007-05-01
Using Gnome, Amarok is playing CDs, no major problems there.

```
 5109 ?        00:00:03 hald
 5110 ?        00:00:00 hald-runner
 5116 ?        00:00:00 hald-addon-acpi
 5130 ?        00:00:00 hald-addon-keyb
 5133 ?        00:00:00 hald-addon-keyb
 5136 ?        00:00:00 hald-addon-keyb
 5139 ?        00:00:00 hald-addon-keyb
 5144 ?        00:00:00 hald-addon-keyb
 5147 ?        00:00:00 hald-addon-keyb
 5165 ?        00:00:01 hald-addon-stor
 5167 ?        00:00:01 hald-addon-stor

```

---

### Post by dmizer on 2007-05-01
well, for the time being, i can tell you how to manually mount it.

create a folder in /media called H10:
```
sudo mkdir /media/H10
```
then mount it like so:
```
sudo mount /dev/sbd1 /media/H10
```

to unmount:
```
sudo umount /media/H10
```

---

