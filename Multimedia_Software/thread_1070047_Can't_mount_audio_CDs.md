---
title: "Can't mount audio CDs"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Number13 on 2009-02-14
I have a ide dvd and i can't seem to mount audio CDs. DVDs mount and play fine. I can read data CDs but they won't mount either.

I have searched but nothing has worked.

Anyone have any suggestions?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=948d8070-f02b-4e09-b509-bb24fb95cf2a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=676bb815-fbcc-4a2e-99fb-8eb44cb383fa /home           ext3    relatime        0       2
# /dev/sda5
UUID=474c903a-d043-a2b0-e2e4-100e8b05a4fa none            swap    sw              0       0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```


```
@Linux:~$ sudo mount /dev/scd0
[mntent]: warning: no final newline at the end of /etc/fstab
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
@Linux:~$ dmesg | tail
[ 1702.088494] end_request: I/O error, dev sr0, sector 1193288
[ 1702.089506] end_request: I/O error, dev sr0, sector 1194528
[ 1702.090518] end_request: I/O error, dev sr0, sector 1193280
[ 1702.091691] end_request: I/O error, dev sr0, sector 1248
[ 1702.092860] end_request: I/O error, dev sr0, sector 2496
[ 1702.094032] end_request: I/O error, dev sr0, sector 1248
[ 1702.095204] end_request: I/O error, dev sr0, sector 2496
[ 1702.095296] UDF-fs: No partition found (1)
[ 1702.165759] end_request: I/O error, dev sr0, sector 64
[ 1702.165859] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```

---

### Post by mc4man on 2009-02-14
> i can't seem to mount audio CDs.
Audio cd's don't 'mount', there is no file system to mount.

Put one in and the go to home folder (view -> show hidden files if not enabled) -> .gvfs and look inside for 'cdda mount on scd0'

> I can read data CDs but they won't mount either.


If you can read them they're mounted somewhere, put one in and look in places -> computer -> filesystem -> media

> [mntent]: warning: no final newline at the end of /etc/fstab

Run this in a terminal
```
gksudo gedit /etc/fstab
```

Put your cursor on the end of this line
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

And then press enter on your keyboard and save (create a new empty line.


Why don't you put a data cd or a dvd in the drive, run this and post

```
sudo lshw -C disk
```

---

### Post by Number13 on 2009-02-14
When I say "mount" i mean when I insert a DVD i get a desktop icon and it lauches media player and plays. When I insert a CD my media player (rhythmbox) launches and it wont play and there is nothing to play and no desktop icon.

.gvfs is empty

I have added an empty line to fstab

```
@Linux:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk
       description: ATA Disk
       product: Hitachi HDP72505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: GM4O
       serial: GEA532RF1MDMXA
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00071d50
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=00079f59
```

---

### Post by Number13 on 2009-02-14
This is with an audio CD 

```
@Linux:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: Hitachi HDP72505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: GM4O
       serial: GEA532RF1MDMXA
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00071d50
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=00079f59
```

---

### Post by mc4man on 2009-02-14
My second reading mistake of the day, didn't see 'xubuntu'

I'm not sure what the location of the audio cd files is in xubuntu (not .gvfs)

The lshw line does indicate that media has been found

> configuration: ansiversion=5 status=[COLOR="Red"]ready[/COLOR]

If nobody who knows xubuntu can help, check back in an hr. or two, I'll take a look in a tester.

(are you using 8.10 or 8.04? Edit: never mind, looks like 8.10 from prior posts

---

### Post by Number13 on 2009-02-14
yes, xubuntu 8.10
I should mention that this is a fresh install on a brand new mobo.


In Rhythmbox; Music > Import File
I get an error message:

> The folder contents could not be displayed
The specified location is not mounted

click 'ok'
click 'audio cd' (from thunar)

The audio CD shows up in Rhythmbox and I can play it.

However it is still not 'mounted'

/media/cdrom is empty

```
@Linux:~$ sudo lshw -C disk 
  *-cdrom                 
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: Hitachi HDP72505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: GM4O
       serial: GEA532RF1MDMXA
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00071d50
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=00079f59
```

---

### Post by djbushido on 2009-02-14
my Xubuntu recognizes audio disks just fine. 
Do this once the cd has been put in and left for ~30 secs:
```
sudo fdisk -l
``` where the "-l" is a lowercase "L".
Also, try to install sound juicer with
```
sudo apt-get install sound-juicer
```this will create a menu entry for "Audio CD Extractor", which is sound-juicer. This should recognize cd's just fine, and you can rip them then. I don't know why you can't access the cd itself (I'm pretty sure that they can actually be mounted - otherwise system would have to use block device), but post back if these don't work.

---

### Post by mc4man on 2009-02-14
Just got it loaded (bit of 'culture shock' compared to ubuntu/gnome/nautilus

First impression

the cd icon doesn't show on desktop 
The listen player finds audio cd fine

At first rhythmbox failed to find nor showed any devices, after doing the same as you, now when I open rhythmbox  it does have 'Devices' entry on left side. (and shows the cd name
It appears you need to do that every time an audio cd is inserted (with rhythmbox


On the other hand Amarok has no problems finding the cd, will work as the default audio cd player (insert a disk, amarok will start up, load contents and start playback, you don't need to do anything
 Let me know if you want to set amarok up (for default auto play


> However it is still not 'mounted'

Never will be (audio cd's are never mounted, they're accessed at a location

Where the location is not sure, got to go get dinner, am going to fool around with this later

---

### Post by Number13 on 2009-02-15
sound juicer is already installed and it works just fine.

> Never will be (audio cd's are never mounted, they're accessed at a location

Where the location is not sure, got to go get dinner, am going to fool around with this later

but i still get an error msg when i try to play audio CDs with Rhythmbox. I get no desktop icon and they don't show up in Thunar.

DVDs show up in Thunar. I get a desktop icon. And they show up as mounted.

DVDs
```
configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
```

CDs
```
configuration: ansiversion=5 status=ready
```

I can work around this but I'm just wondering if there is a fix?

What does sudo lshw -C disk report with an Audio CD & Ubuntu?


Thanks for the help so far!

---

### Post by mark.donaldson4 on 2009-10-10
Has anyone solved this yet? I'm using 9.04 and I am having the exact same problem as Number 13 below.  I can listen to Audio CD's but there is no icon on the desktop or in Thunar, and has to be manually started from the music player I am using (Exaile).

Cheers

---

### Post by mpnordland on 2010-06-23
never mind, the fix i posted, it actually isn't a fix , after trying it on my xubuntu laptop, data cd's showed up in the usual manner, which wasn't working, but removing the "noauto" causes non-fatal mount errors at boot. so if anyone did what i had, change it back to what it was before, and all will return to normal.

---

