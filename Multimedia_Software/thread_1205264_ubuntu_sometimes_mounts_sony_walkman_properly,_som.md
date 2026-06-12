---
title: "ubuntu sometimes mounts sony walkman properly, sometimes doesn't"
date: 2009-07-05
forum: Multimedia Software
---

### Post by pythonscript on 2009-07-05
I have a sony walkman nwz-s616f that's been giving me some problems. As of now, to sync songs to it, I boot into a virtualbox windows xp,  attach it with the virtual usb controller, and sync music with wmp 11. Tedious, I know, right? Especially if I want to add just one song... It doesn't mount under Ubuntu, is the problem. It shows up on the desktop, but only as a device; it doesn't have a mount point, and sudo fdisk -l doesn't show anything. Until! I've noticed that linux will mount it properly in /media/WALKMAN only after it's been mounted under the virtual xp and I shut down the virtual computer. As in, I use it in virtualbox, then shut down virtual windows, then it mounts. Otherwise, no. Any ideas? One of the times it mounted properly, I could see all the files, and here's the output from sudo fdisk -l after it mounted properly after a virtual xp session:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe728f646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        8001   83  Linux
/dev/sda2   *           2        1568    12586927+  83  Linux
/dev/sda4            1700       19457   142641135    5  Extended
/dev/sda5            1700       12153    83971723+  83  Linux
/dev/sda6           12154       18909    54267538+  83  Linux
/dev/sda7           18910       19457     4401778+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 3841 MB, 3841982464 bytes
1 heads, 62 sectors/track, 30257 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdb1: 3841 MB, 3841982464 bytes
1 heads, 62 sectors/track, 30257 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.


```The walkman is /dev/sdb1. Here's lsusb, too, if it helps at all:
```

Bus 002 Device 011: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 010: ID 054c:0327 Sony Corp. 
Bus 002 Device 004: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless 
                     (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Any idea how to make this thing work with Ubuntu? Jsymphonic won't work with it, even when it does mount properly, but I'm *really* hoping for a solution that doesn't involve booting into a virtual windows xp every 20 minutes or so.


EDIT: Hmmm, and in gparted (run from within ubuntu, not the live CD) it only shows up as a 1 GB (900 mb) device, but it's clearly a 3.5 GB device from the fdisk output, and from the specs on the device itself. Don't know if that means anything or not, but figured I'd add gparted's output as a curiousity.
```

Device /dev/sdb has a logical sector size of 2048.  Not all parts of
 GNU Parted support this at the moment, and the working 
code is HIGHLY EXPERIMENTAL.

Invalid partition table - recursive partition on /dev/sdb.

```

---

### Post by gustavp0387 on 2009-12-23
I had quite the same problem... I can see my mp3 device mounted on the desktop but jSymphonic never recognize it... 
Try this:
Open jSymphonic... on the jSymphonic menu select properties.. you will se a rectangle with some information and below it there are three buttons.. click on edit in de **Device Path** text box put **/media/disk**... what I did was to open the sony walkman device on the desktop and copy it address from the address line... hope it helps

---

### Post by lunadads on 2010-02-11
I have the same problem: I see my Walkman on the Desktop but can not find it anywhere in my filesystem. When I open the Walkman, it says the location is gphoto2://[usb:001,009]/,. I've tried editing the filepath under Jsymphonic to /media/disk/gphoto2://[usb:001,009], to no avail.

Any suggestions?

Thanks a lot.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by pythonscript on 2010-02-11
Since I dual boot Windows 7, I eventually decided to just sync media to the device from within Windows, since even under 9.10, the MTP support doesn't seem to be all that strong. I did successfully sync media to the device over a network share in virtualbox. I set up a Windows XP Pro virtual machine, installed the ext2/ext3 driver, then shared my home folder's Music directory as a network share to windows using the virtualbox Shared Folders option. It's slow, but it does work.

---

