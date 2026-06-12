---
title: "Sound IEC958 problem"
date: 2011-04-29
forum: Multimedia Software
---

### Post by gramsyn on 2011-04-29
Hello everybody,

I have a major problem with my PC sound.

I use the on-board sound chip of a Gigabyte motherboard (Realtek)and I have connected it with optical cable to an amplifier.

Everything worked fine, until February, when an update changed the kernel and the PC stopped giving sound signal! When I returned to the previous kernel (at grub), again everything worked. So,it doesn't seem to be a connection or drivers problem.

I supposed that with 11.04 edition this problem would be solved. But it isn't. In fact I have serious problem now because the old kernel isn't listed in grub anymore.

Can anyone help? Thanks in advance

---

### Post by gramsyn on 2011-04-30
I am trying to get an answer to this problem 3 months now. Perhaps no one knows what to do. 

Is there any way to let Canonical know about that fault in the upgrade, so as to fix it?

Do you think that an idea is to downgrade to an older version?

Sorry for the repost,but I am desperate.

---

### Post by Bray90820 on 2011-04-30
i probably should have been more specific i already tried alsamixer and all the settings in the general sound settings i also tried a the usb creative x-fi with headphones and that worked f you need anymore information from me just ask

---

### Post by Bray90820 on 2011-04-30
i apologize for posting that here i know it is completely off topic and i would remove it if i could

---

### Post by lidex on 2011-04-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by gramsyn on 2011-05-01
[http://www.alsa-project.org/db/?f=3545a51b63debd8f83a9182db4aaae31d761ed3c](http://www.alsa-project.org/db/?f=3545a51b63debd8f83a9182db4aaae31d761ed3c)


Can you have a look and see what's the problem?

---

### Post by lidex on 2011-05-04
> In fact I have serious problem now because the old kernel isn't listed in grub anymore.

If you didn't uninstall it, it's still there. Grub in natty only shows the latest kernel outright. You have to drop down to I believe the third line where it says something like previous kernels or other kernels. Don't remember exactly.
 
Once you get into working kernel, run the info script again please.

---

### Post by gramsyn on 2011-05-04
In fact my real issue is to solve the sound problem, in order to have sound using the latest edition.

If it is not possible, I would appreciate to be helped to restore the prompt to the previous kernel. [No, at the previous editions of kernel listed now I can't find the one I want. It lists only one]

If pasting the results of boot info helps you find out what's happening, I paste them:

```
      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2d.
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,757,816,234 1,757,816,172  83 Linux
/dev/sda2    *  1,757,816,832 1,758,021,631       204,800   7 HPFS/NTFS
/dev/sda3       1,758,021,632 1,953,521,663   195,500,032   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2          40,966,142 3,907,026,943 3,866,060,802   5 Extended
/dev/sdb5          40,966,144    48,779,263     7,813,120  82 Linux swap / Solaris
/dev/sdb6          48,781,312 3,907,026,943 3,858,245,632  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4038 MB, 4038066176 bytes
5 heads, 4 sectors/track, 394342 cylinders, total 7886848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 968     7,886,847     7,885,880   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f3a7f2d2-8890-4596-b74c-2646ed8180c4   ext4       Files                         
/dev/sda2        EE6ECEBC6ECE7D39                       ntfs       System Reserved               
/dev/sda3        84BAD175BAD163E8                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a2bc9592-f246-4882-b667-fc0c4e2353a8   swap                                     
/dev/sdb6        28d8f218-520c-4b2b-bdc1-e0c16cfe270f   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        AC92-6073                              vfat                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        5C180EA7180E7FEE                       ntfs       Expansion Drive               
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/AC92-6073         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
set locale_dir=($root)/boot/grub/locale
set lang=el_GR
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=28d8f218-520c-4b2b-bdc1-e0c16cfe270f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.38-8-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=28d8f218-520c-4b2b-bdc1-e0c16cfe270f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=28d8f218-520c-4b2b-bdc1-e0c16cfe270f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.35-28-generic-pae (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=28d8f218-520c-4b2b-bdc1-e0c16cfe270f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 28d8f218-520c-4b2b-bdc1-e0c16cfe270f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root EE6ECEBC6ECE7D39
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=28d8f218-520c-4b2b-bdc1-e0c16cfe270f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a2bc9592-f246-4882-b667-fc0c4e2353a8 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


1927.7GB: boot/grub/core.img
 319.0GB: boot/grub/grub.cfg
  44.3GB: boot/initrd.img-2.6.35-28-generic-pae
  46.2GB: boot/initrd.img-2.6.38-8-generic-pae
1934.7GB: boot/vmlinuz-2.6.35-28-generic-pae
  44.8GB: boot/vmlinuz-2.6.38-8-generic-pae
  46.2GB: initrd.img
  44.3GB: initrd.img.old
  44.8GB: vmlinuz
1934.7GB: vmlinuz.old
```

---

### Post by lidex on 2011-05-04
Do you know which kernel was working?
You currently have the latest natty and a recent maverick available in grub.
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by gramsyn on 2011-05-04
I don't remember exactly which kernel was working, but it was the 4th last. Anyway. Do you think I should try to install a kernel and see what happens, or it will create other issues.

Do I have any chance fixing the sound using the last kernel?

---

### Post by lidex on 2011-05-04
No, should be fine, just follow instructions on that page.

---

### Post by gramsyn on 2011-05-09
I have installed two mainline kernels, but I don't get a listing of them at grub. The page says that it will list them automatically after installation. What should I do?

---

### Post by lidex on 2011-05-10
Run this command:
```
sudo update-grub
```
Now reboot and at the grub screen look for the third line down and select it. Hit enter and you should be given a list of other kernels.

---

### Post by gramsyn on 2011-05-10
I run the command. At the terminal there are some lines stating that the kernel versions I have downloaded are found. I restart, but there are not listed.

---

### Post by lidex on 2011-05-10
> **gramsyn said:**
> I run the command. At the terminal there are some lines stating that the kernel versions I have downloaded are found. I restart, but there are not listed.

They're in there, you just have to look for them. Reboot and at the grub screen move the selection down using arrow keys to stop the boot countdown. Now look at the options available. There should be a line that says something like additional kernels, probably the third line. Select that and hit your enter key.

---

### Post by gramsyn on 2011-05-10
I do that, but there are not listed

---

