---
title: "C-Drive missing in Grub and in Ubuntu"
date: 2011-02-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by suryateja.sun on 2011-02-10
Hai,

I installed Natty 2 days back in my lappy. (Lenovo Y500 160GB, 1.73GHz). Earlier I have maverick installed. At that time, through Grub I have access through C-drive where Windows Vista is installed. After install, Windows entry in grub is missing. In Natty, I tried to mount the C device which is NTFS, but I got the error.

suryateja@suryateja-Linux:~/Desktop$ sudo mount -t ntfs-3g /dev/sda1 /media/C
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
suryateja@suryateja:~/Desktop$ sudo mount -t ntfs-3g /dev/sda /media/C
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I checked the " fdisk -l " but the entry is there.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       17902   123314909+   f  W95 Ext'd (LBA)
/dev/sda3           17903       19457    12490537+  12  Compaq diagnostics
/dev/sda5            2551       15990   107954908+   7  HPFS/NTFS
/dev/sda6           15991       16051      489951   83  Linux
/dev/sda7           16052       17659    12914688    7  HPFS/NTFS
/dev/sda8           17660       17902     1951866   82  Linux swap / Solaris

I am saying about sda1.

Below is file of etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=fb016b71-5dfc-4128-a245-e16b215b6765    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda7 :
UUID=AE2096DD2096ABB9    /media/Extra    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda5 :
UUID=DE189A1B1899F2AF    /media/LENOVO    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda8 :
UUID=f0396b4b-7d1a-4324-b2e5-ffb19aee7a74    none    swap    sw    0    0


I even installed NTFS configuration, but it was not detected. I doubted C-Drive is formatted :( ? Can any one please help me to find C-Drive. Is there any other possibilities to retrieve it and also place it in the Grub loader.

Thanks.

---

### Post by Quackers on 2011-02-10
When booted into Natty alpha2 have you run ```
sudo update-grub
```in a terminal?

---

### Post by suryateja.sun on 2011-02-10
Yes. This were results.

suryateja@suryateja-Linux:/boot/grub$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-2-generic
Found initrd image: /boot/initrd.img-2.6.38-2-generic
Found linux image: /boot/vmlinuz-2.6.35-26-generic
Found initrd image: /boot/initrd.img-2.6.35-26-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Just now I checked /boot/grub/grub.cfg but there is no entry for Windows/sda1 (C-Drive).  I suppose C-drive is formatted???

---

### Post by Quackers on 2011-02-10
Not necessarily. How many primary partitions were in use before you installed Ubuntu - do you know?
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by suryateja.sun on 2011-02-10
The resuls.txt file 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Bem.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 269. But according to the info from fdisk, 
                       sda7 starts at sector 257859584.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,811   287,595,629   246,629,819   f W95 Ext d (LBA)
/dev/sda5          40,965,813   256,875,629   215,909,817   7 HPFS/NTFS
/dev/sda6         256,879,413   257,859,314       979,902  83 Linux
/dev/sda7         257,859,584   283,688,959    25,829,376   7 HPFS/NTFS
/dev/sda8         283,691,898   287,595,629     3,903,732  82 Linux swap / Solaris
/dev/sda3         287,595,630   312,576,704    24,981,075  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda3        fb016b71-5dfc-4128-a245-e16b215b6765   ext4                                     
/dev/sda5        DE189A1B1899F2AF                       ntfs       LENOVO                        
/dev/sda6        803ac286-e1e6-4557-8d4b-5b7dd796ee5c   ext3                                     
/dev/sda7        AE2096DD2096ABB9                       ntfs       Extra                         
/dev/sda8        f0396b4b-7d1a-4324-b2e5-ffb19aee7a74   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/Extra             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/LENOVO            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


============================= sda6/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=01e065e4-eff7-4499-88dc-a4a404909ca1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,7)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=01e065e4-eff7-4499-88dc-a4a404909ca1 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic.bak
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=01e065e4-eff7-4499-88dc-a4a404909ca1 ro single
initrd        /boot/initrd.img-2.6.22-14-generic.bak

