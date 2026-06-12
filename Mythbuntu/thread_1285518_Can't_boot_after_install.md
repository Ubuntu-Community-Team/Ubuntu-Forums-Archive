---
title: "Can't boot after install"
date: 2009-10-07
forum: Mythbuntu
---

### Post by Gibble on 2009-10-07
So, I've attempted to install Jaunty mythbuntu about 5 times, and after each, it won't boot.

The machine has three drives
IDE Western Digital 160gb 
SATA Samsung 250gb
SATA Western Digital 1500gb

The IDE is the primary boot drive in the BIOS.

During the install, when it came time to setup the partitions I selected manual and entered the following
**IDE WD 160GB - sdc**
[FONT="Courier New"]sdc6 - 500mb - EXT3 - /boot
sdc1 -  20gb - EXT3 - /
sdc5 -   2gb - SWAP
sdc7 - 137.5gb - XFS - /storage/wd160gb
[/FONT]
**SATA Samsung 250GB - sda**
[FONT="Courier New"]sda1 - * - XFS - /storage/sp250gb
[/FONT]
**SATA WD 1500GB - sdb**
[FONT="Courier New"]sdb1 - * - XFS - /storage/wd1500gb
[/FONT]

On the advanced screen I told it to load the bootloader to sdc

It then tries to load mythtv-setup.real which fails (black screen which it can't render) because I need to setup nvidia drivers (I think)

The problem is when it reboots, I see **Grub Error 17**!

EVERY SINGLE TIME!!! :(

Please help!

---

### Post by booshire on 2009-10-07
Flash BIOS?

---

### Post by Gibble on 2009-10-07
> **booshire said:**
> Flash BIOS?

Nope, Phoenix.

---

### Post by RockDoctor on 2009-10-07
> **Gibble said:**
> So, I've attempted to install Jaunty mythbuntu about 5 times, and after each, it won't boot.

The machine has three drives
IDE Western Digital 160gb 
SATA Samsung 250gb
SATA Western Digital 1500gb

The IDE is the primary boot drive in the BIOS.

<snip>

The problem is when it reboots, I see **Grub Error 17**!

EVERY SINGLE TIME!!! :(

Please help!
No guarantees, but here's what comes to mind:
1. It's possible that grub isn't seeing the drives in the order you think it should - that is, what you think of as /dev/sdc grub may be treating as (hd0) or (hd1) rather than (hd2)
2. If your BIOS is old, it's possible that the boot partition needs to be within the first 1024 cylinders.

---

### Post by klc5555 on 2009-10-07
> **Gibble said:**
> So, I've attempted to install Jaunty mythbuntu about 5 times, and after each, it won't boot.

The machine has three drives
IDE Western Digital 160gb 
SATA Samsung 250gb
SATA Western Digital 1500gb

The IDE is the primary boot drive in the BIOS.

During the install, when it came time to setup the partitions I selected manual and entered the following
**IDE WD 160GB - sdc**
[FONT="Courier New"]sdc6 - 500mb - EXT3 - /boot
sdc1 -  20gb - EXT3 - /
sdc5 -   2gb - SWAP
sdc7 - 137.5gb - XFS - /storage/wd160gb
[/FONT]
**SATA Samsung 250GB - sda**
[FONT="Courier New"]sda1 - * - XFS - /storage/sp250gb
[/FONT]
**SATA WD 1500GB - sdb**
[FONT="Courier New"]sdb1 - * - XFS - /storage/wd1500gb
[/FONT]

On the advanced screen I told it to load the bootloader to sdc

It then tries to load mythtv-setup.real which fails (black screen which it can't render) because I need to setup nvidia drivers (I think)

The problem is when it reboots, I see **Grub Error 17**!

EVERY SINGLE TIME!!! :(

Please help!

A common glitch with Ubuntu. But not usually serious. Grub uses its own arcane drive nomenclature, and what with Ubuntu strangely labelling all drives as scsi devices, and not in the same order as Grub, Grub tends to get very confused when IDE and SATA drives are both present --after install the two halves of the bootloader can't find each other. The solution usually is after install to boot from the CD and run Grub as follows:

1) sudo grub
2) find /boot/grub/stage1 (this will give an output of (hd#,#))
3) root (hd#,#)   (where #,# are the numbers found in step 2)
4) setup (hd0)
5) quit
6) reboot

This generally should do it.

---

### Post by Gibble on 2009-10-08
grub> find /boot/grub/stage1

Error 15: File not found



When I boot from the CD which option should I be using?

---

### Post by klc5555 on 2009-10-09
> **Gibble said:**
> grub> find /boot/grub/stage1

Error 15: File not found



When I boot from the CD which option should I be using?

If grub can't find the stage1 files at all, then it would appear that grub hasn't been completely installed.

This becomes a bit more complicated, but there are two good documents to help you. The first is the installation section of gnu.org's own grub manual: [http://www.gnu.org/software/grub/manual/grub.html#Installation](http://www.gnu.org/software/grub/manual/grub.html#Installation)  

The second is the Ubuntu documentation page referring to grub, at: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

There is also an earlier forum thread detailing how to do a text-mode install of grub in Ubuntu from the installation CD. (Written in 2006-2008, but should still hold for any version of Ubuntu prior to 9.10) Here: [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

After you're pretty sure you've got grub installed, you can give another reboot a try. It may fail with something along the lines of an error 2. This will be because grub sees your ide drive, at what the non-Ubuntu world would properly call /dev/hda as your _first_ drive, whereas Ubuntu insists on defining it as your _third_ drive, at /dev/sdc, after your sata drives. At this point finding the stage1 files and configuring as described earlier should work.

Good luck!

---

