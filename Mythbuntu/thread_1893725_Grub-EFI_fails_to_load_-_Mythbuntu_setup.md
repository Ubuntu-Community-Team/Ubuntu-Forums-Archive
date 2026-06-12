---
title: "Grub-EFI fails to load - Mythbuntu setup"
date: 2011-12-10
forum: Mythbuntu
---

### Post by pgjohnson on 2011-12-10
I&#8217;m attempting to load MythBuntu onto an out of the box HTPC system via an .ISO image loaded into a pendrive, configured for booting using Universal-USB-Installer-1.8.7.3.

It all goes well until nearly the end when it stops on "Error &#8211; Unable to load grub-efi package to /target/ &#8230;. without the boot loader&#8221; &#8230;.etc etc 

My presumption is that the boot loader is unable to access &#8220;/&#8221; hence the error message &#8220;/target/&#8221; &#8211; either because it is not there or the permissions are wrong. 
   
  I have had a tinker with the partioning during the early part of the install &#8211; there is no option to set the efi partition to &#8220;/&#8221; &#8211; it&#8217;s greyed out as I guess it should be as there's only the one place it can reside. 
   
  Any help would be appreciated &#8211; it is tantalizingly close ..
  Paul J 
   
  System
  Mobo &#8211; ASUS Maximus Genie Z 
  Intel Core I5 Processor 
  8GB memory
  1 TB HDD 
  Haupaugge 2200 TV card
  Nvidia graphics card 
  ISO image - mythbuntu-11.10-desktop-amd64

---

### Post by nickrout on 2011-12-11
googling that message gives a number of threads. Read them all and see if you can find the answer.

---

### Post by pgjohnson on 2011-12-11
> **nickrout said:**
> googling that message gives a number of threads. Read them all and see if you can find the answer.
Read them all? It would be quicker to load W7 and WMC. Amazing. I did not expect 
to get blocked by a boot loader! 

On on

---

### Post by oldfred on 2011-12-11
You set the efi partition flag to boot.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Grub does have some bugs with efi:
UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

May have related info:
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by nickrout on 2011-12-11
> **pgjohnson said:**
> Read them all? It would be quicker to load W7 and WMC. Amazing. I did not expect 
to get blocked by a boot loader! 

On on

Sorry I really meant that you need to do some reading - obviously once you find the answer you can stop at that point.

But you sound like you expect someone else to do your googling and reading.

---

### Post by pgjohnson on 2011-12-11
> **nickrout said:**
> Sorry I really meant that you need to do some reading - obviously once you find the answer you can stop at that point.

But you sound like you expect someone else to do your googling and reading.
Oh no - I'm fully qualified as a man and therefore don't "expect" anything - I thought it was a piece of simple ignorance of mine, not a fundamental ****-up with linux boot loaders. 

Anyway  - sorted meantime - cooked up a bootable pendrive with super_grub2_disk_hybrid_1.99b1.iso on it and this gets me into Myth OK. 

Currently downloading rescatux_cdrom_usb_hybrid_i386_486-amd64_0.30b3.iso which at our ISP speed up here will take about 19 hours. This may help if oldfreds advice stumbles.

Back to google and oldfreds post (thanks). 

PJ

---

### Post by superm1 on 2011-12-11
> **pgjohnson said:**
> I’m attempting to load MythBuntu onto an out of the box HTPC system via an .ISO image loaded into a pendrive, configured for booting using Universal-USB-Installer-1.8.7.3.

It all goes well until nearly the end when it stops on "Error – Unable to load grub-efi package to /target/ …. without the boot loader” ….etc etc 

My presumption is that the boot loader is unable to access “/” hence the error message “/target/” – either because it is not there or the permissions are wrong. 
   
  I have had a tinker with the partioning during the early part of the install – there is no option to set the efi partition to “/” – it’s greyed out as I guess it should be as there's only the one place it can reside. 
   
  Any help would be appreciated – it is tantalizingly close ..
  Paul J 
   
  System
  Mobo – ASUS Maximus Genie Z 
  Intel Core I5 Processor 
  8GB memory
  1 TB HDD 
  Haupaugge 2200 TV card
  Nvidia graphics card 
  ISO image - mythbuntu-11.10-desktop-amd64

This actually sounds like a bug in that GRUB2's EFI package isn't on the pool on the mythbuntu 64 bit media.  could you please file a bug at launchpad.net/ubuntu/+source/mythbuntu-meta ?

Thanks

---

### Post by pgjohnson on 2011-12-12
> **superm1 said:**
> ...  could you please file a bug at launchpad.net/ubuntu/+source/mythbuntu-meta ?

Thanks

Done - I note that the EFI folders on the HDD are not comparable with the pendrive EFI folders. I will attempt to copy over the EFI files to the HDD (boots OK on the pendrive), so maybe its boot files are OK to use? I'm probably being naive but what the hell. It's been over 15 years since I worked in Unix/Linux. 

At this stage of the install I don't mind fiddling about - if it all falls in a heap I can simply start again.

Meantime I am enjoying my Mythbuntu experience - a credit to all those who work and play on this system. :P 

PJ

---

### Post by pgjohnson on 2011-12-12
> **superm1 said:**
> This actually sounds like a bug in that GRUB2's EFI package isn't on the pool on the mythbuntu 64 bit media.  could you please file a bug at launchpad.net/ubuntu/+source/mythbuntu-meta ?

Thanks for filing the bug.  Unfortunately it won't be easy to resolve
this on  the 11.10 media, but I've committed a fix for 12.04's seeds.
Grub-efi will be  seeded on amd64 and added to the pool.

For your 11.10 install, if you are  able to at least boot off the pen
drive like that,  you can probably get GRUB  for EFI installed actually.
Here's some pseudodirections:

1) Boot your  install
2) Check and see which EFI partition got mounted at /boot using the  'mount' command
3) If your HDD's first partition (EFI System Partition) isn't  mounted at /boot, mount it manually
4) Install the 'grub-efi' package.   apt-get install grub-efi
5) Run 'grub-install'

That should hopefully  install grub to the efi system partition for you.

** Also affects:  mythbuntu-meta (Ubuntu Oneiric)
   Importance: Undecided
       Status:  New

** Also affects: mythbuntu-meta (Ubuntu Precise)
   Importance:  Undecided
       Status: Fix Committed

** Changed in: mythbuntu-meta  (Ubuntu Oneiric)
       Status: New => Won't Fix


The above may help someone else meantime. I've run the prgs above but on booting from the HDD get the blank screen - also there is now a grub mount option in the BIOS which takes me to the grub OS.

P

---

