---
title: "[SOLVED] how do I switch grub location from one disk to the other?"
date: 2008-03-28
forum: Mythbuntu
---

### Post by arjay1 on 2008-03-28
Hi all - I read the grubhowto here and it is very helpful but I got a bit confused and am not sure if fits my case.  Could someone spell it out for me if they can.

I have two drives on my PC - sda (sda1 and sda2  - ignoring the swap) and sdb (sdb1 and sdb2). I had mythbuntu 7.10 installed OK and running on sda with the system files on sda1 and /home on sda2.

I wanted to try out mythbuntu 8.04 beta, but not overwrite my 7.10 install.  So I installed 8.04 to sdb on sdb1 for system files and sdb2 for /home.  Unfortunately, I expected the 8.04 install on sdb1 to write the grub files to sdb but it wrote them to sda (hd0) instead.  Now I can't boot 7.10 on sda unless I have both hard disks in the machine.

I want to remove the sdb disk from the machine and still have 7.10 boot again from sda as it did before I messed about.  If I try that now I just get grub error (15?).

I'll post this using this computer and edit it with some more info when I can get back on the problem machine in a little while.

TIA


richard@tranquil:~$ sudo fdisk /dev/sda -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a12b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60427   485379846   83  Linux
/dev/sda2           60428       60801     3004155    5  Extended
/dev/sda5           60428       60801     3004123+  82  Linux swap / Solaris
richard@tranquil:

 richard@tranquil:~$ sudo fdisk /dev/sdb -l

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3493    28057491   83  Linux
/dev/sdb2            3494        3649     1253070    5  Extended
/dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris
richard@tranquil:~$ 

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
timeout		10

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
# kopt=root=UUID=df5abc0c-ebac-4d0e-9f25-7a09aa4c743b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=df5abc0c-ebac-4d0e-9f25-7a09aa4c743b ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=df5abc0c-ebac-4d0e-9f25-7a09aa4c743b ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=618d2e0a-60f2-4cb5-b67e-41dcf415b74d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=618d2e0a-60f2-4cb5-b67e-41dcf415b74d ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by odiseo77 on 2008-03-28
I think the problem is Mythbuntu 8.04 automatically installed its grub into the master boot record (MBR) located in /dev/sda. Try this: boot with both devices plugged in, so you can boot into Ubuntu 7.10. Once you've booted inside Gutsy, simply type the following command:

```
sudo grub-install /dev/sda
```

Restart and you should be able to boot into Gutsy now. 

If you want to continue booting Mythbuntu, you will have to edit Gutsy's /boot/grub/menu.lst and add the right lines for it (you can copy them from your mythbuntu installation's menu.lst).

---

### Post by arjay1 on 2008-03-28
Thanks heaps.

I'll give it a try tomorrow.

regards

RJ

---

### Post by arjay1 on 2008-04-10
Thanks - worked just fine

---

