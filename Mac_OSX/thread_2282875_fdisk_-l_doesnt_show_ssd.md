---
title: "fdisk -l doesnt show ssd"
date: 2015-06-17
forum: Mac OSX
---

### Post by alexander46 on 2015-06-17
after changing graphic card driver and processor state (from max 2 to some quiet splash for PCSX2)
this macbook pro 1.1 ubuntu 14.04 32 bit crashed when i activated bleachbit.

now there is no bootable device.

testdisk doesnt show it, installation cant find space (also not Mac OS X) and memory test seems to check only some part of the disk.
2x 500mb + swap partition are shown with gparted. but it says cant create outside the disk.

need help!

is it possible to save data?

---

### Post by oldfred on 2015-06-17
Moved to the Apple sub-forum.

Fdisk is for MBR(msdos) partitions. Macs use gpt partitions, use gdisk or parted.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But testdisk should show partitions if you select the gpt option, not Intel/MBR/msdos.

---

### Post by alexander46 on 2015-06-17
now i cant even install testdisk anymore.
is it possible that memory check defragmented and destroyed the ssd?

fdisk lists 0 now

[http://paste.ubuntu.com/11740999/](http://paste.ubuntu.com/11740999/)

---

### Post by oldfred on 2015-06-17
I do not know details on SSD, but a few have had issues. But SSD life is now similar to hard drives. But hard drives also fail.

What brand/model SSD?

Does Smart Status show drive? You can use Disks and tiny icon in upper right to see Smart program.

---

### Post by alexander46 on 2015-06-17
Dont know the model.
`disks` and Smart program? dont get you :/

---

### Post by oldfred on 2015-06-17
From live installer, you should be able to load program Disks. 

Smart Status gives lots of detail on drive health, but all I know is passed is good and just about anything else is a new drive.

---

### Post by alexander46 on 2015-06-17
there is only one gigabyte loop device next to cd :(

---

### Post by oldfred on 2015-06-17
If UEFI/BIOS does not show device then no system can do anything with it.
Is it seen in UEFI as connected drive?
If not double check connections and cables.

---

### Post by alexander46 on 2015-06-18
its a vertex 4 solid state drive 2.5... you heard about ways to destroy it?  ill probably just try it again after plugging it back.

---

### Post by oldfred on 2015-06-18
There was this:
 [http://linux.slashdot.org/story/15/06/16/201217/trim-and-linux-tread-cautiously-and-keep-backups-handy](http://linux.slashdot.org/story/15/06/16/201217/trim-and-linux-tread-cautiously-and-keep-backups-handy)

---

