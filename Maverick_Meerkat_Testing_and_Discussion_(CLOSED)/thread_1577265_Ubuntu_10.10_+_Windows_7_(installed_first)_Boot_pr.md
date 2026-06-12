---
title: "Ubuntu 10.10 + Windows 7 (installed first) Boot problem"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sputinyk on 2010-09-18
First, I'm Brazilian, pardon my english.
I installed Ubuntu 10.10 through  Live CD beside Windows 7, through option "install along other operating system" present on installer.
But when I restarted my PC from installation nothing appear on inicialization just a message from motherboard saying that was nothing to boot up. So, doesn't appear any grub screen option or nothing.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total de 1953525168 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total de 625142448 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   526,887,120   526,680,273   7 HPFS/NTFS
/dev/sdb3         526,888,958   625,141,759    98,252,802   5 Extended
/dev/sdb5    *    526,888,960   621,029,375    94,140,416  83 Linux
/dev/sdb6         621,031,424   625,141,759     4,110,336  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CA60DC3F60DC33C3                       ntfs       Depósito                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14041E0C041DF18A                       ntfs       Reservado pelo Sistema        
/dev/sdb2        C214ECCB14ECC38F                       ntfs       Win7                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab   ext4                                     
/dev/sdb6        6a9e055b-22d1-4989-b7da-a15c97ca9df7   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /mnt                     ext4       (rw)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
set locale_dir=($root)/boot/grub/locale
set lang=pt
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 14041e0c041df18a
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=2412b9f6-88ed-4121-a0a3-5d7fc5b8e5ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6a9e055b-22d1-4989-b7da-a15c97ca9df7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 278.5GB: boot/grub/grub.cfg
 270.8GB: boot/initrd.img-2.6.35-22-generic
 306.4GB: boot/vmlinuz-2.6.35-22-generic
 270.8GB: initrd.img
 306.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  95 4c 90 e9 0a b3 5b 3d  95 f3 36 31 2e 9b 5b a0  |.L....[=..61..[.|
00000010  f3 cd 1e b4 80 52 84 96  4a 83 ef 57 ce 48 65 82  |.....R..J..W.He.|
00000020  14 3e 6a 01 f8 cb 01 67  43 41 02 59 b6 ec b4 92  |.>j....gCA.Y....|
00000030  eb ea 77 95 3b 63 3b d4  08 aa d7 d5 8d 1a ff fb  |..w.;c;.........|
00000040  b2 6c 36 80 05 43 68 dc  6b 0f 4b 70 41 44 3b 9f  |.l6..Ch.k.KpAD;.|
00000050  61 85 32 16 49 9d 6b 8c  3d 2d c0 df 90 ed f1 96  |a.2.I.k.=-......|
00000060  20 c8 5c e9 27 dc b6 29  fe a7 3a d6 43 11 cd a9  | .\.'..)..:.C...|
00000070  d2 cf f6 a4 5e a2 b2 d4  8f 4e 5e 5d 10 d2 cc 23  |....^....N^]...#|
00000080  42 f4 5c bc 65 16 c4 4a  a1 0a 9e 35 02 23 31 31  |B.\.e..J...5.#11|
00000090  15 80 08 84 f2 28 42 6c  4d 12 48 dd fd d0 88 a6  |.....(BlM.H.....|
000000a0  40 22 62 92 88 21 0a 8f  1e f8 0e 7d 21 7d e9 5a  |@"b..!.....}!}.Z|
000000b0  93 1c 69 c6 45 d1 09 8a  82 c6 15 8b 84 8e 82 8a  |..i.E...........|
000000c0  52 90 f9 c8 89 30 51 14  f2 8f 5a df 13 11 fc a4  |R....0Q...Z.....|
000000d0  c7 6c 96 ff ff ff ff d7  fb 9e a7 b9 5f ff 4c 6d  |.l.........._.Lm|
000000e0  b6 13 4b aa bb 8a 80 03  28 20 6b 5e c2 97 26 93  |..K.....( k^..&.|
000000f0  79 29 8d 4e 33 ac 5e bf  89 3a e1 5f 2c 5b 36 b7  |y).N3.^..:._,[6.|
00000100  44 56 48 9f 9b ab 6f 16  33 f4 92 f3 cf 0c 72 9e  |DVH...o.3.....r.|
00000110  59 92 3b 11 aa d7 3c 77  51 69 89 99 bc 2c c6 ad  |Y.;...<wQi...,..|
00000120  db d1 70 b4 64 36 6d ef  14 36 55 2a 14 b7 18 c1  |..p.d6m..6U*....|
00000130  18 4d b3 11 4b 84 d3 46  a2 ad 82 c1 cb b9 a4 8f  |.M..K..F........|
00000140  17 da 8f 91 6f 15 d1 9d  3f 1d 67 c8 b8 bc 77 7a  |....o...?.g...wz|
00000150  8b a1 61 75 71 29 ba 6f  f7 5d 5c 08 17 06 e7 26  |..auq).o.]\....&|
00000160  52 09 bd b1 03 58 da 44  a6 0d 35 34 99 49 da f0  |R....X.D..54.I..|
00000170  ac 7b f5 02 3c 7f d3 6a  79 b2 d4 23 30 59 a2 23  |.{..<..jy..#0Y.#|
00000180  8c 25 ce 9f f3 d4 f2 44  e2 a2 b1 76 d6 f5 3f 6f  |.%.....D...v..?o|
00000190  d7 65 fa 05 1b ae 40 0c  41 c9 83 c2 89 85 06 98  |.e....@.A.......|
000001a0  18 b5 6a 84 d7 3f 06 1d  a9 74 68 26 28 0a cf 0e  |..j..?...th&(...|
000001b0  1e b6 51 b4 d1 57 e3 3c  f0 e8 44 61 d9 21 80 86  |..Q..W.<..Da.!..|
000001c0  ce ff 83 86 ce ff 02 00  00 00 00 78 9c 05 00 86  |...........x....|
000001d0  ce ff 05 86 ce ff 9a 7f  9c 05 68 b8 3e 00 00 00  |..........h.>...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I'm posting from Live CD

---

### Post by uRock on 2010-09-18
Moved to Maverick Meerkat Testing and Discussion.

---

### Post by plun on 2010-09-18
Can you please file a bug about this..... ?

Bug howto
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


Its just ridicoulus that users falls in this trap...!   Lucid is occupied with this tragic Grub2 debacle....

More help is for sure coming about solving your problem !

---

### Post by sputinyk on 2010-09-18
So, I reinstalled GRUB according to the tutorials present in ubuntu.com site and solved my problems. Thanks.

---

### Post by wilee-nilee on 2010-09-18
> **plun said:**
> Can you please file a bug about this..... ?

Bug howto
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


Its just ridicoulus that users falls in this trap...!   Lucid is occupied with this tragic Grub2 debacle....

More help is for sure coming about solving your problem !

There was no bug here, that is a bias.

---

### Post by Anadon on 2010-09-18
I had an identical problem, but reinstalling GRUB didn't fix it.  That's weird.

---

### Post by cariboo on 2010-09-18
How did you re-install grub? The best method I've found is with the Live CD:

[list=1]
[*] boot to the desktop
[*] mount your linux partition sudo mount /dev/sdaX /mnt, where sdaX is you linux partition
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo mount -o bind /sys /mnt/sys
[*] sudo mount -o bind /proc /mnt/proc
[*] sudo chroot /mnt
[*] sudo grub-install /dev/sda
[*] sudo update-grub
[/list]

Then reboot.

---

### Post by plun on 2010-09-18
A bug MUST be filed..... IMHO.... just ridiculus that a installer fails with Grub and a dual-boot !

---

### Post by wilee-nilee on 2010-09-18
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: 

> **plun said:**
> A bug MUST be filed..... IMHO.... just ridiculus that a installer fails with Grub and a dual-boot !

I agree to some extent as far as bugs that are bugs should be filed. But in a situation where somebody is dual booting and as the script showed the sda was first in line for boot when it should have bee sdb it is hard to see a bug here. They fixed it, but the HD were in the wrong order to boot. The script shows the boot order, I believe somebody correct me if I'm wrong. 

Grub was not installed by the user in the correct mbr to begin with, and the boot order was wrong. The mbr in sda is looking for a partition that doesn't exist in that HD.

---

### Post by plun on 2010-09-18
> **wilee-nilee said:**
> 

I agree to some extent as far as bugs that are bugs should be filed. But in a situation where somebody is dual booting and as the script showed the sda was first in line for boot when it should have bee sdb it is hard to see a bug here. They fixed it, but the HD were in the wrong order to boot. The script shows the boot order, I believe somebody correct me if I'm wrong. 

Grub was not installed by the user in the correct mbr to begin with, and the boot order was wrong. The mbr in sda is looking for a partition that doesn't exist in that HD.

Well... Mr Watson must fix this because this "Russian roulette" with Grub2 and dual-boot badly hurts Ubuntu.

KansasNoob has done a great job with this and reporting/commenting bugs but it seems to need more developer work....  just sad when a total newbie fails with a dual-boot !!!  Disaster IMHO.....

---

### Post by VMC on 2010-09-18
> **wilee-nilee said:**
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

...

I'm a little confused myself. It looks like the OP has two installs of Vista, sda and sdb. The grub.cfg file came from sdb. Where is sda #5? Was that an external drive?

---

### Post by wilee-nilee on 2010-09-18
@plun
There are problems with all bootloaders. I agree with the comment that kansasnoob and several others have made a great efforts to get things corrected, I bow to these people for all my knowledge, which ain't much.;) I agree I would like to see even the neophyte have no problems.

@VMC
It looks like two vista's in the partition names but there is only one MS boot setup and it is on sdb as well. sdb1 is the vista boot and sdb2 is the vista os.

Really I'm not surprised that there were problems here there is a boot flag on sda and it is first to be read, and has grub in its mbr=problems

---