title        Ubuntu 7.10, memtest86+
root        (hd0,6)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sda6: Location of files loaded by Grub: ===================


 131.6GB: grub/menu.lst
 131.6GB: grub/stage2
 131.5GB: initrd.img-2.6.22-14-generic.dpkg-bak
 131.5GB: vmlinuz-2.6.22-14-generic

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.38-2-generic ...'
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-2-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.35-26-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.35-26-generic ...'
    linux    /boot/vmlinuz-2.6.35-26-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fb016b71-5dfc-4128-a245-e16b215b6765 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root fb016b71-5dfc-4128-a245-e16b215b6765
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=fb016b71-5dfc-4128-a245-e16b215b6765    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda7 :
UUID=AE2096DD2096ABB9    /media/Extra    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda5 :
UUID=DE189A1B1899F2AF    /media/LENOVO    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda8 :
UUID=f0396b4b-7d1a-4324-b2e5-ffb19aee7a74    none    swap    sw    0    0



=================== sda3: Location of files loaded by Grub: ===================


 155.9GB: boot/grub/core.img
 150.1GB: boot/grub/grub.cfg
 149.2GB: boot/initrd.img-2.6.35-22-generic
 149.4GB: boot/initrd.img-2.6.35-23-generic
 153.3GB: boot/initrd.img-2.6.35-24-generic
 155.3GB: boot/initrd.img-2.6.35-25-generic
 155.9GB: boot/initrd.img-2.6.35-26-generic
 159.1GB: boot/initrd.img-2.6.38-2-generic
 156.1GB: boot/vmlinuz-2.6.35-22-generic
 156.3GB: boot/vmlinuz-2.6.35-23-generic
 156.2GB: boot/vmlinuz-2.6.35-24-generic
 156.5GB: boot/vmlinuz-2.6.35-25-generic
 156.5GB: boot/vmlinuz-2.6.35-26-generic
 157.2GB: boot/vmlinuz-2.6.38-2-generic
 159.1GB: initrd.img
 155.9GB: initrd.img.old
 157.2GB: vmlinuz
 156.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  cc ff ff e0 d1 1e 43 d5  26 7b 3a 7c a6 b0 e2 1a  |......C.&{:|....|
00000010  2a 8d 0a 66 af 8b 8a bb  ab b3 63 34 c3 a0 50 ca  |*..f......c4..P.|
00000020  8f 6f 01 70 fd c9 ad a9  49 0d b7 a2 df 81 de df  |.o.p....I.......|
00000030  41 6d 5f 1c 65 96 da f5  8a 0f c1 11 21 b5 ae 43  |Am_.e.......!..C|
00000040  9f 32 9b ee ca c0 ce 99  31 3c 8f 11 e2 90 32 e9  |.2......1<....2.|
00000050  76 6a d9 94 50 d3 e2 27  93 39 17 8f a1 dc 85 8d  |vj..P..'.9......|
00000060  46 bc 45 e7 d7 61 01 52  ec 8a c4 2e 6d 00 d6 06  |F.E..a.R....m...|
00000070  91 53 36 6e b8 ca 4a 33  af 58 39 8c dc 58 49 b0  |.S6n..J3.X9..XI.|
00000080  6d 70 5c 3a 95 ae 71 8a  9c 02 3e 46 99 98 b4 55  |mp\:..q...>F...U|
00000090  39 b0 6c df 05 3f 30 4e  1b 77 a6 d7 fc b3 b0 47  |9.l..?0N.w.....G|
000000a0  3a c7 73 bb 7d fd f6 b2  37 71 c0 cd 69 49 fe 3b  |:.s.}...7q..iI.;|
000000b0  3e d8 31 cb 97 35 fd 46  73 27 1c 1c d9 42 e7 60  |>.1..5.Fs'...B.`|
000000c0  1e c3 d6 a2 a5 45 ac 2e  6e 45 d8 79 32 a3 b6 b5  |.....E..nE.y2...|
000000d0  67 38 bb d8 a6 76 af 5b  8d 1b ce c0 68 32 63 82  |g8...v.[....h2c.|
000000e0  0c df 58 e8 c7 41 c0 2c  fd b8 30 bd 7d b9 d7 43  |..X..A.,..0.}..C|
000000f0  fa 3e 95 bf 71 ec 2f ea  b4 34 c9 47 0a e2 12 99  |.>..q./..4.G....|
00000100  3c e6 99 53 24 5d 8d e6  68 f5 0b 24 45 ea 61 3e  |<..S$]..h..$E.a>|
00000110  9e db fe af b0 9c 16 d6  09 ae 0c 2d ed 1c d3 76  |...........-...v|
00000120  2b 31 d0 48 0f 64 71 78  21 ca 03 97 d2 bf 9a e8  |+1.H.dqx!.......|
00000130  3d af f1 f7 bd eb 3b f6  26 10 ce 77 67 6c 3d 17  |=.....;.&..wgl=.|
00000140  fb f5 df d6 8b f4 4e b0  1b 20 e2 cc c7 e7 00 7c  |......N.. .....||
00000150  44 47 d6 22 56 ab 34 1a  c0 9f 2c d6 ef a2 4d 8f  |DG."V.4...,...M.|
00000160  fb e7 d3 2e 38 0f 00 fb  50 d6 4e 23 43 2e 09 df  |....8...P.N#C...|
00000170  4f 26 95 79 44 71 2a 6e  41 89 99 2b 89 f2 db 9a  |O&.yDq*nA..+....|
00000180  3f d1 20 e5 f7 6e a7 ee  e3 b2 c5 81 38 24 bd cc  |?. ..n......8$..|
00000190  94 8b 6e a8 ce cc ca e6  77 ed 1b 68 31 b0 99 fc  |..n.....w..h1...|
000001a0  ca 52 dd c9 42 37 85 f9  fc 03 cb bd 9b b6 97 b8  |.R..B7..........|
000001b0  d8 2b 3f 8f ca d3 29 41  04 86 f5 04 f1 c4 de ba  |.+?...)A........|
000001c0  94 74 c5 ae 4a 37 1e 3b  24 30 b0 a8 7a 9c a0 09  |.t..J7.;$0..z...|
000001d0  dd ec 02 f5 ef 71 82 47  94 37 b5 1c 59 0f 43 6d  |.....q.G.7..Y.Cm|
000001e0  df a6 40 6d 36 1d d4 1d  b3 a5 c8 2f 34 93 15 b9  |..@m6....../4...|
000001f0  89 f3 b3 bd 05 ac c4 a5  b0 57 15 f1 5c 29 42 03  |.........W..\)B.|
00000200


