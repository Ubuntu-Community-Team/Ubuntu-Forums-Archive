---
title: "Multisystem does not create the proper partitions"
date: 2019-08-18
forum: MINT
---

### Post by kodokcowok on 2019-08-18
I used Mint 18.2 to create persistent multiboot with Multisystem on a 64GB USB with FAT32 format I first put W7 then Mint 19.2 when I boot the USB all I have is Mint 19.2 , no W7 and no root, swap or casper .It used 6Gb but when I tried to save data it says it is full while there is still 57 GB available. How can I fix and create the proper partitions.
The mkusb application does not create the problems I am having with Multisystem.
Help is much appreciated.

---

### Post by howefield on 2019-08-18
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2019-08-19
> create a Custom Multiboot UFD containing your favorite Bootable Live Linux Distributions.

The quote above is from the multiboot home page and tells you that it can be used to create a 'live' Linux system.  A 'live' Linux system is a read-only system so you should not expect it to be writeable.  Also, there is no indication that I saw that it will work with windows.  Windows is designed to not install to a usb so are you trying to put the windows 7 install iso on the usb?  That can be done but I don't know that multiboot will do it.  A 'live' Mint should not be much more than 2GB so I'm not sure where the 6GB comes from.

---

