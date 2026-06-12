---
title: "Grub 2 after 11.04 upgrade"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-04-01
Last night I upgraded 10.10 to 11.04.  All went well except when I boot my computer I do not get the grub bootloader.  Bios boots then my monitor goes blank and gives me an out of range message.  Then after 30 seconds or so I boot into 11.04.  I tried to reinstall grub but no difference.  

When I run sudo update-grub, this is my output:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-7-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-7-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done

So I have a feeling that I must have grub in the wrong place or the boot order is wrong.  I attached the results of boot info script.  Thanks for the help

---

### Post by Hedgehog1 on 2011-04-01
Here is that script result in a '#' 'CODE, /CODE tags' (so we can read it easier):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks for Ae.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   234,581,847   234,375,000   7 HPFS/NTFS
/dev/sdb3         234,582,014   976,771,071   742,189,058   5 Extended
/dev/sdb5         234,582,016   242,395,135     7,813,120  82 Linux swap / Solaris
/dev/sdb6         242,397,184   302,942,207    60,545,024  83 Linux
/dev/sdb7         302,944,256   303,429,631       485,376  83 Linux
/dev/sdb8         303,431,680   976,771,071   673,339,392  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0CCED1BA7E26BEBA                       ntfs       EXTERNAL                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A06C22B36C2283DE                       ntfs       System Reserved               
/dev/sdb2        5C7C25487C251E70                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        a897162d-73d4-4aaa-97eb-91c9135fa803   swap                                     
/dev/sdb6        826eb711-8e2a-47d1-9dcd-fe766d4cc575   ext4                                     
/dev/sdb7        b930b9ee-95c2-402e-91cc-70e177a144fe   ext4                                     
/dev/sdb8        52c68b0e-0557-41a0-95f0-4a22685948c1   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /boot                    ext4       (rw,commit=0)
/dev/sdb8        /home                    ext4       (rw,commit=0)
/dev/sda1        /media/EXTERNAL          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=826eb711-8e2a-47d1-9dcd-fe766d4cc575 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb7 during installation
UUID=b930b9ee-95c2-402e-91cc-70e177a144fe /boot           ext4    defaults        0       2
# /home was on /dev/sdb8 during installation
UUID=52c68b0e-0557-41a0-95f0-4a22685948c1 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=a897162d-73d4-4aaa-97eb-91c9135fa803 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 124.1GB: initrd.img
 124.1GB: initrd.img.old
 124.1GB: vmlinuz
 124.1GB: vmlinuz.old

============================= sdb7/grub/grub.cfg: =============================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 826eb711-8e2a-47d1-9dcd-fe766d4cc575
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
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
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-7-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	linux	/vmlinuz-2.6.38-7-generic-pae root=UUID=826eb711-8e2a-47d1-9dcd-fe766d4cc575 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-7-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	echo	'Loading Linux 2.6.38-7-generic-pae ...'
	linux	/vmlinuz-2.6.38-7-generic-pae root=UUID=826eb711-8e2a-47d1-9dcd-fe766d4cc575 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-7-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=826eb711-8e2a-47d1-9dcd-fe766d4cc575 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=826eb711-8e2a-47d1-9dcd-fe766d4cc575 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root b930b9ee-95c2-402e-91cc-70e177a144fe
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root A06C22B36C2283DE
	chainloader +1
}
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

=================== sdb7: Location of files loaded by Grub: ===================


 155.1GB: grub/core.img
 155.1GB: grub/grub.cfg
 155.1GB: initrd.img-2.6.35-28-generic-pae
 155.1GB: initrd.img-2.6.38-7-generic-pae
 155.1GB: vmlinuz-2.6.35-28-generic-pae
 155.1GB: vmlinuz-2.6.38-7-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  4b 52 87 2f bc ff dd cb  08 d2 cc 74 5c 0e a4 de  |KR./.......t\...|
