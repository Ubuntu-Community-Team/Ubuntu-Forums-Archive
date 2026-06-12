---
title: "hardy will not play encrypted DVDs"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Steve1961 on 2008-08-01
I have a thinkpad R50e that's been running Dapper for the last two years and I've just done a clean upgrade to Hardy.  Problem is, it wont play encrypted DVDs in Hardy when it worked fine in Dapper.

The laptp has an IDE disk which Hardy identifies as /dev/scd0.  libdvdcss is installed and so are w32 codecs, all the gstreamer stuff, and I've linked /dev/dvd, /dev/dvd1, /dev/dvdrw, /dev/cdrom0, /dev/cdrom1 to /dev/scd0.  I've also set all the permissions to 777.

I've tried vlc, mplayer, xine, smplayer, and kaffeine and nothing works.  VLC crashes when trying to play the DVD, Kaffeine complains about a problem accessing the disk and not being able to determine DMA mode, and xine complains there's no input plugin.

Unencrypted discs play fine, and discs mount and I can view the files and folders.  I cant find a way to set the DMA mode in Hardy though.

Any ideas much appreciated.  This is the laptop my wife uses, largely for watching her DVDs, and after spending many months persuading her to upgrade to Hardy I really need this to work.

---

### Post by mc4man on 2008-08-01
Why don't you put a dvd movie in the drive and run this to ck. device, links,  mount, ect.
```
sudo lshw -C disk
``` Also open vlc from the terminal, try to play a disk and ck. the output.

> I've linked /dev/dvd, /dev/dvd1, /dev/dvdrw, /dev/cdrom0, /dev/cdrom1 to /dev/scd0. I've also set all the permissions to 777.
 probably unnecessary, with one drive you only need, want 1 set of links (preferably /dev/dvd, dev/cdrom, /dev/cdrw. dev/dvdrw, /dev/sr0 )

you could run this to ck. what is assigned to drive (easier to read from maximized terminal)

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by jualin on 2008-08-01
*deleted post*

---

### Post by racoq on 2008-08-01
Open the console and try:

sudo /usr/share/doc/libdvdread3/install-css.sh

That hopefully will do the trick on playing encrypted DVD's

This will install libdvdcss2

---

### Post by Steve1961 on 2008-08-02
> **racoq said:**
> Open the console and try:

sudo /usr/share/doc/libdvdread3/install-css.sh

That hopefully will do the trick on playing encrypted DVD's

This will install libdvdcss2


This was one of the first things I tried.  It just downgraded the medibuntu libdvdcss2 to an earlier version.  This made no difference I'm afraid, so I upgraded to the medibuntu version again

---

### Post by Steve1961 on 2008-08-02
> **mc4man said:**
> Why don't you put a dvd movie in the drive and run this to ck. device, links,  mount, ect.
```
sudo lshw -C disk
``` Also open vlc from the terminal, try to play a disk and ck. the output.

 probably unnecessary, with one drive you only need, want 1 set of links (preferably /dev/dvd, dev/cdrom, /dev/cdrw. dev/dvdrw, /dev/sr0 )

you could run this to ck. what is assigned to drive (easier to read from maximized terminal)

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

OK, here's the output of sudo lshw -C disk
```

*-disk                  
       description: ATA Disk
       product: HTS541060G9AT00
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MB3I
       serial: MPB3LAXGHJYBJM
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cccdcccd
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-830Sx
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime

```

and cat /etc/udev/rules.d/70-persistent-cd.rules
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD-RAM_UJ-830Sx (pci-0000:00:1f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

```

---

### Post by dentaku65 on 2008-08-02
Can be a problem of some old config file; try to clean those files:
```
mv ~/.dvdcss ~/.dvdcss.ORIGINAL

```
then insert the dvd and try to play it.

---

### Post by Steve1961 on 2008-08-02
> **dentaku65 said:**
> Can be a problem of some old config file; try to clean those files:
```
mv ~/.dvdcss ~/.dvdcss.ORIGINAL

```
then insert the dvd and try to play it.

That did the trick.  Thanks very much.

---

