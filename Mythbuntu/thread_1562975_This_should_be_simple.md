---
title: "This should be simple"
date: 2010-08-28
forum: Mythbuntu
---

### Post by MikeKulls on 2010-08-28
Hi Guys and Girls,

I'm trying to install mythbuntu on a 2TB drive but only use 20GB (with all other space unused). It seems that auto options don't allow this so I have to choose manually setup partitions. I go in and create my partition of 20GB as ext4 and set it as /. It gives me a warning about no swap partition which I presume I can ignore for now. The install proceeds as normal but when I reboot I get "No bootable device -- insert boot disk and press any key". What am I doing wrong? There seems to be very few options for partitioning during the install.

I've tried rebooting with the CD, installing gparted and setting my 20GB partition as boot with no luck.

I've tried making a partition for /boot in the installer and then my 20 GB partition for /. Same problem.

I've tried creating a swap partition with and without a boot partition.

I know this is my first question here and it's likely people will tell me to use google. I have tried that for the last hour and every link appears to refer to either installing on a PC with XP on it or for using the entire HDD.

Thanks in advance,
Mike

---

### Post by MikeKulls on 2010-08-28
OK, I've tried again with all auto options using full hard drive, same problem. Then I tried on a 100GB disk and it worked first go. Looks like ubuntu has a drive size limit. I'm using one of the latest intel boards (boxd510mo) so surely it's not the board. Does anyone have any suggestions of anything else I could try?

---

### Post by Jeruvy on 2010-08-28
Regardless of whether you have another OS like Windows or not, partitioning basics are the same.  Since you are working with a fresh new disk with no prior OS's you cannot lose anything, so don't be afraid to do this a few times to get the hang of it.  I know my first attempt at manual partitioning was a bit screwed up, but the second and further attempts worked as I desired.  I know only install after manually setting up the partitions.  This help page will describe everything you need, but if you need some help or clarification feel free to reply back.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck,

---

### Post by presence1960 on 2010-08-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by MikeKulls on 2010-08-28
> **Jeruvy said:**
> Regardless of whether you have another OS like Windows or not, partitioning basics are the same.  Since you are working with a fresh new disk with no prior OS's you cannot lose anything, so don't be afraid to do this a few times to get the hang of it.  I know my first attempt at manual partitioning was a bit screwed up, but the second and further attempts worked as I desired.  I know only install after manually setting up the partitions.  This help page will describe everything you need, but if you need some help or clarification feel free to reply back.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck,

Thanks for the reply. I have already tried every option under the sun I could think of. I think I've install ubuntu 10 times at least (it's a lot quicker than installing an MS OS luckily). It doesn't look like i'm doing anything wrong however as when I selected all automatic options I got the same error. I did find the link above when I searched originally but when I followed those instructions I got the same error. I've even tried all sorts of combinations of BIOS settings also.

