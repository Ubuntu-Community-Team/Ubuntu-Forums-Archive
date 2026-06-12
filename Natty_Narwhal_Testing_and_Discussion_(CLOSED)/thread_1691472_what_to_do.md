---
title: "what to do"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-02-19
hello Folks
this is really starting to get to me I have done a dd of both my hards drives I reloaded windows on sda it works ok then I tried installing natty on sdb it went through ok till it got to installing boot loader it then told me installer was broken i worked on it till 2 amm then did a dd of both discs again as windows was some how crashed to I have installed windows its ok when I installed natty I let it install the upgrades and third party software is this where my problem lies natty build was 18th of feb
regards Ron

---

### Post by cariboo on 2011-02-19
Did you use the instructions I gave you [here]("http://ubuntuforums.org/showpost.php?p=10469542&postcount=16"), to fix grub?

BTW I did a fresh install using the iso from the 18th, with zero problems yesterday, I have basically the same setup as you, Windows 7 and Maverick on /dev/sda and natty on /dev/sdb. My system has an Nvidia graphics card, so I am trying the nouveau drivers with the 3D library.

---

### Post by rbrick49 on 2011-02-20
hi Caraboo
do i leave this code as is or do I change this
   1. sudo mount /dev/sdXx /mnt <this to this sudo mount /dev/sdb /mnt
   2. sudo mount -o bind /sys /mnt/sys
   3. sudo mount -o bind /dev /mnt/dev
   4. sudo mount -o bind /proc /mnt/proc
   5. sudo chroot /mnt
this is what I did and it gave me an error my windows is on sda and ubuntu on sdb its an amd x 64 system not i386
regards ron
ps did you do updates while installing or not

---

### Post by VMC on 2011-02-20
> **cariboo907 said:**
> ... My system has an Nvidia graphics card, so I am trying the nouveau drivers with the 3D library.

I'm interested in how you deployed that. I used todays[19th] ISO. Installed on a fresh partition and had no desktop. Even using "nomodeset". I have the integrated series6 chip set.

---

### Post by rbrick49 on 2011-02-20
Vmc you can put in that code rom terminal in live cd just reboot live cd open terminal and put the code that caraboo gave me but I got an error back. waiting on Caraboo to verify the code

---

### Post by rbrick49 on 2011-02-20
heres the error message
ubuntu@ubuntu:~$ sudo mount /dev/sdb/mnt
mount: can't find /dev/sdb/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
ubuntu@ubuntu:~$ sudo mount -o bind /sys/mt/sys
mount: can't find /sys/mt/sys in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o bind /sys/mnt/sys
mount: can't find /sys/mnt/sys in /etc/fstab or /etc/mtab

---

### Post by Quackers on 2011-02-20
You are missing spaces on occasions, and missing letters on others. Copy/paste the commands (and adjust as necessary) - it's safer!

---

### Post by rbrick49 on 2011-02-20
yes I did that Quackers but had to readjust as you said but it went through ok but on reboot black screen again I cant help but think its a major graphics problem.I purchased a new case and the computer tech reinstalled all my components including a new ati graphics card 6950 model no. my motherboard has an ati radeon 3100 on board windows disabled it to take the new card but ubuntu wont give me a graphics screen of an sort even low reolution which it should just as windows did before installing drivers from disc that came with the card. I cant help thinking windows has done something weird. I have removed the 6950 card and am now running this computer graphics from the 3100 card. I am at a loss as ubuntu should run in low graphics mode no matter what card is installed
my system sda windows 7
sdb ubuntu 
amd 5000+ processor
8gig of ram
asusm3a78-cm motherboard
I have tried reinstalling maverick as a standalone on sda,i watched it load it went through ok on reboot black screen
I am lost never had this drama before
regards Ron

---

### Post by Quackers on 2011-02-20
If you boot from the live cd and select "try ubuntu" does the desktop load?

---

### Post by rbrick49 on 2011-02-20
yes it does load and runs ok

---

### Post by Quackers on 2011-02-20
Ok, thanks. A graphics problem is less likely then (though not impossible).
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ronacc on 2011-02-20
are you getting a grub menu yet ?

---

