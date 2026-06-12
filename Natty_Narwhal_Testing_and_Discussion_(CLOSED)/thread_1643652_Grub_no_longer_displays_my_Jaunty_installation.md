---
title: "Grub no longer displays my Jaunty installation"
date: 2010-12-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2010-12-12
My test system used to dual boot Jaunty and Natty.
After my last update grub quit displaying the entry for my Jaunty installation.

I tried a "sudo update-grub" to no avail.

---

### Post by karthick87 on 2010-12-12
Post the output of bootinfoscript,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ratcheer on 2010-12-12
See my bug 683355 on Launchpad. They state that they are not going to fix it because the fix causes more problems than this.

Here is how I got around it. This may or may not work for you.

1) In Natty, run "sudo os-prober". If I recall, the output will inform you if it finds another OS on the system.

2) After os-prober completes, run "sudo grub-install /dev/xxx" where xxx is the device, but not the partition, on which Ubuntu is installed. E.g., if Natty is installed on /dev/sda6, use /dev/sda.

In my case, this detected my other Ubuntu installation and put it back on the grub menu. Hope it helps.

Tim

---

### Post by JRV on 2010-12-12
ratcheer - Thank you for your response, but it didn't work.

karthick87 - Thank you for your response, here is my RESULTS.txt File.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 9cem.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8447 MB, 8447459328 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16498944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     2,184,839     2,184,777  83 Linux
/dev/sda2           2,184,840    14,249,654    12,064,815  83 Linux
/dev/sda3          14,249,655    16,498,754     2,249,100  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        321bb365-319a-4be4-994c-7858470e2171   ext3       thin                          
/dev/sda2        2af66828-1aec-4711-8f48-d856472c0a29   ext3                                     
/dev/sda3                                               swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=321bb365-319a-4be4-994c-7858470e2171 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=321bb365-319a-4be4-994c-7858470e2171

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
# defoptions=quiet splash quiet

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
uuid		321bb365-319a-4be4-994c-7858470e2171
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=321bb365-319a-4be4-994c-7858470e2171 ro quiet splash quiet 
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid		321bb365-319a-4be4-994c-7858470e2171
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=321bb365-319a-4be4-994c-7858470e2171 ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, memtest86+
uuid		321bb365-319a-4be4-994c-7858470e2171
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=321bb365-319a-4be4-994c-7858470e2171 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/menu.lst
    .4GB: boot/grub/stage2
    .4GB: boot/initrd.img-2.6.28-19-generic
    .4GB: boot/vmlinuz-2.6.28-19-generic
    .4GB: initrd.img
    .4GB: vmlinuz

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2af66828-1aec-4711-8f48-d856472c0a29
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2af66828-1aec-4711-8f48-d856472c0a29
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=yellow/brown
set menu_color_highlight=yellow/red
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.37-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2af66828-1aec-4711-8f48-d856472c0a29
	linux	/boot/vmlinuz-2.6.37-8-generic root=UUID=2af66828-1aec-4711-8f48-d856472c0a29 ro   quiet splash
	initrd	/boot/initrd.img-2.6.37-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2af66828-1aec-4711-8f48-d856472c0a29
	echo	'Loading Linux 2.6.37-8-generic ...'
	linux	/boot/vmlinuz-2.6.37-8-generic root=UUID=2af66828-1aec-4711-8f48-d856472c0a29 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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
UUID=2af66828-1aec-4711-8f48-d856472c0a29 /               ext3    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


   5.1GB: boot/grub/core.img
   5.1GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.37-8-generic
   5.1GB: boot/vmlinuz-2.6.37-8-generic
   5.2GB: initrd.img
   5.1GB: vmlinuz