I just tried to install XP to see if it was a hardware problem but XP worked ok as long as I had the SATA mode set to IDE and not the other option (can't remember the acronym at the mo). I've tried ubuntu with both these options.

---

### Post by MikeKulls on 2010-08-28
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Will do, I'm just reinstalling ubuntu now after testing XP. I have to go out so it might be a few hours before I can reply back.

Thanks for the reply.

Cheers,
Michael

---

### Post by MikeKulls on 2010-08-29
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Ok, here it is. This was created with the following install settings
- full HDD, automatic install
- SATA mode in the bios set to IDE

Thanks again for your help,
Michael


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Bios Boot Partition
/dev/sda2           4,096 3,883,352,063 3,883,347,968 Linux or Data
/dev/sda3   3,883,352,064 3,907,028,991    23,676,928 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        b695864d-29b9-43dc-8318-8796f1f00c6d   ext4                                     
/dev/sda3        f4d55e0f-0d30-4662-85e2-8114fd74531c   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b695864d-29b9-43dc-8318-8796f1f00c6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b695864d-29b9-43dc-8318-8796f1f00c6d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b695864d-29b9-43dc-8318-8796f1f00c6d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b695864d-29b9-43dc-8318-8796f1f00c6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f4d55e0f-0d30-4662-85e2-8114fd74531c none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


1365.9GB: boot/grub/core.img
1451.8GB: boot/grub/grub.cfg
1365.9GB: boot/initrd.img-2.6.32-21-generic
1365.9GB: boot/vmlinuz-2.6.32-21-generic
1365.9GB: initrd.img
1365.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200
```

---

### Post by Sef on 2010-08-29
Moved to Mythbuntu subforum.

---

### Post by DemonBob on 2010-08-29
Since you have the system installed it may be easier to use the [Gparted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") to resive the partition how you want it.

---

### Post by MikeKulls on 2010-08-29
> **DemonBob said:**
> Since you have the system installed it may be easier to use the [Gparted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") to resive the partition how you want it.

That was one of the things I was considering but it still doesn't boot when I use the fully auto options. I presume I would be able to resize the OS partition?

---

### Post by srs5694 on 2010-08-29
Your disk is partitioned using the GUID Partition Table (GPT) scheme, rather than the older and more common Master Boot Record (MBR) system. GPT can and does work (I've got several systems that boot from GPT), but my suspicion is that your problem is related to GPT. Some specific suggestions:


[list]
[*]Post more hardware information, especially including your computer or motherboard make and model.
[*]If you've got a BIOS-based computer (most systems today are BIOS-based, but some use the newer EFI or UEFI), check my ["Legacy BIOS issues with GPT"](http://nessus.rodsbooks.com/gdisk/bios.html) page. It lists several possible issues. My first suspicion is that you need to use Linux fdisk to mark the one and only MBR partition (of type "ee") active.
[*]Use an emergency disk system to re-install GRUB 2. I note that the Boot Info Script output claims that the core.img contents can't be found where it should be found, but I'm not sure this report is reliable in the case of GRUB 2. If it is reliable, manually re-installing GRUB 2 should fix the problem.
[*]If the computer's BIOS has an EFI-compatibility mode, try activating it and re-installing.
[*]Use GParted, gdisk, or some other tool to convert the disk from GPT to MBR form and re-install using MBR. Note that some tools, such as Linux fdisk, will do an incomplete job of such a conversion, so you've got to be sure to use a tool that will completely wipe the GPT data.
[/list]

---

### Post by MikeKulls on 2010-09-01
> **srs5694 said:**
> Your disk is partitioned using the GUID Partition Table (GPT) scheme, rather than the older and more common Master Boot Record (MBR) system. GPT can and does work (I've got several systems that boot from GPT), but my suspicion is that your problem is related to GPT. Some specific suggestions:


[list]
[*]Post more hardware information, especially including your computer or motherboard make and model.
[*]If you've got a BIOS-based computer (most systems today are BIOS-based, but some use the newer EFI or UEFI), check my ["Legacy BIOS issues with GPT"](http://nessus.rodsbooks.com/gdisk/bios.html) page. It lists several possible issues. My first suspicion is that you need to use Linux fdisk to mark the one and only MBR partition (of type "ee") active.
[*]Use an emergency disk system to re-install GRUB 2. I note that the Boot Info Script output claims that the core.img contents can't be found where it should be found, but I'm not sure this report is reliable in the case of GRUB 2. If it is reliable, manually re-installing GRUB 2 should fix the problem.
[*]If the computer's BIOS has an EFI-compatibility mode, try activating it and re-installing.
[*]Use GParted, gdisk, or some other tool to convert the disk from GPT to MBR form and re-install using MBR. Note that some tools, such as Linux fdisk, will do an incomplete job of such a conversion, so you've got to be sure to use a tool that will completely wipe the GPT data.
[/list]

Thanks for the reply, I will give all these things a try and let you know how it goes. I won't have time for the next couple of days but am pretty keen to get this working. My MythTV book just arrived from amazon thankfully (I was stuck reading a BSD command line book on the train each day :-)

Thanks again,
Michael

---