```

---

### Post by Quackers on 2011-02-10
Thanks.
When booted into Natty alpha2, please go to System > Admin >synaptic package manager and in the search box enter os-prober.
When it appears in the main window, is there a green box to its left (in other words, is it installed)?
If not install it (right-click and select "mark for installation", then click on the green tick mark in the toolbar, to apply the change). Then run sudo update-grub again please.

Edit: actually I don't think that will help in your circumstances. You have 4 Windows type partitions but the boot script seems unable to see anything in them. sda5 and sda7 are logical partitions (they seem to be your main Windows partitions). This is not usually the case. They also don't report the presence of a Windows operating system, which is not good!
Do you have a Windows repair cd?

---

### Post by suryateja.sun on 2011-02-10
Dear Quackers,

It was installed. By observing the above code, I think Drive is available.

```
### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title        Other operating systems: root   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1 title        Windows Vista/Longhorn (loader) root        (hd0,0) savedefault makeactive chainloader    +1
```

Please check it. Thanks for your replies. Can I add this to Grub loader?

---

### Post by jfernyhough on 2011-02-10
(As a last resort I'd suggest trying booting from the Windows CD/DVD and asking it to repair startup problems. This will likely overwrite GRUB too, but that's easy enough to get back with an Ubuntu LiveCD.)

---

### Post by Quackers on 2011-02-10
Please see my edit to post #6

---

### Post by kansasnoob on 2011-02-10
Look at oldfred's instructions on running chkdsk here:

[http://ubuntuforums.org/showpost.php?p=10424362&postcount=17](http://ubuntuforums.org/showpost.php?p=10424362&postcount=17)

---

### Post by suryateja.sun on 2011-02-10
Dear Quackers and Jferny, My CD drive is not working :(

Quackers:

Yes these partitions were my general partitions before installation of windows. Please see the above code for /dev/sda1.

Thanks.

---

### Post by Quackers on 2011-02-10
That code is probably only referring to Windows first 2 boot files, not the system.
Do you have a Windows Vista repair cd or installation disc?

---

### Post by suryateja.sun on 2011-02-10
Dear Quackers,

My CD-Drive is not working even though I have CD. 

Thanks.

My problem 2:

How to mount C-Drive on sda1.

---

### Post by dino99 on 2011-02-10
sudo dpkg-reconfigure autofs5
sudo dpkg-reconfigure mountall

---

### Post by Quackers on 2011-02-10
I suspect there may be a problem with the file system on the Windows partitions. Mounting sda1 will not mount Windows (and in any case, sda1 is unmountable, according to the script output).
It would be an option to run a chkdsk via the Windows cd, but without a working cd drive it is going to be difficult to solve your problems, unless you can make a Windows repair usb flash drive. I believe it has been done, but have not done it myself.
There may be one method below
[http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/](http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/)

See one post up also :-)

---

### Post by suryateja.sun on 2011-02-10
Dino99:

I tried it. But Windows is not shown.

Quackers:

I will try it out using USB drive. 

Thanks for your suggestions.

Apart from the above problems, I got the another ones.

1. Indicator Applet Appmenu is not working, I hope this bug has sent.
2. Gnome bar on top is missing.
3. I am getting several error reports like compiz etc. failed to load. How to disable the reports?
4. The list is empty when I click top left ubuntu icon. 

Please also help in this regard.

Thanks

---

### Post by ELD on 2011-02-10
It is a problem with GRUB, i had the exact same issue.

The only way i found to fix it is to run the boot repair from the windows dvd.

I have windows 7 though, it doesn't overwrite grub but it allows grub to pick up the partition again.

It's an odd bug but i was told it wasn't a bug and that grub won't pick up a badly shut down windows but it happens when natty updates grub too so it's definitely a bug?

[http://ubuntuforums.org/showthread.php?t=1677365](http://ubuntuforums.org/showthread.php?t=1677365) - my original post on it

---

### Post by dino99 on 2011-02-10
> **ELD said:**
> It is a problem with GRUB, i had the exact same issue.

 so it's definitely a bug



yes need to be reported asap

---

### Post by ELD on 2011-02-10
Not exactly sure where to, clicking report a bug on launchpad now goes to that wiki page.

If someone else could make the bug i can comment with all my info.

---

### Post by mc4man on 2011-02-10
> Not exactly sure where to, clicking report a bug on launchpad now goes to that wiki page.


Better to do from terminal - ubuntu-bug <package name>
```
ubuntu-bug grub-pc
```

---

### Post by kaffelars on 2011-03-03
Was this submitted, and to what bug?
I had the same issue with the ISO from March 2. 

I managed to fix it in 2 steps though:

1. Boot a Windows 7 install disc or Repair disk, and choose repair startup.
2. Boot Ubuntu, and THEN run the "update-grub"-command.
3. Now, Windows Loader is added to the boot menu.

---

### Post by cariboo on 2011-03-03
This has been a known problem almost from day one of testing. Grub-pc just doesn't like files systems that aren't shut down properly, be ext2/3/4 et al or NTFS.

---

### Post by dino99 on 2011-03-03
about ext3/ext4 partitions: the latest portmap package has fixed the shutdown issues ( 6.0.0-2ubuntu4)

---

### Post by billbear on 2011-03-10
In short, to solve [this problem]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html"), recent update of grub introduces [this new bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225") which can corrupt the first ntfs partition.

---

### Post by suryateja.sun on 2011-03-10
Billibear,

I tried out commands given in that link. These are my results.

```

