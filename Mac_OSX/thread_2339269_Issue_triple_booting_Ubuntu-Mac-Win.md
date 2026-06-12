---
title: "Issue triple booting Ubuntu-Mac-Win"
date: 2016-10-06
forum: Mac OSX
---

### Post by elliot.campbell on 2016-10-06
Hi all,

I am having an issue triple booting an iMac with Ubuntu 16.04, Mac OS, and Windows 7 (through Bootcamp) installed. I have had Ubuntu installed for months and the triple-booting was working fine, but the other day I was unable to boot into Windows. I am still able to boot into Ubuntu or Mac OS fine.

When I select Windows from the rEFInd boot screen, the screen goes black for a second and I get the message "No bootable device -- insert boot disk and press any key". The computer doesn't respond at this point, even if I insert a bootable flash drive. 

I am guessing rEFInd or Grub somehow received an update and has messed up the boot record for the Windows partition. A boot info log is below. Any advice would be appreciated! 

Boot Info: [http://paste.ubuntu.com/23286157/](http://paste.ubuntu.com/23286157/)

Thanks!

---

### Post by oldfred on 2016-10-06
Moved to Apple Mac sub-forum where those who know Macs may offer to help.

---

### Post by elliot.campbell on 2016-10-11
Just an update, I've tried using a Windows 7 repair disk to repair the Windows bootloader with no luck. I always receive an error that the version of System Recovery I am using is not compatible with my version of Windows. 

I am pretty sure the OS is Win7 Enterprise 64-bit, but I have tried repair disks for Win7 Enterprise 64-bit, Win7 Enterprise 32-bit, Win7 Pro 64-bit, and Win7 Pro 32-bit and receive the same error message everytime. I even created a system recovery disk from an iMac running the same original Bootcamp installation and Windows version, and got the same error. 

Any ideas? There must be some way I can access the bootloader mounted in Ubuntu and fix whatever is preventing rEFInd from seeing the Windows installation, right?

---

### Post by oldfred on 2016-10-12
Older Windows had to be installed in BIOS mode and then only can boot from MBR partitions.
Newer Windows can be installed in UEFI mode and has to have gpt partitions.
Macs use gpt, but to make older Windows work used hybrid partitioning which is not recommended.
And Windows 7 installer defaults to BIOS/MBR. You have to convert installer to flash drive and move some files around to make it boot in UEFI mode.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

      [/URL]
 [http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html) 
    [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by elliot.campbell on 2016-10-12
Thanks, I will read up on this and give it a shot. 

What I don't understand is that the triple-booting was working fine for several months after I installed Ubuntu alongside Mac/Win7 Bootcamp - I could boot into all three OSes without issue. It was only recently I started receiving an error when trying to boot into Windows.

Could upgrading grub in Ubuntu have caused this? Is there an easy way to roll-back that change?

---

### Post by oldfred on 2016-10-12
I do not know Mac and all the details of multiple boot.
But it looks like you had a BIOS boot of Windows and had gptsync for hybrid configuration. But then the Windows partition would have to be in the first 4 partitions. But now you show the NTFS partition as sda6. And no UEFI boot of Windows in ESP - efi system partition.
So did partitions get renumbered, and then gptsync cannot have NTFS in first 4 partitions?

Ubuntu UEFI Mac install, answer by Rod Smith author of gdisk & rEFInd.
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios)

---

