---
title: "Mythbuntu 8.10 - won't boot - swap problem"
date: 2009-01-27
forum: Mythbuntu
---

### Post by lklig on 2009-01-27
I upgraded to Mythbuntu 8.10 a few weeks ago.  Had everything setup and working and was very happy with the new version.

After recompiling my v4l drivers and rebooting, I got the following error on startup:

Starting up …
Loading, please wait…
kinit: name_to_dev_t(/dev/disk/by-uuid/bd656dcd-04b4-412f-a880-62a6553bd8b) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/bd656dcd-04b4-412f-a880-62a6553bd8b
kinit: No resume image, doing normal boot…

After searching around I found some methods to resolve, which included swapping off the swap partition, using mkswap, and then  update-initramfs.

Unfortunately nothing worked, and I had no way to recover the box.  I wiped the drive, did a full scan (500GB Seagate Barracuda), and it came up clean.  I reinstalled and everything seemed fine after several restarts, however a couple days later the same thing happened.  Strange thing as well is that a friend of mine has experienced the exact same thing with 2 different brand new drives, on Seagate and one WD.  

Previously I had Mythbuntu 8.04 running on the exact same hardware for months without a problem.

Has anyone experienced this problem?  Any ideas?

Cheers,

---

### Post by caljohnsmith on 2009-01-27
So can you boot into Mythbuntu at all now, or no? If not, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by lklig on 2009-01-29
If I hit alt-ctrl-del it will boot me into a single console.  So, I booted off of the Mythbuntu 8.10 live cd and run the script you linked to.  These are the results.  I really hope this helps so that I can get back onto my box!

Thanks.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00025c9d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    23,438,834    23,438,772  83 Linux
/dev/sda2          23,438,835 1,953,520,064 1,930,081,230   5 Extended
/dev/sda5          23,438,898    25,430,894     1,991,997  82 Linux swap / Solaris
/dev/sda6          25,430,958 1,953,520,064 1,928,089,107  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b2607603-684c-4387-a4e3-71f8307e3176" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="81534229-c4a6-49b6-a257-2848b15e01b4" TYPE="swap" 
/dev/sda6: UUID="a907684f-5ea5-4b39-9997-4d15042ae3f1" TYPE="xfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

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
# kopt=root=UUID=b2607603-684c-4387-a4e3-71f8307e3176 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b2607603-684c-4387-a4e3-71f8307e3176

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b2607603-684c-4387-a4e3-71f8307e3176
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2607603-684c-4387-a4e3-71f8307e3176 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b2607603-684c-4387-a4e3-71f8307e3176
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2607603-684c-4387-a4e3-71f8307e3176 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b2607603-684c-4387-a4e3-71f8307e3176
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b2607603-684c-4387-a4e3-71f8307e3176 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=a907684f-5ea5-4b39-9997-4d15042ae3f1 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=81534229-c4a6-49b6-a257-2848b15e01b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


    .8GB: boot/grub/menu.lst
    .8GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.27-7-generic
    .8GB: boot/vmlinuz-2.6.27-7-generic
    .8GB: initrd.img
    .8GB: vmlinuz


```

---

### Post by caljohnsmith on 2009-01-29
Well the script results don't reveal anything wrong with at least your basic boot setup, so unfortunately it doesn't give us any significant clues what your problem might be. You mentioned in your first post about compiling your own v4l drivers and getting booting errors, so then you reinstalled Mythbuntu; after you reinstalled, did you again try to compile your own v4l drivers? Also, you said after a few days with your fresh reinstall the "same thing happened"--do you mean you got the same kinit errors you show in your first post? You mentioned that you did a "full scan" of the HDD and that it came up clean, so what was the full scan you did? Was it some sort of HDD diagnostic test, maybe a SMART HDD test?

---

### Post by lklig on 2009-01-29
After my initial post, with a brand new HDD, I installed Mythbuntu 8.10, compiled the v4l drivers, rebooted, and all was well.  Just this evening I restarted the machine and it has come up with the exact same kinit error that I posted above.  There must be a way to recover the /var/lib partition of the drive...

By a full scan, I plugged the drive into a Windows machine, and ran the Seagate full scan, that took over an hour which reported no errors.

---

### Post by caljohnsmith on 2009-01-29
OK, how about from your Live CD try:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And for the first Mythbuntu entry, find the "kernel" line, and add "rootdelay=120" at the end of that line similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d0b10c15-66ed-4d1c-b7f6-c1fc131636f7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Blue"]rootdelay=120[/COLOR]
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```
Reboot, select the Mythbuntu entry in the Grub menu that has the rootdelay line added to it, and let me know if it makes any difference.

---

### Post by lklig on 2009-01-29
Unfortunately that had no affect.  Still hangs on the same error above.

---

### Post by lklig on 2009-01-29
Biggest issue with this, is that my /var/lib mount has disappeared, which seems to be a bit different from other peoples postings with this same error message.

---

### Post by caljohnsmith on 2009-01-29
I'm just curious, but why did you choose to put /var/lib on its own partition, and also why did you choose xfs as the file system? Maybe a more standard install with /var/lib in your main ext3 partition would work better.

---

### Post by lklig on 2009-01-30
That is what the Mythbuntu guided partition does for you.  I have wiped the disk, and manually partitioned the drive, with /var/lib on the main partition, all ext3.  We'll see what happens.

---

