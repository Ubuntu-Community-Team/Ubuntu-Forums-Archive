---
title: "linux mint"
date: 2019-01-20
forum: MINT
---

### Post by roy robb on 2019-01-20
was wondering if anyone knew how to turn a usb drive back into a usable disk image? becuase i think i messed it up because everytime i try to use a boot loader everything goes threw but when i restart and try to go into the boot menu it doesnt show up in the menu only windows. any help would be helpfull

---

### Post by howefield on 2019-01-20
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2019-01-20
>                           was wondering if anyone knew how to turn a usb drive back into a usable disk image? 

From what?  What are you trying to use it as and what did you use it as?  What bootloader are you trying to use and where?  Is the bootloader on an internal hard drive?  Do you have a bootloader and some OS on the USB?  Did you install Ubuntu on an internal/external drive?   Which version/release of windows?   You're a bit short on details.

---

### Post by jeremy31 on 2019-01-20
What brand computer?  I know after putting Mint on a new HP, I had to go into BIOS, system config, boot options, OS boot manager and change the default from windows to ubuntu, save the settings and boot in order to be able to use Grub boot loader

---

### Post by oldfred on 2019-01-21
If you used dd or any of the tools that use dd under the hood to create installer, the flash drive is in a hybrid DVD/flash drive mode which is not with standard partitions.

       Reset USB flash that was dd'd to make it usable again
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266)
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by ajgreeny on 2019-01-21
I think the easiest way is to use [mkusb]("https://help.ubuntu.com/community/mkusb") to restore the USB to normal use.

See [https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) for the details

---

