---
title: "grub-common fails to work - falls down with error"
date: 2010-11-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2010-11-25
Anyone else having problems with grub-common 1.99-20101124-1ubuntu1 failing to load and falling back to an error message?

I get this occur if I try to boot:
```
error: symbol not found: 'grub_err_printed_errors'.
grub rescue>_
```
I can get to the desktop via my USB stick for some reason I can't fathom.

I'm wondering because no-one else seem to have started a thread on what is quite major breakage.

---

### Post by dino99 on 2010-11-25
have installed this latest grub and dont have trouble. Are you using removable devices or a foreign language? Seems that grub simply dont find its way: wrong or corrupted uuid in the grub menu, check with:

sudo blkid

note: glance at "strange" symbol in the boot line

---

### Post by Harry33 on 2010-11-25
The package "grub2" 1.99~20101124-1ubuntu1 works fine with my setups too.

---

### Post by kansasnoob on 2010-11-25
> **tghe-retford said:**
> Anyone else having problems with grub-common 1.99-20101124-1ubuntu1 failing to load and falling back to an error message?

I get this occur if I try to boot:
```
error: symbol not found: 'grub_err_printed_errors'.
grub rescue>_
```
I can get to the desktop via my USB stick for some reason I can't fathom.

I'm wondering because no-one else seem to have started a thread on what is quite major breakage.

So you can boot the installed Natty selecting "boot first hard disc" from the Live USB menu?

I've not encountered any Natty specific problem yet, but it may be helpful if we could see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions for the script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Most recently I had a box w/Lucid do that after some repartitioning because the repartitioning changed some partition designations. I managed to straighten it out quickly just by running "update-grub" in a chroot.

Could you also include a brief list of your hardware/computer brand and model?

There are a few hardware specific corner issues.

---

### Post by tghe-retford on 2010-11-25
> **dino99 said:**
> have installed this latest grub and dont have trouble. Are you using removable devices or a foreign language?
I have a USB stick in use during the update and what I suspect has happened is that grub2 has updated and put itself on the USB stick instead of the hard disk where it should be. It's weird because even with a USB stick in, this problem has never happened before.

Output of debconf-show grub-pc:
```
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: **/dev/disk/by-id/usb-HP_c485b_055FF1005160310487500123-0:0**
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: splash quiet
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
```
HP_C485b = USB stick!

I have also started a bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/681280](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/681280)
> **kansasnoob said:**
> So you can boot the installed Natty selecting "boot first hard disc" from the Live USB menu?

I've not encountered any Natty specific problem yet, but it may be helpful if we could see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions for the script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Most recently I had a box w/Lucid do that after some repartitioning because the repartitioning changed some partition designations. I managed to straighten it out quickly just by running "update-grub" in a chroot.

Could you also include a brief list of your hardware/computer brand and model?

There are a few hardware specific corner issues.
I added the results.txt file as a attachment considering how much information was reported.

As for my computer brand and hardware, luckily I have them written out somewhere ready to copy and paste:

- Intel Core2Quad Q6600 CPU @ 2.4Ghz
- ASUS P5N-E SLI motherboard
- 2GB OCZ 800MHz DDR2 PC2-6400 RAM
- 500GB Seagate SATA HDD
- Zotac 8800GT Amp! Edition overclocked NVidia graphics card
- X-Fi sound card (currently not in use)
- Hauppauge Nova-T 90002 PCI TV card for DVB-T (Freeview)
- Sony DVD-RW disc drive

---

### Post by kansasnoob on 2010-11-25
It appears to me that you're 100% correct:

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => [COLOR="Red"]Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for abdc3[/COLOR].

And sdb is clearly a flash drive:

> Disk /dev/sdb: 4105 MB, 4105175040 bytes

I think I saw something recently in the changelog so give me a bit and I'll see if I can find it. *I also want to check this against Maverick and Lucid changelogs!*

It's always excellent to see early testers locate bugs :)

I'm thinking you **may have** found a regression due to a recent update.

I'm curious if you do iso-testing? I ask because I've found that bugs reported during iso-testing/upgrade-testing seem to get a fast response.

Please be patient, I may be out for several hours (t-day here and all) :)

