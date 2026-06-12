---
title: "Cannot create 128mb partition in Mac OS X Sierra"
date: 2017-01-17
forum: Mac OSX
---

### Post by trtsmb on 2017-01-17
I am following these instructions - [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf) - to create a dual boot on my Mac mini. In Part 2, the instruction call for creating two partitions. One partition is 128mb and will be the future boot loader. When I try to create it, it fails with the following error message - "An internal error has occurred. Operation failed." I have run first aid on the drive and it does not show any errors but every attempt to create the initial partition fails. Does anyone have any insight on the issue or how I can proceed?

---

### Post by oldfred on 2017-01-17
Moved to Apple sub-forum where those who know Mac may be able to help.

I have a few links, not sure if current, but I do not know Mac.
The default install for Ubuntu is just / (root) & swap. 
With UEFI systems you also need the ESP - efi system partition which is FAT32, you Mac may have that already and normally with PC you can only have one.
Drive does need to be gpt. If you installed Windows in BIOS mode you may have hybrid MBR/gpt which is not recommended.

       [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by trtsmb on 2017-01-17
Thanks. The only thing on the Mac is Sierra. My first attempt at doing dual boot ended up reformatting my hard drive. Thankfully, I had everything backed up and lost the current day's stuff. I'd rather not go through having to recover Sierra again.

> **oldfred said:**
> Moved to Apple sub-forum where those who know Mac may be able to help.

I have a few links, not sure if current, but I do not know Mac.
The default install for Ubuntu is just / (root) & swap. 
With UEFI systems you also need the ESP - efi system partition which is FAT32, you Mac may have that already and normally with PC you can only have one.
Drive does need to be gpt. If you installed Windows in BIOS mode you may have hybrid MBR/gpt which is not recommended.

       [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by oldfred on 2017-01-17
With a PC some install options erase entire hard drive, like the LVM full drive encryption.
Default install will install alongside Windows or another Linux, I would assume it would work the same with a Mac, but do not know.

But if you know & understand partitions, always better to partition in advance, and use Something Else install option to only use (choose) the ext4 partition as / (root) and swap. If swap created in advance the installer auto finds it.

---

