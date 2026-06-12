---
title: "Canon 450D and Ubuntu"
date: 2010-09-27
forum: Multimedia Software
---

### Post by big_bum on 2010-09-27
First of all I wanna say hi. 
I have a problem connecting my Canon 450d camera through USB in Ubuntu 10.04. The system does not recognize the camera as an Mass storage device and I cannot mount it.
The F-Spot sees the camera but (Canon 450D PTP mode) when i try to import the pics, F-Spot manager gives me the following error: "Error when connecting to camera. Unspecified error"

Can someone help me? Any ideas? If it's necessary I can change F-Spot manager with another pic importing software. (can someone give me a adivce in which software to use? )

I can say I am kinda noob in linux/Ubuntu so please be kind :)
I'm attaching some codes I raned but I'm kinda stuck. I don't know what to do next. 

```

dmesg returns:

[86954.500248] usb 2-2: new high speed USB device using ehci_hcd and **address 25**
[86954.670643] usb 2-2: configuration #1 chosen from 1 choice
[86965.050046] usb 2-2: reset high speed USB device using ehci_hcd and **address 25**

``````

**lsusb** returns:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 025: ID 04a9:3145 Canon, Inc. **
Bus 002 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


``````

**df -h** returns:

cristi@ubuntu:~$ df -h
Sis. fi&#537;iere            Dim    Uz Liber  Uz% Montat pe
/dev/loop0            5,6G  3,4G  1,9G  65% /
none                  1,9G  316K  1,9G   1% /dev
none                  1,9G  6,8M  1,9G   1% /dev/shm
none                  1,9G   88K  1,9G   1% /var/run
none                  1,9G     0  1,9G   0% /var/lock
none                  1,9G     0  1,9G   0% /lib/init/rw
/dev/sda3             172G  154G   18G  90% /host
/dev/sda2              30G   26G  3,5G  89% /media/Win7
/dev/sda5              98G   57G   42G  58% /media/imagini


```In /dev I cannot see anything new when I connect the camera, but any USB-stick, or device that can use Mass storage mode (I tried with a Mio GPS and a Nokia N73) appears in the /dev folder as a /sdb (or sdb+sdc in the case of the GPS, I think because the linux sees the internal memory of the device and also the MicroSD card from it)

Sorry for the long thread and sorry for any mistakes I made, but I tried to be as coherent as I could be since english is not my second language.
And sorry if I posted the thread in the wrong section.:oops:

Oh, I forgot:

```
cristi@ubuntu:/dev$ sudo fdisk -l
[sudo] password for cristi: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf5b87835

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3825    30616576    7  HPFS/NTFS
/dev/sda3            3825       26165   179448832    7  HPFS/NTFS
/dev/sda4           26165       38914   102401024    f  W95 Ext'd (LBA)
/dev/sda5           26165       38914   102400000    7  HPFS/NTFS

```

PS: If you wonder why do I have NTFS partitions, it's because I installed Ubuntu via Wubi from Windows.

---

### Post by big_bum on 2010-10-02
I've tryed digikam and it also doesn't works.
 Help?

---