---

### Post by tghe-retford on 2010-11-25
> **kansasnoob said:**
> 
It's always excellent to see early testers locate bugs :)

I'm thinking you **may have** found a regression due to a recent update.

I'm curious if you do iso-testing? I ask because I've found that bugs reported during iso-testing/upgrade-testing seem to get a fast response.

Please be patient, I may be out for several hours (t-day here and all) :)
Thanks for your help and compliment, much appreciated. :)

As for your question, I don't do iso-testing, I normally just test out the KDE desktop and report bugs as and when they become apparent.

---

### Post by wilee-nilee on 2010-11-25
Here is the script so it can be viewed by all.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for abdc3.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   146,485,247   146,483,200  83 Linux
/dev/sda2         146,485,248   968,946,185   822,460,938  83 Linux
/dev/sda3         968,960,000   976,773,119     7,813,120  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4105 MB, 4105175040 bytes
127 heads, 62 sectors/track, 1018 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     8,015,731     8,015,670   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9537fc0a-769d-4bee-9d6d-7554e36ae1bd   ext4       TGHE Main                     
/dev/sda2        326e193b-2755-45da-8e77-f2c28c167107   ext4                                     
/dev/sda3        98255a5b-9cbe-4461-98b6-8bb4ae8a8cc2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        13F5-6584                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
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
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.lst
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
menuentry 'Ubuntu, with Linux 2.6.37-6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	linux	/boot/vmlinuz-2.6.37-6-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro   splash quiet
	initrd	/boot/initrd.img-2.6.37-6-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	echo	'Loading Linux 2.6.37-6-generic ...'
	linux	/boot/vmlinuz-2.6.37-6-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-6-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	linux	/boot/vmlinuz-2.6.37-5-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro   splash quiet
	initrd	/boot/initrd.img-2.6.37-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	echo	'Loading Linux 2.6.37-5-generic ...'
	linux	/boot/vmlinuz-2.6.37-5-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	linux	/boot/vmlinuz-2.6.37-4-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro   splash quiet
	initrd	/boot/initrd.img-2.6.37-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	if [ "$linux_gfx_mode" != text ]; then load_video; fi
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	echo	'Loading Linux 2.6.37-4-generic ...'
	linux	/boot/vmlinuz-2.6.37-4-generic root=UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-4-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9537fc0a-769d-4bee-9d6d-7554e36ae1bd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9537fc0a-769d-4bee-9d6d-7554e36ae1bd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=326e193b-2755-45da-8e77-f2c28c167107 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=98255a5b-9cbe-4461-98b6-8bb4ae8a8cc2 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  62.4GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.37-4-generic
   1.7GB: boot/initrd.img-2.6.37-5-generic
   2.5GB: boot/initrd.img-2.6.37-6-generic
  64.6GB: boot/vmlinuz-2.6.37-4-generic
  64.7GB: boot/vmlinuz-2.6.37-5-generic
  64.7GB: boot/vmlinuz-2.6.37-6-generic
   2.5GB: initrd.img
   1.7GB: initrd.img.old
  64.7GB: vmlinuz
  64.7GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install" {
	set gfxpayload=keep
	linux	/linux -- quiet
	initrd	/initrd.gz
}

menuentry "Command-line install" {
	set gfxpayload=keep
	linux	/linux tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false -- quiet
	initrd	/initrd.gz
}

menuentry "Expert install" {
	set gfxpayload=keep
	linux	/linux priority=low --
	initrd	/initrd.gz
}

menuentry "Command-line expert install" {
	set gfxpayload=keep
	linux	/linux tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low --
	initrd	/initrd.gz
}

menuentry "Rescue mode" {
	set gfxpayload=keep
	linux	/linux rescue/enable=true -- quiet
	initrd	/initrd.gz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
    ??GB: initrd.gz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7f 00 00 00 00 00  |........>.......|
00000020  36 4f 7a 00 88 1e 00 00  00 00 00 00 02 00 00 00  |6Oz.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 84 65 f5 13 20  20 20 20 20 20 20 20 20  |..).e..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b0 b4 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e d2 1d 08 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-25
You can boot in manually from that grub prompt without the USB flash

