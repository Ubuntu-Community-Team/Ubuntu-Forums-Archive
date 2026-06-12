---
title: "help grub wont let me select windows anymore!"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dirtyburger on 2010-09-16
hi everyone, today i installd 10.10 beta

the installer was different, what i did was make a huge 32 gb free space, for the intall

i then selected this space and made a 29689 gb and made it ext4, made it mount at / to intall ubuntu

then i made a 2 gb partion and made it a swap partition

ubuntu 10.10 install goes beatifully, and works good

but now when i reboot, i try to arrow down to the windows 7 loader in grub, but ubuntu auto starts! theres still time lft in the timer

what did i do wrong>? ubuntu 10.04 didnt do this!

while were at it why wasnt there a use largest free space option in the intaller? manually editing partitions causes crap like this to happen!

how do i fix this please help i dont wanna reintall windows, then resinstall ubuntu AGAIN.

i need ms office fast pls

how do i stop grub from auto starting ubuntu, i cant even select memtest because it picks ubuntu so fast

---

### Post by wilee-nilee on 2010-09-16
> **dirtyburger said:**
> hi everyone, today i installd 10.10 beta

the installer was different, what i did was make a huge 32 gb free space, for the intall

i then selected this space and made a 29689 gb and made it ext4, made it mount at / to intall ubuntu

then i made a 2 gb partion and made it a swap partition

ubuntu 10.10 install goes beatifully, and works good

but now when i reboot, i try to arrow down to the windows 7 loader in grub, but ubuntu auto starts! theres still time lft in the timer

what did i do wrong>? ubuntu 10.04 didnt do this!

while were at it why wasnt there a use largest free space option in the intaller? manually editing partitions causes crap like this to happen!

how do i fix this please help i dont wanna reintall windows, then resinstall ubuntu AGAIN.

i need ms office fast pls

how do i stop grub from auto starting ubuntu, i cant even select memtest because it picks ubuntu so fast

Post the boot script in my signature in code tags, as described, if you can.

---

### Post by dirtyburger on 2010-09-16
woo that took a while to enter that terminal command


SDA4 is my storage partion btw

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    62,095,359    61,888,512   7 HPFS/NTFS
/dev/sda3         123,989,670   625,137,344   501,147,675   7 HPFS/NTFS
/dev/sda4          62,097,406   123,987,967    61,890,562   5 Extended
/dev/sda5          62,097,408   120,083,736    57,986,329  83 Linux
/dev/sda6         120,084,480   123,987,967     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C3E919E3E9171AE                       ntfs       System Reserved               
/dev/sda2        FA9A9C4B9A9C0673                       ntfs                                     
/dev/sda3        1AB6C7BEB6C79921                       ntfs       Storage                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        189817a5-e7a8-437a-ac5c-9e98ab499e5a   ext4                                     
/dev/sda6        b1f483d1-863b-4b62-ab20-4c1f88bf4fe5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=189817a5-e7a8-437a-ac5c-9e98ab499e5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=189817a5-e7a8-437a-ac5c-9e98ab499e5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 189817a5-e7a8-437a-ac5c-9e98ab499e5a
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c3e919e3e9171ae
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=189817a5-e7a8-437a-ac5c-9e98ab499e5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b1f483d1-863b-4b62-ab20-4c1f88bf4fe5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  36.2GB: boot/grub/core.img
  59.9GB: boot/grub/grub.cfg
  32.9GB: boot/initrd.img-2.6.35-19-generic
  36.2GB: boot/vmlinuz-2.6.35-19-generic
  32.9GB: initrd.img
  36.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  64 53 55 56 57 a1 14 db  97 10 33 c4 50 8d 44 24  |dSUVW.....3.P.D$|
