---
title: "Grub error"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Pablo Pablovski on 2010-10-02
Ok, so I've upgraded to 10.10RC. While the upgrade was running, I was promoted with a "do you want to keep or replace your custom config file" message about GRUB. Can't remember the exact wording - it was about the use of UUID - but I elected to keep the old file from 10.04, which I'd customised with my video resolution and reduced timeout.

Now, when I boot 10.10, an error message is produced when GRUB runs. It disappears too quickly to read it, but it's something about a module. GRUB runs, but it's like it's a default version - 640*480, no auto timer, so I need to press enter to auto-load, though 10.10 boots properly when I do that.

ubuntu is installed on sda1. I also have Windows XP on the system (on sdb1) - it boots ok from GRUB.

Output from bootscript, below - it looks ok to me, but I'm no expert:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    43,584,344    43,584,282  83 Linux
/dev/sda2    *    388,612,350   390,716,864     2,104,515  82 Linux swap / Solaris
/dev/sda3          43,584,345   388,612,349   345,028,005  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   179,976,194   179,976,132   7 HPFS/NTFS
/dev/sdb2         179,976,195   390,716,864   210,740,670  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   634,904,864   634,904,802  83 Linux
/dev/sdd2         634,904,865   976,768,064   341,863,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d   ext3       lucid                         
/dev/sda2        2d98637d-39cd-4df6-910a-5cb672af2fc0   swap                                     
/dev/sda3        6bfbd14c-df28-4d99-a0b2-12b39cb4ec8f   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8EC0F32EC0F31B63                       ntfs       Windows                       
/dev/sdb2        16c6d26e-727b-467b-a505-bd82127b8308   ext3       VirtualBox                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3A363D2E60801A87                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        25914567-8bcc-4f8d-bdcc-2ac6d3107e22   ext3       Music2                        
/dev/sdd2        7a49934c-ac72-4129-bf08-052597117d99   ext3       Media2                        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /mnt/Windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /mnt/VirtualBox          ext3       (rw,nosuid,nodev,relatime,commit=0)
/dev/sdc1        /mnt/Archive             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /mnt/Music2              ext3       (rw,nosuid,nodev,relatime,commit=0)
/dev/sda3        /mnt/karmic              ext4       (rw,nosuid,nodev,relatime,commit=0)
/dev/sdd2        /mnt/Media2              ext3       (rw,nosuid,nodev,relatime,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1680x1050
  set gfxpayload=keep
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    linux    /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8ec0f32ec0f31b63
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bd4edbb1-6758-47c1-bc3e-9e7c2956ca1d /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=2d98637d-39cd-4df6-910a-5cb672af2fc0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdb1 /mnt/Windows    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/sdb2 /mnt/VirtualBox ext3 nouser,atime,auto,rw,nodev,exec,nosuid,relatime 0 0
/dev/sdc1 /mnt/Archive    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/sdd1 /mnt/Music2 ext3 nouser,atime,auto,rw,nodev,exec,nosuid,relatime 0 0
/dev/sda3 /mnt/karmic ext4 nouser,atime,rw,exec,nosuid,nodev,relatime 0 0
/dev/sdd2 /mnt/Media2 ext3 nouser,atime,auto,rw,nodev,exec,nosuid,relatime 0 0

=================== sda1: Location of files loaded by Grub: ===================


   7.0GB: boot/grub/core.img
   6.9GB: boot/grub/grub.cfg
   7.0GB: boot/initrd.img-2.6.32-25-generic
   7.1GB: boot/initrd.img-2.6.35-22-generic
   7.0GB: boot/vmlinuz-2.6.32-25-generic
   7.1GB: boot/vmlinuz-2.6.35-22-generic
   7.1GB: initrd.img
   7.0GB: initrd.img.old
   7.1GB: vmlinuz
   7.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

;timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 0f 33 f3 03 00 00  |.......|...3....|
000001b0  00 00 80 00 00 3a 0e 00  80 1f 81 1f f6 0e 80 01  |.....:..........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 c4 37 ba 0a 00 fe  |......?....7....|
000001d0  ff ff 83 fe ff ff 03 38  ba 0a be a5 8f 0c 00 00  |.......8........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdc

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 f2 0e 00  a1 95 a1 95 5c f7 80 01  |............\...|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 dd 49 17 00 00  |......?.....I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I've had a look through bootlog etc., but saw nothing that would indicate the nature of the fault.

So, any ideas as to what might be the problem? Can I run any diagnostics on GRUB? 

Thanks in advance.

PP

---

### Post by Pablo Pablovski on 2010-10-02
Sorry, should've mentioned - I've changed some other parameters in /etc/default.grub, then run "update-grub" to see if they "took" - they didn't. The same issue with GRUB booting to a default setup remained.

My feeling is there's something wrong in one of the config files that causes GRUB to run in a failsafe mode, but I've no way of knowing what that might be.

---

### Post by dino99 on 2010-10-02
previously , is grub1 was used ? As grub2 dont like menu.lst from grub legacy, you have to search and remove everything about grub & menu.lst (do it with nautilus "search")

then:
sudo grub-mkconfig
sudo update-grub

---

### Post by Pablo Pablovski on 2010-10-02
> **dino99 said:**
> previously , is grub1 was used ? As grub2 dont like menu.lst from grub legacy, you have to search and remove everything about grub & menu.lst (do it with nautilus "search")

then:
sudo grub-mkconfig
sudo update-grub

Thanks dino99.

No, this system was originally a clean install of Lucid that I've now updated to Maverick. So, it has never had GRUB1 (Legacy GRUB) on it.

I've tried the mkconfig, which completed without error. GRUB still runs like it's in default mode.

---

### Post by DougieFresh4U on 2010-10-02
When you ran updates you must have run into this drama:
[http://ubuntuforums.org/showthread.php?t=1583508]("http://ubuntuforums.org/showthread.php?t=1583508")
and this
[http://ubuntuforums.org/showthread.php?t=1584156]("http://ubuntuforums.org/showthread.php?t=1584156") :)

---

### Post by Pablo Pablovski on 2010-10-10
Thanks to all who contributed. I eventually fixed / avoided the problem by installing BURG, which I've been able to configure to my preferences (auto-boot of default OS, native video resolution etc.). Still don't know what went wrong with GRUB - I purged and re-installed several times, tried other stuff...

Anyway, BURG is great - themeable graphical replacement for GRUB, easy to install and use. So, thumbs up!

---