### Post by rbrick49 on 2011-02-20
here you go quackers
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18982d9d-3526-4d20-95aa-ac3438798e10   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        adeee93f-f74f-44b1-a9c2-1d795fe1efdf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c8d428ed-e981-40ad-8be0-ec284a994661   ext4       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=18982d9d-3526-4d20-95aa-ac3438798e10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=adeee93f-f74f-44b1-a9c2-1d795fe1efdf none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 159.6GB: boot/initrd.img-2.6.37-7-generic
 227.7GB: boot/vmlinuz-2.6.37-7-generic
 159.6GB: initrd.img
 227.7GB: vmlinuz

---

### Post by rbrick49 on 2011-02-20
heres what I get when I use the script Caraboo posted
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 9de.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18982d9d-3526-4d20-95aa-ac3438798e10   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        adeee93f-f74f-44b1-a9c2-1d795fe1efdf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c8d428ed-e981-40ad-8be0-ec284a994661   ext4       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/apt               iso9660    (ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 2.6.37-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=18982d9d-3526-4d20-95aa-ac3438798e10 ro   quiet splash
	initrd	/boot/initrd.img-2.6.37-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
	echo	'Loading Linux 2.6.37-7-generic ...'
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=18982d9d-3526-4d20-95aa-ac3438798e10 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 18982d9d-3526-4d20-95aa-ac3438798e10
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=18982d9d-3526-4d20-95aa-ac3438798e10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=adeee93f-f74f-44b1-a9c2-1d795fe1efdf none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 227.7GB: boot/grub/core.img
 227.7GB: boot/grub/grub.cfg
 159.6GB: boot/initrd.img-2.6.37-7-generic
 227.7GB: boot/vmlinuz-2.6.37-7-generic
 159.6GB: initrd.img
 227.7GB: vmlinuz
and it still wont boot still getting black screen
regards Ron

---

### Post by ronacc on 2011-02-20
can you now mount sdb1 by clicking on it from nautilus on the live cd ? if you can, open gedit as root from the live cd ```
sudo gedit
``` no password required to run sudo from the live session . navigate to sdb1/boot/grub and open grub.cfg and remove splash quiet and vthandoff=7  from the line that starts "linux  /boot/vmlinuz "  . also change the line that reads
"set gfxpayload=$linux_gfx_mode" to read  "set gfxpayload=text" save and reboot and see what happens .

---

### Post by Quackers on 2011-02-20
According to the first boot script output you have the following
```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> No boot loader is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu natty (development
branch)
Boot files/dirs: /etc/fstab
```

But, according to the second boot script output (which is the same script) you have
```

=> Grub 2 is installed in the MBR of /dev/sda and looks for 9de.
=> No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu natty (development
branch)
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

Which is completely different! This was run on the same pc?

---

### Post by rbrick49 on 2011-02-20
yes quackers the first script I posted was before I put in the script that Caraboo posted to install the boot loader.The second script is the reult from installing the boot loader but it still wont boot,I am still getting a black screen.

---

### Post by Quackers on 2011-02-20
Lol, well the first one is useless then :-)
Which hard drive is set to boot first in bios?
Also did you see ronacc's post above my last one?

---

### Post by cariboo on 2011-02-20
@rbrick49

My instruction work as typed, the only thing you have to change is where you installed ubuntu, if you are unsure of which partition you installed it on, open a terminal type:

```
sudo fdisk -l
```

This command will give you a listing of your hard drives and partitions. On the system I'm on now the output looks like this:

```
udo fdisk -l
[sudo] password for cariboo

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016e1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216       30402   234432512   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1287    10335937+  83  Linux
/dev/sdb2            1287        1530     1952768   82  Linux swap / Solaris
/dev/sdb3            1531       30401   231906307+  83  Linux
cariboo@alexis-natty:~$
```

This system is a dual boot, Maverick and Natty, You should see something similar if you installed on /dev/sdb. So the initial command would be:

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by rbrick49 on 2011-02-20
well thank you all Caraboo,ronacc and quackers its working it was the bios when the computer guy installed my components in the new computer case he didnt check the bios thats what the problem was booting from second hard drive instead of first one and now I have learnt to install a boot loader also thank you all
regards Ron

---

### Post by Quackers on 2011-02-20
Glad to see you're up and running now.

---