Manual boot from grub prompt for grub2

set root=(hd0,X)    (X=the partition # of OS) 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

notice bracketed areas are information not commands

In the debconf out put I also see this not sure if it is relevant.
 grub-pc/chainload_from_menu.lst: true

There is no menu.list in the script but this was still in the debconf, did you have another OS with grub-legacy at some point.

---

### Post by tghe-retford on 2010-11-25
> **wilee-nilee said:**
> You can boot in manually from that grub prompt without the USB flash

Manual boot from grub prompt for grub2

set root=(hd0,X)    (X=the partition # of OS) 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

notice bracketed areas are information not commands

In the debconf out put I also see this not sure if it is relevant.
 grub-pc/chainload_from_menu.lst: true

There is no menu.list in the script but this was still in the debconf, did you have another OS with grub-legacy at some point.
Thanks for the commands. I'll give it a go next time I boot, I can always use the USB stick to boot if I don't get it right.

As for another OS with grub-legacy, there isn't and hasn't been another OS on this computer, this is just being used to test Kubuntu. The USB stick did have a version of grub installed because I placed a minimal Kubuntu ISO on there using unetbootin (usb-creator-kde would not work due to a bug the last time I used it earlier this month).

EDIT: A reinstall of grub-common managed to restore grub2 on the hard disk. However, doesn't resolve the problem of why grub2 installed onto the USB stick and screwed up grub2 on the hard disk.

---

### Post by wilee-nilee on 2010-11-25
> **tghe-retford said:**
> Thanks for the commands. I'll give it a go next time I boot, I can always use the USB stick to boot if I don't get it right.

As for another OS with grub-legacy, there isn't and hasn't been another OS on this computer, this is just being used to test Kubuntu. The USB stick did have a version of grub installed because I placed a minimal Kubuntu ISO on there using unetbootin (usb-creator-kde would not work due to a bug the last time I used it earlier this month).

EDIT: A reinstall of grub-common managed to restore grub2 on the hard disk. However, doesn't resolve the problem of why grub2 installed onto the USB stick and screwed up grub2 on the hard disk.

kansanoob would have a better answer here, but without knowing what happened, grub sometimes will be pointed at the HD or a external install say to a thumb, you just have to know where the put grub portion is in the install gui and make sure it is where you want it.

Could be some sort of bug but personally I doubt it, I have never had a problem nor seen one that was not a users fault so to speak.

With the manual boot in just run 
```
sudo-update-grub
```
once in

---

### Post by tghe-retford on 2010-11-25
> **wilee-nilee said:**
> kansanoob would have a better answer here, but without knowing what happened, grub sometimes will be pointed at the HD or a external install say to a thumb, you just have to know where the put grub portion is in the install gui and make sure it is where you want it.

Could be some sort of bug but personally I doubt it, I have never had a problem nor seen one that was not a users fault so to speak.
All I did was:

```
sudo aptitude safe-upgrade
```

grub-common and grub-pc were the two packages which got updated and they updated without the need for any user input from me. One minute grub2 is installed on the hard disk, the next minute it's on both the hard disk and the USB stick, but only grub2 on the USB stick works.

Very odd...

---

### Post by cariboo on 2010-11-25
You can install grub on the right hard drive using the Live CD/USB. Once you are at the desktop, open a terminal and type:

[LIST]
[*]sudo mount /dev/sdaX /mnt
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Substitute your / partition for /dev/sdaX

Once you are in the chroot type:

```
sudo grub-install /dev/sda
```

Then once the command has finished type:

```
sudo update-grub
```

Ctrl-D out of the chroot and terminal and reboot.

---

### Post by wilee-nilee on 2010-11-25
So the safe-upgrade though was from Maverick to Natty correct. If this is the case you should have not had that thumb plugged in, if I'm correct here, you had no time to point grub correctly. You probably did with a command line but personally I just know the key cli I need.

If my hypothesis is somewhat correct we have to remember that your computer is a box of circuits, it needs some direction at times.;)

And even if it was a safe-upgrade in natty for updates, you have to watch out for stuff. Never know though could be a grub bug, but kansasnoob is as advanced as they are looking for these bugs so may easily like all of us use confirmation bias at first before confirming. Sorry kansanoob you know I respect your work but these sort of bias plague us all.;)

