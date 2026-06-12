---
title: "Linux loader borked by Windows boot...Please help me recover my home directory...:("
date: 2020-05-31
forum: MINT
---

### Post by inomoxo on 2020-05-31
Hi all, 
I am posting here as the Linux Mint forum is no good and this is a common Linux/Ubuntu issue.

I have a Mac mini which has Windows 10 installed on a separate partition. I added an external USB3 SSD drive and installed Linux Mint on it. During installation I chose to encrypt the home directory only. There was some confusion as to where to place the boot loader but the install seemed to work.... I was able to boot into Linux by using the Mac's boot options on startup.

Linx Mint was running slowly. It worked though, until i booted into Windows :( 

After that I have been unable to boot back into Linux no matter what I try. I get a GRUB screen and when i type in "boot" (the only command I know) it tells me "You need  to load the kernel first"..

[SIZE=4]**To be clear: I don't need to run Linux again.. I just want to access my home directory so i can retrieve some files.**[/SIZE] I have an EXTFS driver on my Mac so I can read the contents of that drive but  of course the home directory is encrypted...
I tried running the USB stick that I used to install Linux Mint from but I couldn't repair the problem.

Please help!?

---

### Post by howefield on 2020-05-31
Moved to the "*MINT*" sub forum.

---

### Post by yancek on 2020-05-31
I'm not familiar with Macs but understand that you use (or can use) an Option key to select boot device from a menu, does that work?  Is this an EFI install, most Macs for a number of years have been doing EFI.

I don't really understad how simply 'booting' into windows on the computer can completely disable the boot options.  Are you able to boot the Mac OS?

I'm not sure what the  EXTFS drive on your Mac is capable of but if all you want to do is copy data FROM the unbootable Mint partition you should be able to mount it from the Mint usb, you should be able to mount the partition and copy any files FROM it to some other partition.  No root user permissions are required to copy FROM a partition.  I dont use encryption so I don't know what steps you would need to decrypt before copying.

---

