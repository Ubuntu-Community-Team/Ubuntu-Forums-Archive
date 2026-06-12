---
title: "Deleted partition table by mistake"
date: 2019-10-03
forum: MINT
---

### Post by tutututu2 on 2019-10-03
Hi,

I erased by mistake my partition table (and, I suppose, only the table) and, when rebooting, (no surprise) the system did not boot at all (directly to the BIOS, saying no system found).

I tried many techniques, including running Gparted Live OS, TestDisk, and Boot-Repair-Disk, but none succeeded.

Here are some logs from boot-repair (made sequentially after each try):

[http://paste.ubuntu.com/p/dGY3Y9x82F/](http://paste.ubuntu.com/p/dGY3Y9x82F/)

[http://paste.ubuntu.com/p/Nx5w9T8VSg/](http://paste.ubuntu.com/p/Nx5w9T8VSg/)

[http://paste.ubuntu.com/p/rZ48rH43tS/](http://paste.ubuntu.com/p/rZ48rH43tS/)

In my last attempt, TestDisk manage to detect some thing, but most of the disk (in GParted) still appeared to be "unused space", i.e., absent from any partition.

When I rebooted, I was asked "Please unlock disk nvmeOn1p3_crypt", but inputting my usual password never succeeds.

I use Linux Mint XFCE (I forgot which version, perhaps 19) and I have encrypted partitions. That is, whenever I used to boot normally before the problem comes, I first had to enter a first password to unlock something, and then only my user password to open my session in Linux Mint.

Any idea what I can do?

---

### Post by oldfred on 2019-10-04
I do not really know LVM - logical volumes which you have if you do a full drive encrypted install.

But this is typical of the partitions with LVM. All the volumes are inside the third partition, only the ESP - efi system partition and /boot partition are not in LVM partition.
But your third partition is way too small, it should be all of the rest of the drive.

      ```
 Device           Start     End Sectors  Size Type
/dev/nvme0n1p1    2048 1050623 1048576  512M EFI System
/dev/nvme0n1p2 1050624 2050047  999424  488M Linux filesystem
/dev/nvme0n1p3 2050048 2054143    4096    2M Linux filesystem 


```

Not sure if expanding p3 to rest of drive will let you then run repairs on your LVM volumes or not.

If using Boot-Repair, be sure to both mount your LVM and decrypt it before running any Boot-Repair fixes.

Info on LVM:
       LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[URL="https://www.howtoforge.com/linux_lvm"]https://www.howtoforge.com/linux_lvm

      [/URL]
 Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu) 
   Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line) 
    [URL="https://www.howtoforge.com/linux_lvm"]
[/URL]

---

