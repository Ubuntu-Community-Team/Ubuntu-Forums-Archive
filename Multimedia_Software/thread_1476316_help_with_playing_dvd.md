---
title: "help with playing dvd"
date: 2010-05-07
forum: Multimedia Software
---

### Post by Thestinger on 2010-05-07
I am quite new to Ubuntu, I installed 9.10 and managed to get it to play DVDs eventually after following the various tutorials on the forums.

I upgraded to 10.04 and can now no longer play encrypted DVDs, I have VLC and totem and on both they don't appear to even see the DVD let alone play it.

I have installed all the mediabuntu packages and followed the instructions on restricted formats. 

Does anyone have any ideas

I jave hopefully attached a screen shot of what happens when I try to play a DVD

System- AMD64 3400,  1.5 GB ram, incredibly rubbish SIS graphics
[IMG]file:///home/paul/Desktop/Screenshot.png[/IMG]/home/paul/Desktop/Screenshot.png
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Thestinger on 2010-05-08
Well I had another look on the forums and tried a few other things, I attempted to get rid of VLC and then re-install it and  that didn't work.

I have uninstalled and then re installed all the libdvd stuff.

I keep getting this error message

 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]


any ideas

---

### Post by mykei on 2010-05-08
I also have problems playing DVDs with ubuntu 10.04LTS 64BIT, appears the error that the device cannot be openned or i don't have permission to read it.
This happens with any movie player or DVD ripping program.
&#296;f i copy the dvd  files to my hardrive, it works!

---

### Post by Thestinger on 2010-05-08
The player will play dvds in windows and it will play and burn CDs on Ubuntu. It just doesn't see any DVD movies.

When I look on the disc utility, it sees that there is a DVD drive but doesn't see the dvd that I have inserted I have tried a number of DVDs now to make sure it wasn't a damaged one

It is really annoying as other than this issue I am really liking Ubuntu

---

### Post by TopEnder on 2010-05-08
Hi, do a Forum search for: [COLOR="Blue"]Comprehensive Multimedia & Video Howto[/COLOR] I think it might be what you are looking for to solve your problem

---

### Post by Thestinger on 2010-05-08
I have looked and looked through the forums, most solutions involve installing all teh restricted extras and libdvd stuff. I have done all that and it just won't accept there is a DVD in the blasted player

---

### Post by xc3RnbFO8P on 2010-05-08
Try this:
> vlc --reset-plugins-cache

---

### Post by mc4man on 2010-05-08
Could you run this in a terminal and post
```
cat /etc/fstab
```

and with a *dvd in the drive* this - post what's in the *-cdrom entry

```
sudo lshw -C disk
```

---

### Post by frogotronic on 2010-05-08
> **Thestinger said:**
> I am quite new to Ubuntu, I installed 9.10 and managed to get it to play DVDs eventually after following the various tutorials on the forums.

I upgraded to 10.04 and can now no longer play encrypted DVDs, I have VLC and totem and on both they don't appear to even see the DVD let alone play it.

I have installed all the mediabuntu packages and followed the instructions on restricted formats. 

Does anyone have any ideas

I jave hopefully attached a screen shot of what happens when I try to play a DVD

System- AMD64 3400,  1.5 GB ram, incredibly rubbish SIS graphics
[IMG]file:///home/paul/Desktop/Screenshot.png[/IMG]/home/paul/Desktop/Screenshot.png
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

Each time you upgrade a distribution (ie 9.10 -> 10.04) you need to re-install/activate the medibuntu repos.

Follow this guide : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Install the following:

```
sudo apt-get install libdvdcss2 non-free-codecs w32codecs libdvdread4
```

You should be good to go...

- CH

---

### Post by Thestinger on 2010-05-08
no that didn't work[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

I got this

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0xa2e4600] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xa2e4600] main access error: no access module matched "dvd"
[0xa2df188] main input error: open of `dvd:///dev/sr0' failed: no access module matched "dvd"

---

### Post by Thestinger on 2010-05-08
> **mc4man said:**
> Could you run this in a terminal and post
```
cat /etc/fstab
```

and with a *dvd in the drive* this - post what's in the *-cdrom entry

```
sudo lshw -C disk
```
For the 1st bit I got this

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9d1407e8-08bf-4976-970e-469f6ce4e166 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=11c6f4d5-1d6d-4fd5-a571-3c3ad0a1711a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Then for 2nd bit I got this

*-disk                  
       description: ATA Disk
       product: SAMSUNG SP1604N
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: TM10
       serial: S013J10Y237732
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4fb7d6d5
  *-cdrom
       description: DVD writer
       product: DVDRW SOHW-1633S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BPSA
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde

---

### Post by Thestinger on 2010-05-08
Just a quick thought

I upgraded from 9.10 rather than a fresh install, would it be worth installing fresh

---

### Post by mc4man on 2010-05-08
> I upgraded from 9.10 rather than a fresh install, would it be worth installing fresh

Possibly.

One  difference in lucid is there are no longer fstab entries for cd/dvd drives. But when you update they are retained and usually don't cause an issue.

From what you posted everything seems ok there as long as the  /media/cdrom0 directory exists.
(I'm assuming it does because you'd get a pop up error when inserting disk if it didn't.

If, when you ran the lshw you had a dvd in the drive as asked then this is the concern
> configuration: ansiversion=5 status=[COLOR="Red"]nodisc[/COLOR]

If the filesystem on the disk (UDF) is not found then there is nothing to mount and playback.

Did you have a dvd in the drive?

If so then there is a possibility that a fresh install will resolve, but then again it may not.

Before doing a fresh install I'd...
make sure /media/cdrom0 exists
run the lshw with a disk in if you hadn't before.

Try commenting out the fstab entry for the drive and rebooting
```
#/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0

```
Try booting up with a dvd in the drive.

---

### Post by Thestinger on 2010-05-08
Well I tired that- or I think I did, I opened a terminal and entered the code you said and then restarted with a DVD in.

Nothing happened.

I am going to try a fresh install

Thanks for the help

---

### Post by Thestinger on 2010-05-08
well that's annoying[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

I have re -installed and it is doing exactly the same

---

### Post by haircat on 2010-12-05
Haircat-Thanks for all the help Movie Player now playing all dvds

---

