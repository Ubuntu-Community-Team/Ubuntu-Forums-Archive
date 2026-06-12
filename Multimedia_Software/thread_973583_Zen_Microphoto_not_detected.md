---
title: "Zen Microphoto not detected"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Scott-271 on 2008-11-06
Howdy all,

I'm having an issue (which I understand is common) with a Creative Zen Microphoto MP3 player. I have no access to WinXP, so Linux is my only option.

I'm running a fresh install of 8.10, fully updated. It is not being detected by almost anything, although the Zen screen says "Docked" when I run *mtp-detect*.

Anyhoo.....on to the nitty-gritty:
```

other@FunkaLinux:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN MicroPhoto (041e:413c) @ bus 0, dev 6
Attempting to connect device(s)
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 8194)
  Try to reset the device.
Unable to open raw device 0
OK.
other@FunkaLinux:~$ sudo mtp-detect
[sudo] password for other: 
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN MicroPhoto (041e:413c) @ bus 0, dev 6
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 8194)
  Try to reset the device.
Unable to open raw device 0
OK.
other@FunkaLinux:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 041e:413c Creative Technology, Ltd Zen MicroPhoto
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
other@FunkaLinux:~$ sudo mount /dev/bus/usb/006 /mnt
mount: special device /dev/bus/usb/006 does not exist
other@FunkaLinux:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000024d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         510     4096543+   7  HPFS/NTFS
/dev/sda2             511         959     3606592+   5  Extended
/dev/sda3             960        1533     4610655   83  Linux
/dev/sda4            1534        2016     3879697+  83  Linux
/dev/sda5             511         575      522081   82  Linux swap / Solaris
/dev/sda6             576         959     3084448+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb82c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
/dev/sdb2   *        4866        4866           0    e  W95 FAT16 (LBA)
other@FunkaLinux:~$ sudo gnomad2
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 8194)
  Try to reset the device.
PDE device NULL.
other@FunkaLinux:~$ mtp-folders
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 8194)
  Try to reset the device.
mtp-folders: There has been an error connecting. Exit
other@FunkaLinux:~$ 

```

I have GNomad2 and Amarok installed, neither detect it. I have read a ton of the info out there, but still no joy. So, any/all help will be appreciated.

Thanks,
Scott

---

