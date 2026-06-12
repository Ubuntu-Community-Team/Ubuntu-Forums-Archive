---
title: "how do i mount my mp3 player"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by tater_3001 on 2007-06-27
it used to connect to amarok right away when i connected it but now it says "Devices handled by this plugin must be mounted first. Please mount the device and click "Connect" again." how do i mount it?

---

### Post by Jellyffs on 2007-06-27
Hi,

It should get mounted when you plug it in. Can you see the player in Nautilus?

---

### Post by tater_3001 on 2007-06-27
no its not on the desktop or in the places menu where it normally , however amarok detects it but cant connect.. it it says its on /dev/sdb1

---

### Post by Jellyffs on 2007-06-27
So if you try:

```
 mount /dev/sdb1
```

What do you get?

---

### Post by tater_3001 on 2007-06-27
ha i tried that first here is what it looks like:

    turner@turner-desktop:~$ mount /dev/sdb1
    mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by djchandler on 2007-06-27
If it's getting an Icon on the desktop, you should be able to click on it and bring up a nautilus window. I've never used amarok, but VLC will play my mp3 files with no problem. I know it is a not an application with lots of extra eye candy, but it's feature rich, and it will play anything I've tried, including HDTV transport streams recorded in BeyondTV in XP, DivX, MP3, WMV, WMA, MOV, etc. Are you maybe running into a DMR problem?

D. J.

---

### Post by Jellyffs on 2007-06-27
> **tater_3001 said:**
> ha i tried that first here is what it looks like:

    turner@turner-desktop:~$ mount /dev/sdb1
    mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

ok. If you plug it in and straight away you type:

```
dmesg
```

Can you see your player? What's the output?

---

### Post by tater_3001 on 2007-06-27
but the icon that is usually there is not... nor is it in the places menu... my sansa (mp3 player) is says connected on the screen and it shows up in amarok , but wont let me connect until i mount it ... but idk how to mount it..

---

### Post by tater_3001 on 2007-06-27
ok a big list comes up and it sees it..  but it still wont connect

---

### Post by tater_3001 on 2007-06-27
ok pretty much i just messed up my whole thing... ha fyi dont mount stuff on the desktop... ha big mess..im gunna back  up and do a clean install thanks for the help anywasy though

---

### Post by tater_3001 on 2007-06-27
ha do  you by chance know how to manually unmount something?

---

### Post by Jellyffs on 2007-06-27
```
umount /dev/whatever
```

might need sudo for some..

---

### Post by zero244 on 2007-10-19
Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your password.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scsi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

---

### Post by dtvarnum on 2007-12-04
This is what my dmesg displays. It doesn show my Insignia MP3 player:
usb-storage: waiting for device to settle before scanning
  Vendor: Insignia  Model: Pilot Player      Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 15859712 512-byte hdwr sectors (8120 MB)
sdb: Write Protect is off
sdb: Mode Sense: 37 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 15859712 512-byte hdwr sectors (8120 MB)
sdb: Write Protect is off
sdb: Mode Sense: 37 00 00 08
sdb: assuming drive cache: write through
 sdb:
sd 2:0:0:0: Attached scsi removable disk sdb
  Vendor: Insignia  Model: Pilot Player      Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdc: 993984 512-byte hdwr sectors (509 MB)
sdc: Write Protect is off
sdc: Mode Sense: 37 00 00 08
sdc: assuming drive cache: write through
SCSI device sdc: 993984 512-byte hdwr sectors (509 MB)
sdc: Write Protect is off
sdc: Mode Sense: 37 00 00 08
sdc: assuming drive cache: write through
 sdc: sdc1


I don't know how to mount. Any ideas?

---

### Post by pebo on 2007-12-04
[https://help.ubuntu.com/communityhttps://help.ubuntu.com/community/Mount?highlight=%28mount%29/Mount?highlight=%28mount%29]("https://help.ubuntu.com/communityhttps://help.ubuntu.com/community/Mount?highlight=%28mount%29/Mount?highlight=%28mount%29")

---

