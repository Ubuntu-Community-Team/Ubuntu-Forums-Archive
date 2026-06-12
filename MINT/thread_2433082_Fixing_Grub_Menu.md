---
title: "Fixing Grub Menu"
date: 2019-12-13
forum: MINT
---

### Post by lxiscs on 2019-12-13
I have a dual boot system with Ubuntu 18.04 and Windows 10. I need to cleanup my grub menu as it doesn't list my current Windows 10 install. Both Windows and Ubuntu are on separate partitions on an SSD (NVME), every other drive should just be used for storage. Running OS prober only finds invalid windows 10 installs on other drives and an unused linux mint install. I ran a boot info script to provide more context.  Output is pasted below. I'm looking for advice on the best way to clean up the system and get the grub menu updated.

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 18.1 Serena
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdd1 has 
                       2353000447 sectors, but according to the info from 
                       fdisk, it has 6647967743 sectors.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sde1 has 
                       2353000447 sectors, but according to the info from 
                       fdisk, it has 6647967743 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,126,399     1,124,352   7 NTFS / exFAT / HPFS
/dev/sda2           1,126,400   250,066,943   248,940,544   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,465,145,343 1,465,143,296   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,269,280,840 1,269,278,793   7 NTFS / exFAT / HPFS
/dev/sdc2       1,269,282,814 1,465,147,391   195,864,578   5 Extended
/dev/sdc5       1,269,282,816 1,452,582,911   183,300,096  83 Linux
/dev/sdc6       1,452,584,960 1,465,147,391    12,562,432  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 9.1 TiB, 10000831348736 bytes, 19532873728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048 6,647,969,791 6,647,967,744 Data partition (Windows/Linux)

Drive: sde _____________________________________________________________________
Disk /dev/sde: 9.1 TiB, 10000831348736 bytes, 19532873728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sde1           2,048 6,647,969,791 6,647,967,744 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop15                                             squashfs   
/dev/loop16                                             squashfs   
/dev/loop17                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1                                                     
/dev/nvme0n1p2   D708-6216                              vfat       
/dev/nvme0n1p3   02A6FF6EA6FF6099                       ntfs       
/dev/nvme0n1p4   3E08464C084602FF                       ntfs       
/dev/nvme0n1p5                                                     
/dev/nvme0n1p6   828c123e-7784-414f-88c7-0a44dff03723   ext4       
/dev/sda1        3CB4F24BB4F206E4                       ntfs       System Reserved
/dev/sda2        02A6FF6EA6FF6099                       ntfs       
/dev/sdb1        1ECA2DEACA2DBF41                       ntfs       HDD1
/dev/sdc1        DC3EE89A3EE86EC8                       ntfs       HDD2
/dev/sdc5        94dc703c-516b-4737-a4e8-2da4e04583fb   ext4       
/dev/sdc6        6ebdeff4-6531-4ff5-afcb-41bb50c2925d   swap       
/dev/sdd1        3470E36D70E333F0                       ntfs       easystore
/dev/sde1        A0DED9EEDED9BCAA                       ntfs       easystore

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/nvme0n1p2   /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p6   /                        ext4       (rw,relatime,errors=remount-ro)


=========================== sdc5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
else
  search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###

function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode



### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 10 (loader) (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-chain-1ECA2DEACA2DBF41' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1ECA2DEACA2DBF41
    else
      search --no-floppy --fs-uuid --set=root 1ECA2DEACA2DBF41
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/31_linux_proxy ###
menuentry "Linux Mint 18.1 Cinnamon 64-bit" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-94dc703c-516b-4737-a4e8-2da4e04583fb' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
    else
      search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
    fi
    linux    /boot/vmlinuz-4.4.0-59-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-59-generic
}
submenu "Advanced options for Linux Mint 18.1 Cinnamon 64-bit"{
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-59-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-59-generic-advanced-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-59-generic ...'
        linux    /boot/vmlinuz-4.4.0-59-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-59-generic
}
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-59-generic (upstart)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-59-generic-init-upstart-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-59-generic ...'
        linux    /boot/vmlinuz-4.4.0-59-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-59-generic
}
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-59-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-59-generic-recovery-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-59-generic ...'
        linux    /boot/vmlinuz-4.4.0-59-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-59-generic
}
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-53-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-advanced-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
}
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-53-generic (upstart)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-init-upstart-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
}
menuentry "Linux Mint 18.1 Cinnamon 64-bit, with Linux 4.4.0-53-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-recovery-94dc703c-516b-4737-a4e8-2da4e04583fb' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
        else
          search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic root=UUID=94dc703c-516b-4737-a4e8-2da4e04583fb ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
}
}
### END /etc/grub.d/31_linux_proxy ###

### BEGIN /etc/grub.d/32_lupin ###
### END /etc/grub.d/32_lupin ###

### BEGIN /etc/grub.d/33_linux_xen ###

### END /etc/grub.d/33_linux_xen ###

### BEGIN /etc/grub.d/34_memtest86+_proxy ###



### END /etc/grub.d/34_memtest86+_proxy ###

### BEGIN /etc/grub.d/35_os-prober_proxy ###



set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/35_os-prober_proxy ###

### BEGIN /etc/grub.d/36_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
    else
      search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  94dc703c-516b-4737-a4e8-2da4e04583fb
    else
      search --no-floppy --fs-uuid --set=root 94dc703c-516b-4737-a4e8-2da4e04583fb
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/36_memtest86+_proxy ###

### BEGIN /etc/grub.d/37_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os $menuentry_id_option 'osprober-chain-C2666C1F666C1687' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  C2666C1F666C1687
    else
      search --no-floppy --fs-uuid --set=root C2666C1F666C1687
    fi
    parttool ${root} hidden-
    chainloader +1
}
### END /etc/grub.d/37_os-prober_proxy ###

### BEGIN /etc/grub.d/38_uefi-firmware ###
### END /etc/grub.d/38_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=94dc703c-516b-4737-a4e8-2da4e04583fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6ebdeff4-6531-4ff5-afcb-41bb50c2925d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-eoNdYM0U/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2019-12-13
Please use code tags for any copied code that is more than a couple of lines.
And with Boot-Repair's report which uses the bootinfoscript as part of the report, it will automatically create a paste-bin link that is easier to post.

Moved to Mint sub-forum since not Ubuntu.

Also bootinfoscript has not yet been updated to include NVMe devices.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)
But another user baedacool posted (3rd one) a copy with the edits needed to show NVMe devices. 
Could you run that and see if it works? I have run it, but do not have NVMe device.

Is Windows on NVMe device and gpt partitioned? It shows FAT32 partition which is usually used for UEFI boot. But your sda, sdb & sdc drives are the old MBR(msdos) partitioned  and Ubuntu is installed in BIOS boot mode.

With UEFI you cannot change boot mode  once you start booting. Or grub can only dual boot other installs in the same boot mode.
Windows requires gpt partitioning with UEFI boot and MBR for BIOS boot. Ubuntu will let you install in UEFI boot mode to MBR drive, but probably should not.

If Windows is UEFI/gpt, better to convert all drives to gpt. Normal repartitioning is destructive, but there are tools to convert that should preserve data, but good backups still required. I started changing drives to gpt in 2010 before UEFI became common on my old BIOS system.

I have not actually used this, as I converted all old drives as I built new systems or only made new drives since 2010 with gpt including my larger flash drives.
       Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    
If you want to boot old BIOS/MBR Windows install, it must remain as MBR and could only be booted from UEFI boot menu. You may have to change UEFI setting to use CSM/Legacy/BIOS mode.

I also believe in having at least a small functional install on every drive. So first two partitions used to be both the bios_grub (for BIOS boot) and ESP for UEFI boot. They must be in first 2TiB of a drive, so I always suggest they be first & then out of the way. Then I add 25GB for a / (root) partition. 

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

---

