---
title: "Graphics card possible problem"
date: 2011-02-09
forum: Multimedia Software
---

### Post by pages on 2011-02-09
Hi everyone ,
I just got a laptop here which came with WIn 7 pre installed but i've been using Ubuntu for a few months and much prefer the OS. So when i opened the laptop near first thing i did was put in the Ubuntu 32bit (just hate some program compatibility problems with my other 64bit Ubuntu and don't want the hassle)

Anyway like a good little boy i when straight update manager and downloaded all the updates for 10.10 and of course it needed a restart but i also thought i'd kill two birds with 1 restart and get the device drivers for the video card i have since i know that also requires a restart.

So i then restarted the laptop and when Ubuntu loaded it would only appear as a command line interface , so i restarted and used the recovery mode and selected to run ubuntu with the default graphics or some option similar ( sorry i cant remember which step i chose exactly ).
 
Now i've stabilised the problem as it were so i now get a normal GUI but i can only have the basic choice of graphics from the appearance. I know this isn't really critical since i can use the laptop but i hate to feel as it's not running at full graphical power especially as i will be using Animation programs such as blender and would like to see the best results .


I've put in the boot script info but pretty sure that wont highlight the error :(
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    45,062,324    45,062,262  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     45,062,328   289,255,607   244,193,280   7 HPFS/NTFS
/dev/sda3         289,257,472   976,771,071   687,513,600   f W95 Ext d (LBA)
/dev/sda5         289,259,520   976,771,071   687,511,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       f9502e0b-0295-41ac-a721-fb7f5fa20bb6   ext4                                     
/dev/sda1        6834-6968                              vfat       RECOVERY                      
/dev/sda2        3C2C99F82C99AE00                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5A7A9C287A9BFEC7                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3c2c99f82c99ae00
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3c2c99f82c99ae00
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6834-6968
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3c2c99f82c99ae00
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

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


  15.2GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-25-generic-pae
   5.0GB: boot/vmlinuz-2.6.35-25-generic-pae
    .9GB: initrd.img
   5.0GB: vmlinuz

```


 but if you do know any way to get my graphics card working then i'd love to hear from you 
System :Asus U53JC 15.6/i5-430M/4GB/500GB/WIN 7


Thanks for your time,
Pages

---

### Post by BicyclerBoy on 2011-02-09
This is an optimus beast is it not ?

IMO it is a really bad idea to update video driver with everything else. If the update includes kernel updates you can be stuck in console login..
It also makes it hard to read all the install/update std out.

The optimus features are not supported in nvidia linux driver.
I think some laptops can be used in a normal 1 fixed GPU only mode..this could be a BIOS setting ??
I think you end up with an intel i GPU only & the power drain from a non-functional nvidia GPU.

This could end up being windows only hardware..caveat emptor
Not very helpful..sorry.

---

### Post by pages on 2011-02-10
Yeah shouldn't have tried to do the driver at the same time but whats done is done it seems :(

But at least i'm able to see the GUI so its not all bad !

---