00000010  98 42 2e 33 4e 47 f4 ee  c2 c6 0c 40 9d 52 15 d0  |.B.3NG.....@.R..|
00000020  27 08 89 96 2e d8 08 b6  76 2c b8 99 33 ff a0 ff  |'.......v,..3...|
00000030  27 1a 13 9f ce 31 29 51  b5 c1 26 bc 8c 26 23 21  |'....1)Q..&..&#!|
00000040  71 dc ad 27 69 77 ab 13  6d 82 52 a5 a6 cd f8 4d  |q..'iw..m.R....M|
00000050  24 33 d1 d7 c8 cc c2 80  61 a4 e8 2d 81 3d 83 c5  |$3......a..-.=..|
00000060  58 74 a0 4c 42 33 49 03  7a 12 8c c3 30 f4 3f 53  |Xt.LB3I.z...0.?S|
00000070  1d 6f 9f 35 33 ab a9 1c  a2 c1 27 4f fd 10 d7 61  |.o.53.....'O...a|
00000080  53 fa 70 bd 03 47 c8 18  72 ef 83 fa 06 ab 34 0a  |S.p..G..r.....4.|
00000090  e5 31 c0 61 5e c2 fa 15  bc f3 e0 d9 c3 ed 13 6d  |.1.a^..........m|
000000a0  03 5a 67 e8 9b eb 13 3b  b4 fd 3a 56 8e ee f0 59  |.Zg....;..:V...Y|
000000b0  a4 dd d8 20 02 c3 72 cb  70 56 68 28 a9 03 5c 6f  |... ..r.pVh(..\o|
000000c0  42 cf 37 ab 65 b8 2d b2  c5 cd 48 19 30 00 09 f1  |B.7.e.-...H.0...|
000000d0  1f 02 6c 7f 6a 26 03 88  c7 a1 27 0d 6b 9c e5 09  |..l.j&....'.k...|
000000e0  a9 57 81 69 07 3a 96 0d  45 0f 06 60 8b 20 17 a2  |.W.i.:..E..`. ..|
000000f0  d8 4c b3 96 18 fa 4e 81  f2 88 d6 18 9b f1 e6 3e  |.L....N........>|
00000100  4d f6 09 0f 17 4b be ed  9d 99 3b 84 8f 08 5a c0  |M....K....;...Z.|
00000110  2b cc c2 ff b2 0e bb d8  81 6f 2c db b6 7d c2 48  |+........o,..}.H|
00000120  24 c6 75 0e e1 26 65 f4  9a 07 9a 5b ed 61 c4 e8  |$.u..&e....[.a..|
00000130  dd be 4e b8 3f f5 bf 1c  b5 c4 f2 cc c2 0e 94 9f  |..N.?...........|
00000140  74 9a b6 39 a9 29 2f 51  f3 54 94 52 35 58 e2 fc  |t..9.)/Q.T.R5X..|
00000150  d0 79 a5 df 2f 17 36 7b  ab 7b 1e 7b 45 c5 97 aa  |.y../.6{.{.{E...|
00000160  63 8c 8e 26 00 44 e2 38  98 c7 c6 08 8c e7 1f 16  |c..&.D.8........|
00000170  79 45 e3 78 bc 77 dc a1  14 b2 04 68 b7 64 28 b9  |yE.x.w.....h.d(.|
00000180  20 07 4c 7c c3 82 41 17  38 c4 68 20 ce 76 b2 5b  | .L|..A.8.h .v.[|
00000190  8e 6b 8e 93 e8 5f 17 92  c0 e2 fb 20 63 f5 be d5  |.k..._..... c...|
000001a0  1b 27 7a e5 86 db 6d b4  c5 ec 14 ff c3 55 a6 65  |.'z...m......U.e|
000001b0  7c 58 8f 35 5d 3c 3b 27  35 23 1e 69 74 48 00 ef  ||X.5]<;'5#.itH..|
000001c0  ff ff 82 ef ff ff 02 00  00 00 00 38 77 00 00 ef  |...........8w...|
000001d0  ff ff 05 ef ff ff 02 38  77 00 00 e0 9b 03 00 00  |.......8w.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Hedgehog1 on 2011-04-01
What I believe you are seeing is an error in the new grub that keeps it from displaying the menu of OS choices, but then the count down finishes and it automatically boots the first OS in the list (which is natty).

I think you have installed grub correctly based on the script results.

Please run all updates for natty using package manager, and then update grub again.  This way we can weed-out an older 'grub bug' (that sounds funny, *'grub bug'* :D )

***The Hedge***

:KS

p.s. Isn't running an 'under development' OS exciting?  Not for the faint of heart...

---

### Post by uRock on 2011-04-01
Moved to NNT&D

---

### Post by mdhollis on 2011-04-01
OK so I am all up to date with the same issue. You are correct though.  When my monitor is giving me the out of range message, I arrowed down 5 times then hit enter and I booted into windows.  For some reason grub is working but not displaying on my screen.

Linux stands for liberty.

---

### Post by mdhollis on 2011-04-01
If anyone cares I was told to uncomment #GRUB_GFXMODE=640x480 in /etc/default/grub and it resolved my issue.

---

### Post by Hedgehog1 on 2011-04-02
> **mdhollis said:**
> If anyone cares I was told to uncomment #GRUB_GFXMODE=640x480 in /etc/default/grub and it resolved my issue.

**Thanks for sharing the solution!**  This helps for the next person who asks (now that I know too, hopefully I will remember next time!)  :D



***The Hedge***

:KS

---

