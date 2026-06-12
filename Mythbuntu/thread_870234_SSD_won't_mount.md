---
title: "SSD won't mount"
date: 2008-07-25
forum: Mythbuntu
---

### Post by kryptonite2k on 2008-07-25
I went through the mythbuntu install process from the livecd.
I setup the partitions as follows

8gb Sata SSD:
Entire drive as / with ext2

250gb HDD:
1gb swap
1gb /tmp with ext2
Rest of drive /var with xfs

The ssd will not mount on start up. I booted into the livecd environment and looked at /etc/fstab and the is what it says.

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hdc1 swap swap defaults 0 0

Is this correct for the above configuration? If not can someone help me correct this or provide other suggestions to help me get the ssd to mount?

---

### Post by ian dobson on 2008-07-26
Hi,

What do you get when you boot into the LiveCD and do a 

fdisk -l

This should list all drives/partitions seen by the system, even it they aren't mounted.

The fstab you displayed, it looks as if it's the fstab from the liveCD rather than the installed system.

If this is a fresh install, try just reinstalling with one one drive installed (The one you want to boot from). I had afew problems on my system getting the installer to use the right drive for / and in the end I just unplugged all the other drives and wheh the install was finished I maually added them.

Regards
Ian Dobson

---