00000010  78 64 a3 00 00 00 00 8d  4c 24 34 c6 44 24 16 00  |xd......L$4.D$..|
00000020  e8 2b b7 0b 00 89 44 24  38 c6 40 21 01 8b 44 24  |.+....D$8.@!..D$|
00000030  38 89 40 04 8b 44 24 38  89 00 8b 44 24 38 33 ff  |8.@..D$8...D$83.|
00000040  89 40 08 89 7c 24 3c 8b  b4 24 88 00 00 00 39 7e  |.@..|$<..$....9~|
00000050  0c 89 bc 24 80 00 00 00  75 11 e8 f1 45 f4 ff 89  |...$....u...E...|
00000060  46 0c 89 78 48 8b 46 0c  89 40 44 8b 5e 0c 3b df  |F..xH.F..@D.^.;.|
00000070  75 11 e8 d9 45 f4 ff 89  46 0c 89 78 48 8b 46 0c  |u...E...F..xH.F.|
00000080  89 40 44 8b 46 0c 8b 70  44 3b de 0f 84 7f 00 00  |.@D.F..pD;......|
00000090  00 8b 13 8b 42 18 8b cb  ff d0 84 c0 75 64 57 8b  |....B.......udW.|
000000a0  cb e8 7a 69 f4 ff 85 c0  75 58 8b 43 20 c1 e0 1b  |..zi....uX.C ...|
000000b0  c1 f8 1b 83 f8 04 74 0e  83 f8 05 74 09 3b c7 74  |......t....t.;.t|
000000c0  05 83 f8 02 75 3c 53 e8  14 f1 ff ff 83 c4 04 84  |....u<S.........|
000000d0  c0 75 2f 89 9c 24 88 00  00 00 e8 e1 e6 ff ff 8d  |.u/..$..........|
000000e0  8c 24 88 00 00 00 51 8d  54 24 20 52 8d 4c 24 3c  |.$....Q.T$ R.L$<|
000000f0  89 44 24 24 e8 e7 fd ff  ff 8b c8 e8 60 41 eb ff  |.D$$........`A..|
00000100  33 ff 8b 5b 48 3b de 75  88 8d a4 24 00 00 00 00  |3..[H;.u...$....|
00000110  8b 44 24 38 8b 28 8d 7c  24 34 c6 84 24 88 00 00  |.D$8.(.|$4..$...|
00000120  00 00 89 6c 24 28 89 7c  24 24 89 44 24 30 8b ff  |...l$(.|$$.D$0..|
00000130  85 ff 74 08 8d 44 24 34  3b f8 74 05 e8 7e e6 13  |..t..D$4;.t..~..|
00000140  00 3b 6c 24 30 0f 84 fc  01 00 00 85 ff 75 05 e8  |.;l$0........u..|
00000150  6b e6 13 00 3b 6f 04 75  05 e8 61 e6 13 00 3b 6f  |k...;o.u..a...;o|
00000160  04 8d 75 10 75 05 e8 54  e6 13 00 8b 46 04 85 c0  |..u.u..T....F...|
00000170  c7 44 24 18 00 00 00 00  0f 84 b3 01 00 00 8b 4e  |.D$............N|
00000180  08 2b c8 c1 f9 02 89 4c  24 1c 0f 84 a1 01 00 00  |.+.....L$.......|
00000190  8b 5c 24 18 83 c3 01 3b  d9 89 5c 24 20 0f 84 82  |.\$....;..\$ ...|
000001a0  01 00 00 8b 4e 04 85 c9  74 0c 8b 46 08 2b c1 c1  |....N...t..F.+..|
000001b0  f8 02 3b d8 72 05 e8 04  e6 13 00 8b 7e 04 00 ef  |..;.r.......~...|
000001c0  ff ff 83 ef ff ff 02 00  00 00 19 cd 74 03 00 ef  |............t...|
000001d0  ff ff 05 ef ff ff 1b cd  74 03 e7 92 3b 00 00 00  |........t...;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by kansasnoob on 2010-09-16
Well, "/etc/grub.d/30_os-prober" did not find Windows for some reason, so the first thing to try is simply running:

```
sudo update-grub
```

You should be able to see from the output if it finds Windows, or you can run the command:

```
cat /boot/grub/grub.cfg
```

Then look at the section "/etc/grub.d/30_os-prober" and see if it was added.

---

### Post by arubislander on 2010-09-16
You know 10.10 is beta software right? The idea being: **Beta not to install this software on a production machine!**

Having said that, you should try:
```
$ sudo update-grub
```
and reboot.

Chances are the installer did not recognize your Windows partition at install time, but running the above command should add it to your grub menu.

---

### Post by dirtyburger on 2010-09-16
i ran the first sudo command and thi was the output

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-19-generic
Found initrd image: /boot/initrd.img-2.6.35-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
Found Windows 7 (loader) on /dev/sda1
done

------------


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c3e919e3e9171ae
    chainloader +1

-----------


what does this mean??

sorry for the anger, yes it was my fault to install a beta

now i just want a solution tho, sorry

lol

but ya the problem was never that i couldent see the windows 7 in gruyb,  its jut every time i move the arrow keys to select it, ubuntu boots!

i cant move the cursor to get to windows 7, or even memtest!



[B]
I have rebooted after running all the commands, same problem
windows 7 loader is visabl;e, but when i press teh arrow keys to scroll down to it, ubuntu automaticcly boots, in fact whatever i press ubuntu boots immediatly, cant even scroll down to memtest, let alone windows[/B]

---

### Post by dirtyburger on 2010-09-16
sry dbl post

---

### Post by kansasnoob on 2010-09-16
Sorry, I see now that Win was there. Sometimes I fail to see the obvious :)

Let me study a bit more.

BTW sda4 is your extended partition, I'd assume that sda3 is DATA?

---

### Post by dirtyburger on 2010-09-16
> **kansasnoob said:**
> Sorry, I see now that Win was there. Sometimes I fail to see the obvious :)

Let me study a bit more.

BTW sda4 is your extended partition, I'd assume that sda3 is DATA?

wow thanks for all the support man!

honestly that SDA file in the code confuses me a little bit, i didn't know i had 3 NTFS ones O.o and the order is all screwy

i know my partitions are as follows when i installed ubuntu

SDA1: windows 7 system reserved/loader - 100 mb

SDA2: windows 7 install partition - around 32 GB

SDA3: ubuntu install partition - around 30 gb

SDA4: ubuntu swap partition - 2 gb

SDA5: Storage partition - 257 GB

i really dont know what SDA6 is, i dont think i have any unallocated space

THANKS for all the support man, its only a matter of time before i need ms office again :( if i can get this fixed without a complete format o 7 + ubuntu and fresh start, that would be golden

heres a picture of my partition layout from disk utility, if it helps u visualize any

[IMG]http://img844.imageshack.us/img844/9158/hddc.png[/IMG]

---

### Post by kansasnoob on 2010-09-16
A screenshot of Gparted would be more helpful to me.

How did you resize Windows? Using the Win 7 utility, the Live installer, or Gparted? I always resize Vista and Win 7 with only it's own tools!

Do you have Win 7 recovery discs?

Never panic! Doing so only makes things worse.

Just as a matter of troubleshooting I'd first want to see a screenshot of Gparted.

Next I'd try restoring the Windows mbr. If you have a Win 7 disc you can do it the Windows way:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or if you have no Win 7 disc you can do it with an Ubuntu Live CD:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

This, of course will render Ubuntu unbootable so you can restore grub2 as described in that first link or my way:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Knowing whether or not Win will boot on it's own will tell us a lot.

---

### Post by dirtyburger on 2010-09-16
hi everyone, ive found a workaround but its far from ideal, id really like to know what settings grub has messed up???

whenever i get to the grub select menu, i decied to press e for settings, got confused as hell and pressed esc, once back at the boot menu and can move the selector as i please and boot whatever i want

i botted in windows 7, and it works fine got to the desktop, rebooted the system, and it auto picked ubuntu again

what has been set so that the cursor auto loads ubuntu unless i go into settings????

surely this is a easy fix?

EDIT:

> **kansasnoob said:**
> A screenshot of Gparted would be more helpful to me.

How did you resize Windows? Using the Win 7 utility, the Live installer,  or Gparted? I always resize Vista and Win 7 with only it's own tools!

Do you have Win 7 recovery discs?

Never panic! Doing so only makes things worse.

Just as a matter of troubleshooting I'd first want to see a screenshot of Gparted.

Next I'd try restoring the Windows mbr. If you have a Win 7 disc you can do it the Windows way:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or if you have no Win 7 disc you can do it with an Ubuntu Live CD:

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda  mbr
```This, of course will render Ubuntu unbootable so you can  restore grub2 as described in that first link or my way:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev  /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo  chroot /mnt
``````
grub-install  /dev/sda
``````
exit
``````
sudo umount /mnt/dev &&  sudo umount /mnt/proc && sudo umount /mnt
```Knowing whether  or not Win will boot on it's own will tell us a lot.


as i recently discovered windows is completly bootable! and the cursor problem can be fixed by going into grub settings, then pressing esc and going back to the boot menu!

i dont know if should use such drastic commands, unless you think there is no other way, of course


what happened and how do i fix this behaviour so i can select and os by default?!


THANKS!!!!

---

### Post by dirtyburger on 2010-09-16
hi kanasnoob

ive booted into the live cd, and heres a screenshot of my gparted

[img]http://img704.imageshack.us/img704/110/screenshoteu.png[/img]

---

### Post by kansasnoob on 2010-09-16
OK, sorry for being dense, but I want to be perfectly clear on this. If you press one of the "arrow" up or down keys it boots Ubuntu without even allowing you to select another OS or boot option?

Did you use the actual Beta? Or a daily build?

Have you tried updating Maverick?

I've not seen this behavior before so I'm very curious myself :)

---

### Post by kansasnoob on 2010-09-16
Glad we can at least crank down the urgency :D

I know what it's like to be stuck absolutely "needing" to get something done. Scary stuff! And it does little good to kick ones own rear end after jumping into something at the wrong moment.

---

### Post by dirtyburger on 2010-09-16
> **kansasnoob said:**
> OK, sorry for being dense, but I want to be perfectly clear on this. If you press one of the "arrow" up or down keys it boots Ubuntu without even allowing you to select another OS or boot option?

Did you use the actual Beta? Or a daily build?

Have you tried updating Maverick?

I've not seen this behaviour before so I'm very curious myself :)

hi thanks for replying again, been heping me for like a hour im very thankful!

ya its the wiedest thing

i downloaded the 64 bit iso from here and burned to a dvd, like i also do with os's

[http://www.ubuntu.com/testing/maverick/beta](http://www.ubuntu.com/testing/maverick/beta)

im guessing its the beta?

it works fine, but at boot when i get the the grub select menu im presented with the usual options

ubuntu - first option, so its highlighted
ubuntu recovery
memtest
othermemtestiforget
othermemtestiforget
windows 7 loader (sda1 or something lol going by memory :P)

i want to go down to windows 7 to boot it, instead of ubuntu,

when i press the DOWN arrow key ubuntu takes over and boots, regardless o the countdown timer i dont even see the highlighted option move, ubuntu just boots!

if it press ANYTHING on the keyboard ubuntu takes over and boots 

i cant select anyhting but ubuntu, because ubuntu boots no matter what

unless i press e, go into grub options and press esc to get back to the boot menu

after that, im able to select windows 7, memtest whatever i want freely with the arrow keys just like how i should!

the next time i reboot however, ubuntu takes control and i cant select anything but ubuntu, without going into grub options





now i dont know much about grub, but this seems like some type o setting? 

i wonder what this auto boot setting is, i know its specifc to 10.10 because i formatted and reintalled 10.10 when i first encountered this issue it did not fix the problem, as i am posting here lol!

10.04 worked fine and i could selct ubuntu, windows or memtest right off the bat

hope i was clear!

and thanks for helping again! p/s sorry about my redicolous typos, this keyboard is messed up and doesnt register all the keystrokes all the time

---

### Post by wilee-nilee on 2010-09-16
> **kansasnoob said:**
> Glad we can at least crank down the urgency :D

I know what it's like to be stuck absolutely "needing" to get something done. Scary stuff! And it does little good to kick ones own rear end after jumping into something at the wrong moment.

I wonder if as I have seen on very rare occasions that grub just needs to be loaded again and the partition mounted in the usual way from the live cd. Of course I defer to you in this area.

Also I wonder if this is a Dell computer, the usual thing that happens with the Dell data Safe is giving MS the boot back though.

---

### Post by arpanaut on 2010-09-16
> p/s sorry about my redicolous typos, this keyboard is messed up and doesnt register all the keystrokes all the time

This could very much be the issue.
Have you tried cleaning out your keyboard with compresses air, or turning upside-down and shaking and slapping the back.
Check the connections, try another keyboard.

This is strange behavior I do not recall seeing before.

---

### Post by kansasnoob on 2010-09-16
Hmmm, given the keyboard behavior maybe we're blaming grub when we should be looking at either hardware or "hardware management" by the OS :confused:

I'm grabbing at straws but I do try to follow grub2 development pretty darn close and I just haven't seen this before.

---

### Post by kansasnoob on 2010-09-16
> **arpanaut said:**
> This could very much be the issue.
Have you tried cleaning out your keyboard with compresses air, or turning upside-down and shaking and slapping the back.
Check the connections, try another keyboard.

This is strange behavior I do not recall seeing before.

Sorry, should have begun with a +1 to you!

I've tried duplicating this behavior with a Maverick that was installed during Beta iso-testing and can't.

I can only imagine that the machine is recognizing "arrow-up-down" as enter/return. So I guess we need to know language, keyboard layout, whether the keyboard is PS2 or USB, etc.

Does the OP have another keyboard available?

Or is this a lappy w/onboard keyboard?

---

### Post by wilee-nilee on 2010-09-16
> **kansasnoob said:**
> Hmmm, given the keyboard behavior maybe we're blaming grub when we should be looking at either hardware or "hardware management" by the OS :confused:

I'm grabbing at straws but I do try to follow grub2 development pretty darn close and I just haven't seen this before.

I wondered about the keyboard as well, but I missed the quote, being that we posted at the same minute, and I didn't look closer.

---

