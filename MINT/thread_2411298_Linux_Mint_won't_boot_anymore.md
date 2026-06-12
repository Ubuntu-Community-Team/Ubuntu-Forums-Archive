---
title: "Linux Mint won't boot anymore"
date: 2019-01-28
forum: MINT
---

### Post by lehphyro on 2019-01-28
Hi, I'm a software developer and have been using Linux for years now but I've got an issue that I can't figure out. My machine won't boot anymore and I don't really know why.
I tried to use boot-repair (here is its report: [http://paste.ubuntu.com/p/zVsVRtjRXV](http://paste.ubuntu.com/p/zVsVRtjRXV)) but it didn't work.
I'm using encrypted drives and I'm not sure if there is a hardware failure. The last time I rebooted it, it hung with a message saying that the filesystem was in read-only mode, I don't know the exact message.

Can someone shed some light on this? Thank you!

---

### Post by lehphyro on 2019-01-28
This is the output of fdisk -l:

> $ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1890041856 bytes, 3691488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3917FE9B-C6FF-489D-A5DA-E0EA5D344D39

Device         Start       End   Sectors   Size Type
/dev/nvme0n1p1  2048 488396579 488394532 232.9G unknown


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2EDFE33A-F894-4AAF-B0BC-C795D96CE91A

Device     Start        End    Sectors   Size Type
/dev/sda2   2048 1953523711 1953521664 931.5G unknown


Disk /dev/sdb: 59 GiB, 63333990400 bytes, 123699200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x09bebfcf

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3855295 3855296  1.9G  0 Empty
/dev/sdb2       3843044 3847715    4672  2.3M ef EFI (FAT-12/16/32)

I believe it's missing /dev/nvme1n1 since I've got two 256GB SSDs and a 1TB spinning drive in this laptop, so it may indeed be a hardware failure, how can I prove that?

---

### Post by lehphyro on 2019-01-28
Somehow it solved itself. I rebooted, turned it off and on again and it booted normally.

---

