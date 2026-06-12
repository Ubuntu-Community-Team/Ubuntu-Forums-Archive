---
title: "Getting a digital photo album to work"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by evil316 on 2007-12-22
My wife bought a cheap keychain sized digital photo album and I'm trying to get it to work with Ubuntu.  It connects via USB.  When I connect it Ubuntu doesn't recognize it (doesn't mount it).  It came with Windows software but I haven't tried to do anything with it in Wine as of yet.  Is there any easier solution to this?  Are there any specific mount points I may want to try first?  I would think it would just mount as a USB drive but maybe it has a different filesystem that Ubuntu is not recognizing?  Unfortunately there is no technical data that came with the unit.

Thanks!

---

### Post by Erky on 2007-12-25
I am also having the same problem. I installed the supplied Windows software through Wine, but when I try to start the program, I get this error: "Access violation at address 00652466. Write of address B82C7E34." My computer also will not mount it through the USB drive.

---

### Post by bindatype on 2007-12-25
Same problem here. I get the following results 
 ~ $ lsusb
 Bus 005 Device 003: ID 093a:020f Pixart Imaging, Inc. 
and 
 ~ $ dmesg|tail
 [ 1180.288000] usb 5-1: new full speed USB device using uhci_hcd and address 3
 [ 1180.516000] usb 5-1: configuration #1 chosen from 1 choice

so I know that ubuntu understands that a USB device was connected but it won't mount it. 
 $ sudo fdisk -l 

 Disk /dev/sda: 80.0 GB, 80026361856 bytes
 255 heads, 63 sectors/track, 9729 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1          10       80293+  de  Dell Utility
 /dev/sda2              11         272     2104515    b  W95 FAT32
 /dev/sda3             273         297      200812+  83  Linux
 /dev/sda4             298        9729    75762540    f  W95 Ext'd (LBA)
 /dev/sda5             298         618     2578401   82  Linux swap / Solaris
 /dev/sda6             619        5295    37567971   83  Linux
 /dev/sda7   *        5296        9541    34105963+  83  Linux
 /dev/sda8            9542        9729     1510078+  82  Linux swap / Solaris

As you can see, fdisk doesn't show the device. 

I'd mount it my hand but I can't associate the block device in the /dev directory. Should it be /dev/usb or something like that? I tried /dev/usb1 and /dev/usb2, etc but got no love. I figure that someone could do this with the output of lsusb but I don't know enough,

---

### Post by bindatype on 2007-12-25
PS, I didn't try wine yet. I thought that would be a last resort.

---

### Post by Timendus on 2008-07-08
Hello all,

We've been doing some research into this device, and trying to write a driver for it. It's still far from done (we can only check the available slots), but perhaps someone else can use our information or source to speed up development.

See here:
[http://timendus.student.utwente.nl/~fail/wiki/index.php/Photoviewer](http://timendus.student.utwente.nl/~fail/wiki/index.php/Photoviewer)

Cheers,
Tim
FAIL Systems

---