---

### Post by kansasnoob on 2010-11-26
I decided to try and reproduce this behavior with a couple of differences: I'm using Ubuntu instead of Kubuntu, and my Live USB was created using Startup Disc Creator.

It was really easy because there was another grub2 update waiting for me this AM, but before applying the updates I ran "sudo dpkg-reconfigure grub-pc" with the flash drive plugged in just to check the starting point:

[ATTACH]176645[/ATTACH]

Then I checked with the Boot Info Script:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #16 for (,msdos16)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

Anyway I completed that update without a problem. I double checked with both 'dpkg-reconfigure' and by running the Boot Info Script again, and it worked fine.

But I downloaded the pertinent parts of the changelog:

> grub2 (1.99~20101124-1ubuntu1) natty; urgency=low

  [ Colin Watson ]
  * Resynchronise with Debian experimental.  Remaining changes:
    - Adjust for default Ubuntu boot options ("quiet splash").
    - Default to hiding the menu; holding down Shift at boot will show it.
    - Set a monochromatic theme for Ubuntu.
    - Apply Ubuntu GRUB Legacy changes to legacy update-grub script: title,
      recovery mode, quiet option, tweak how memtest86+ is displayed, and
      use UUIDs where appropriate.
    - Fix backslash-escaping in merge_debconf_into_conf.
    - Remove "GNU/Linux" from default distributor string.
    - Add crashkernel= options if kdump and makedumpfile are available.
    - If other operating systems are installed, then automatically unhide
      the menu.  Otherwise, if GRUB_HIDDEN_TIMEOUT is 0, then use keystatus
      if available to check whether Shift is pressed.  If it is, show the
      menu, otherwise boot immediately.  If keystatus is not available, then
      fall back to a short delay interruptible with Escape.
    - Allow Shift to interrupt 'sleep --interruptible'.
    - Don't display introductory message about line editing unless we're
      actually offering a shell prompt.  Don't clear the screen just before
      booting if we never drew the menu in the first place.
    - Remove some verbose messages printed before reading the configuration
      file.
    - Suppress progress messages as the kernel and initrd load for
      non-recovery kernel menu entries.
    - Change prepare_grub_to_access_device to handle filesystems
      loop-mounted on file images.
    - Ignore devices loop-mounted from files in 10_linux.
    - Show the boot menu if the previous boot failed, that is if it failed
      to get to the end of one of the normal runlevels.
    - Don't generate /boot/grub/device.map during grub-install or
      grub-mkconfig by default.
    - Adjust upgrade version checks for Ubuntu.
    - Don't display "GRUB loading" unless Shift is held down.
    - Adjust versions of grub-doc and grub-legacy-doc conflicts to tolerate
      our backport of the grub-doc split.
    - Fix LVM/RAID probing in the absence of /boot/grub/device.map.
    - Look for .mo files in /usr/share/locale-langpack as well, in
      preference.
    - Make sure GRUB_TIMEOUT isn't quoted unnecessarily.
    - Probe all devices in 'grub-probe --target=drive' if
      /boot/grub/device.map is missing.
    - Build-depend on qemu-kvm rather than qemu-system for grub-pc tests.
    - Use qemu rather than qemu-system-i386.
    - Program vesafb on BIOS systems rather than efifb.
    - Add a grub-rescue-efi-amd64 package containing a rescue CD-ROM image
      for EFI-AMD64.
    - On Wubi, don't ask for an install device, but just update wubildr
      using the diverted grub-install.
    - When embedding the core image in a post-MBR gap, check for and avoid
      sectors matching any of a list of known signatures.
    - Disable video_bochs and video_cirrus on PC BIOS systems, as probing
      PCI space seems to break on some systems.
  * Downgrade "ACPI shutdown failed" error to a debug message, since it can
    cause spurious test failures.

  [ Evan Broder ]
  * Enable lua from grub-extras.
  * Incorporate the bitop library into lua.
  * Add enum_pci function to grub module in lua.
  * Switch back to gfxpayload=keep by default, unless the video hardware
    is known to not support it.

  [ Mario Limonciello ]
  * Built part_msdos and vfat into bootx64.efi (LP: #677758)

 -- Colin Watson <cjwatson@ubuntu.com>  Wed, 24 Nov 2010 13:59:55 +0000

grub2 (1.99~20101124-1) experimental; urgency=low

  * New Bazaar snapshot (command priorities, build fixes, grub-mkdevicemap
    segfault).
  * Don't try to build grub-efi-amd64 on kfreebsd-i386 or hurd-i386
    (requires gcc-4.4-multilib).

 -- Colin Watson <cjwatson@debian.org>  Wed, 24 Nov 2010 12:12:33 +0000

grub2 (1.99~20101123-1) experimental; urgency=low

  * New Bazaar snapshot (build fixes).
  * Build-depend on qemu-utils and parted on non-Hurd architectures.
  * qemu_img_exists.patch: Skip partmap test if qemu-img doesn't exist (as
    is the case on the Hurd).
  * Make grub-efi-ia32 and grub-efi-amd64 depend on efibootmgr so that
    grub-install works properly.
  * Upgrade the installed core image when upgrading grub-efi-ia32 or
    grub-efi-amd64, although only if /boot/efi/EFI/<id> (where <id> is an
    identifier based on GRUB_DISTRIBUTOR, e.g. 'debian') already exists.
  * Re-expand a couple of dpkg architecture wildcards to exclude certain
    special cases: gcc-4.4-multilib is not available on kfreebsd-i386 or
    hurd-i386, and qemu-system is not available on hurd-i386.

 -- Colin Watson <cjwatson@debian.org>  Tue, 23 Nov 2010 10:51:23 +0000

