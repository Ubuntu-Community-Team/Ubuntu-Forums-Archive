---
title: "Grub issues - can't boot system"
date: 2022-10-27
forum: MINT
---

### Post by bizres on 2022-10-27
So I was perfectly using my Linux Mint 20.3 system and normally shut down my system, only to boot up the following day to see a grub error:[ATTACH=CONFIG]291195[/ATTACH]
I tried to recover the situation using GRUB Rescue, but it kept giving some UEFI error. Noting that my PC does not seem to use UEFI (HP Compaq Pro 6300 Small Form Factor PC with 3.2GHz Dual Core processor), so I connected my HDD via USB to my laptop which supports UEFI.
Booted the laptop via Linux Mint 21 live USB and performed the "Recommended repair" of GRUB Rescue.
All seemed to go well and got a success message.
Then I connected my HDD back into it's PC and booted, but just see a blinking cursor on a black screen. PC looks to be frozen.
Connected the HDD by USB to the laptop which supports UEFI, but get the message there is none system disk or disk error/no bootable device.

Is there any way I can recover my system?

If it's not possible, I do have a Timeshift backup of the Linux Mint installation.
1. Is it possible to recover/repair the GRUB/boot problem from the timeshift backup?
2. Alternatively, if I do a fresh install of Linux Mint 20.3 on the HDD, how would I go about recovering my system from timeshift? (btw, my Linux Mint installation was done using passphrase as well as encrypted home folder)

Would really appreciate some help on this, pls.

---

### Post by QIII on 2022-10-27
Moved to MINT as the appropriate sub-forum.

---

### Post by yancek on 2022-10-28
If no changes were made prior to the original error, there are any number of possible problems.  You can boot your live Mint and run the following command while booting on the  HP Compaq Pro 6300 to determine if it is UEFI capable.  You could also simply the live Mint and run fdisk to see if you have an EFI partition on the failed boot drive.

> /sys/firmware/efi  

If the message indicates the folder doesn't exist, you are using Legacy/MBR.  If the computer isn't EFI capable, doing an EFI repair won't help.  If you are no longer able to boot the laptop, you installed the efi file on it pointing to the failing HD.  I would suggest the next step be to boot the live Mint and download and run boot repair from the link below.  Use the 2nd option explained on that page and when you run boot repair, select the Create BootInfo Summary option and do NOT try to make any repairs.  You will get a link to post here when it finishes which will show necessary details of your system.  Do this on the HP Compaq.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

