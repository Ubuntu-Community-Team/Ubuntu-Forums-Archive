---
title: "DVD's burn, but fail to mount only on ubuntu."
date: 2008-10-19
forum: Multimedia Software
---

### Post by liquidgecka on 2008-10-19
I have run into a strange problem with Ubuntu since I reinstalled to 8.04.1. After burning a DVD image using several command line utilities the image is unmountable in Ubuntu, but works fine in Mac OS.

I am using the exact same script to burn the image as I used on my previous machine (a MythBuntu install running 8.04 as well). The disks produced earlier all still work. The disks burned with the modern system all fail to mount on my linux machine, but mount without problems on my Mac.

Anybody have any idea what I am doing wrong here or what I can try in order to find out what is broken? I am at a loss.

So far I have tried every combination of mkisofs, genisoimage, and dvdrecord and wodim with the same results every time.

I tried pure mkisofs as well as genisoimage due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942)

Commands used to burn:
# sudo dvdrecord -eject -dao dev=/dev/cdrom D5-15.iso
# sudo wodim -dao dev=/dev/cdrom D5-15.iso

Commands used to make the image:
/usr/bin/mkisofs -J -r -V D5-15 -o ../D5-15.iso .
/usr/local/bin/mkisofs -J -r -V D5-15 -o ../D5-15.iso .

Where:
$ /usr/bin/mkisofs --version
mkisofs 2.01 is not what you see here. This line is only a fake for too clever
GUIs and other frontend applications. In fact, this program is:
genisoimage 1.1.6 (Linux)
$ /usr/local/bin/mkisofs --version
mkisofs 2.01.01a33 (x86_64-unknown-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2007 J?rg Schilling


# isoinfo -d dev=/dev/cdrom
CD-ROM is in ISO 9660 format
System id: LINUX
Volume id: D5-15
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 2181761
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found

$ sudo mount /dev/cdrom /media/cdrom -t iso9660
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[233466.204367] sr0: rw=0, want=1252, limit=4
[233466.204371] attempt to access beyond end of device
[233466.204373] sr0: rw=0, want=1028, limit=4
[233466.204376] UDF-fs: No partition found (1)
[233466.213812] attempt to access beyond end of device
[233466.213816] sr0: rw=0, want=68, limit=4
[233466.213819] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[233472.330976] attempt to access beyond end of device
[233472.330982] sr0: rw=0, want=68, limit=4
[233472.330985] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

---