suryateja@suryateja-Linux:~$ sudo fdisk -lu /dev/sda1

Disk /dev/sda1: 21.0 GB, 20974431744 bytes
255 heads, 63 sectors/track, 2549 cylinders, total 40965687 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04f58604

Disk /dev/sda1 doesn't contain a valid partition table


```

I downloaded flexnet signature and placed it in /home/suryateja folder and ran the command.

```

suryateja@suryateja-Linux:~$ sudo dd if=flexnet.sector32 of=/dev/sdc seek=32
1+0 records in
1+0 records out
512 bytes (512 B) copied, 6.8165e-05 s, 7.5 MB/s

```

And after running grub-install, I encountered following error

```

suryateja@suryateja-Linux:~$ sudo grub-install /dev/sda1 --root-directory=/media/C
/usr/sbin/grub-setup: error: unable to identify a filesystem in /dev/sda; safety check can't be performed.

```

Please look into it.

Thanks

---

### Post by billbear on 2011-03-10
suryateja,
The commands given in the bug link is an example to ruin your partitions.
Don't follow those commands if you are trying to recover partitions.

By the way, it doesn't make sense to run "sudo fdisk -lu /dev/sda1" instead of "sudo fdisk -lu /dev/sda".

And if you are trying to see how the bug ruins your data, replace sdc in "sudo dd if=flexnet.sector32 of=/dev/sdc seek=32" with your device name.

And it's dangerous to run "sudo grub-install /dev/sda1 --root-directory=/media/C" (command from my bug report is "sudo grub-install /dev/sdc --root-directory=/mnt" which installs grub to the mbr, not to a ntfs partition), it could ruin your sda1 once more, fortunately /media/C does not contain a valid linux file system and the command will not execute.

Don't follow the commands there if you don't understand them. They are very dangerous commands to ruin your partition.

---