```

---

### Post by Quackers on 2010-12-12
You appear to have a mixture of grub legacy and grub2.
Your boot script, though quite normal for a Natty install, doesn't say where grub2 is looking for its boot files. So not too helpful in that respect.
It may help to re-install grub2 but I'm not 100% sure.
It may be prudent to await further clarification.

---

### Post by wilee-nilee on 2010-12-12
If you could use supergrub to get into jaunty, upgrade it to grub2 that is what I would do. The leave it as the lead boot in the setup, any grub updates in Natty would override this but once grub2 is in jaunty it is just a easy reload.

Thats how I would insure I had the jaunty in control of the boot rather then a not released (Running 2 versions on a SDHC card) myself

The only problem I see with this idea is jaunty is past the end of release cycle by a month or more.

You might be better served by backing up your stuff you can't loose the putting a later still supported release in its place that has grub2

---

### Post by drs305 on 2010-12-12
I'm curious - when you ran "sudo os-prober" was your Jaunty OS shown in the terminal output?

---

### Post by ratcheer on 2010-12-13
Ok, I have figured it out. The problem is told about in the explanation of why they will not fix my bug. The filesystem of the other Linux installation is, for some reason, not clean. I always shut down cleanly, so I do not understand why the filesystem is not clean, but at any rate, that is the problem.

So first, in Natty, run: "sudo fsck /dev/xxxx" where xxxx is the partition your OTHER Ubuntu is installed on, e.g., /dev/sda2. In my case, I saw a bunch of obsolete inodes that were cleaned up.

Then run the os-prober and grub install as detailed in post #3.

I think the reason it worked for me as described in post #3 was purely by chance - my Maverick filesystem had just happened to come down cleanly before I tried it that time.

Tim

---

### Post by rondackcpu on 2010-12-13
Thank you, ratcheer.  Your suggestion in post #3 worked for me.  But fsck in post #8 reported the partition clean.  Maybe the error was in "ubiquity" when I re-installed Natty this morning (after the Python break.

CRS

---

### Post by cariboo on 2010-12-13
I just ran into a similar problem on my netbook, after todays kernel upgrade Maverick wasn't showing in grub. After running fsck, and then update-grub the Maverick menu selection showed up.

The last time I used Maverick, I hibernated the system, but haven't used it since, as I'm still chasing hibernation problems on Natty. It could be that grub-wasn't seeing the hibernated kernel, so it wasn't showing up in the grub menu.

If grub isn't showing a partition that wasn't shut down cleanly, this could lead to problems for those who have dual boot systems, as Windows may not show up in the menu either.

---

### Post by JRV on 2010-12-13
> **drs305 said:**
> I'm curious - when you ran "sudo os-prober" was your Jaunty OS shown in the terminal output?

Yes, when running os-prober from Natty the Jaunty Installation is the only entry that shows up.

---

### Post by JRV on 2010-12-13
> **ratcheer said:**
> Ok, I have figured it out. The problem is told about in the explanation of why they will not fix my bug. The filesystem of the other Linux installation is, for some reason, not clean. I always shut down cleanly, so I do not understand why the filesystem is not clean, but at any rate, that is the problem.
Tim

The Jaunty system is never shutdown cleanly.  It is a command line install with only xorg and gdm added.  The /etc/gdm.conf is modified so that it is just a XDMCP thin client, it boots directly into the chooser.  There is no way to exit the chooser and do a clean shutdown.  

From the Natty installation I did an fsck on Jaunty, then an update-grub and that fixed it.  
But it sounds like it that will need to be done every time grub is updated.

Thank you for the help.

---

### Post by ratcheer on 2010-12-13
> **cariboo907 said:**
> 

If grub isn't showing a partition that wasn't shut down cleanly, this could lead to problems for those who have dual boot systems, as Windows may not show up in the menu either.

That makes sense, but as I stated above, I always shutdown cleanly. Maybe there is some bug in the shutdown process or something is hanging up and does not shutdown correctly, but it is not a cockpit error.

Tim

---

### Post by cariboo on 2010-12-13
> **JRV said:**
> The Jaunty system is never shutdown cleanly.  It is a command line install with only xorg and gdm added.  The /etc/gdm.conf is modified so that it is just a XDMCP thin client, it boots directly into the chooser.  There is no way to exit the chooser and do a clean shutdown.  

From the Natty installation I did an fsck on Jaunty, then an update-grub and that fixed it.  
But it sounds like it that will need to be done every time grub is updated.

Thank you for the help.

Can't you use one of the consoles to do a clean shutdown? Ctrl-Alt-F1 to F6

---

### Post by JRV on 2010-12-13
> **cariboo907 said:**
> Can't you use one of the consoles to do a clean shutdown? Ctrl-Alt-F1 to F6

Good idea, I didn't think of that.  Thank you.

---

