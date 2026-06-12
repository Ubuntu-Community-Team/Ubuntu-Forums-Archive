---
title: "usb-mounting is off and on"
date: 2010-03-10
forum: Multimedia Software
---

### Post by avguy on 2010-03-10
Hi all. I am really unlucky 'cause i'm experiencing a lot of problems with ubuntu. I'm using ubuntu 9.10 i386. When i plug in my usb drive into my computer, sometimes it'll will find it and mount it and open it up. Sometimes, it won't mount it and when i go into "places" where the storage devices on my computer are shown, it is not there. Someone Please Help!

---

### Post by wilee-nilee on 2010-03-10
What is the USB? Sansa that have a U3 driver show problems.

---

### Post by avguy on 2010-03-10
Super Talent

---

### Post by avguy on 2010-03-10
it's just a regular flash drive, not u3

---

### Post by garvinrick4 on 2010-03-10
Just so you can always mount a drive.
Give the drive a label.
Go to gparted and right click on drive or partition and label what
ever you want, lets say flash for this post.

To make a directory:
sudo mkdir /media/flash

To Mount:
sudo mount /dev/sdb1 /media/flash    (space after sdb1)

To unmount:
sudo umount /media/flash


To get your sdb1 or sda5 or whatever it is:
sudo fdisk -l    (that is a small L) every drive and partition on that drive is different sda1 or sda2 or sda3 and so on.

All drives or partitions will mount this way. After you have Labeled a drive or partition it will always be /media/flash from then on or whatever you name it. /media will always be in front of

---

### Post by garvinrick4 on 2010-03-10
Study your fstab to understand mounting. If your fstab is wrong your mounting of drives in Places will be in error at times. 
Google Ubuntu fstab and read up on. Always keep a copy of your fstab before you change. You will then have a copy to copy and paste with for UUID's and sda5 or sda7 and so on if and when you need. Study though so you understand what it is about, it is important for Linux users to understand.

---