grub2 (1.99~20101122-1) experimental; urgency=low

  [ Colin Watson ]
  * New Bazaar snapshot.  Too many changes to list in full, but some of the
    more user-visible ones are as follows:
    - GRUB script:
      + Function parameters, "break", "continue", "shift", "setparams",
        "return", and "!".
      + "export" command supports multiple variable names.
      + Multi-line quoted strings support.
      + Wildcard expansion.
    - sendkey support.
    - USB hotunplugging and USB serial support.
    - Rename CD-ROM to cd on BIOS.
    - Add new --boot-directory option to grub-install, grub-reboot, and
      grub-set-default; the old --root-directory option is still accepted
      but was often confusing.
    - Basic btrfs detection/UUID support (but no file reading yet).
    - bash-completion for utilities.
    - If a device is listed in device.map, always assume that it is
      BIOS-visible rather than using extra layers such as LVM or RAID.
    - Add grub-mknetdir script (closes: #550658).
    - Remove deprecated "root" command.
    - Handle RAID devices containing virtio components.
    - GRUB Legacy configuration file support (via grub-menulst2cfg).
    - Keyboard layout support (via grub-mklayout and grub-kbdcomp).
    - Check generated grub.cfg for syntax errors before saving.
    - Pause execution for at most ten seconds if any errors are displayed,
      so that the user has a chance to see them.
    - Support submenus.
    - Write embedding zone using Reed-Solomon, so that it's robust against
      being partially overwritten (closes: #550702, #591416, #593347).
    - GRUB_DISABLE_LINUX_RECOVERY and GRUB_DISABLE_NETBSD_RECOVERY merged
      into a single GRUB_DISABLE_RECOVERY variable.
    - Fix loader memory allocation failure (closes: #551627).
    - Don't call savedefault on recovery entries (closes: #589325).
    - Support triple-indirect blocks on ext2 (closes: #543924).
    - Recognise DDF1 fake RAID (closes: #603354).

  [ Robert Millan ]
  * Use dpkg architecture wildcards.

  [ Updated translations ]
  * Slovenian (Vanja Cvelbar).  Closes: #604003
  * Dzongkha (dawa pemo via Tenzin Dendup).  Closes: #604102

 -- Colin Watson <cjwatson@debian.org>  Mon, 22 Nov 2010 12:24:56 +0000


So I'm in hopes this was just a glitch :)

It'll be interesting to see what happens when I perform upgrade and iso-testing.

---

