---
title: "libdvdread: Error cracking CSS key"
date: 2008-11-02
forum: Multimedia Software
---

### Post by kikazaru on 2008-11-02
Forgive me if the solution is already to be found in the forum, but nothing I've found has worked. I've been trawling and testing for the best part of two days. Any help very much appreciated!

I can't play DVDs from the "wrong" region. 

Drive settings:

```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE
Would you like to change the region setting of your drive? [y/n]:n

```

vlc errors:

```

[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: FUTURAMA_SEASON_2_DISC_1
libdvdnav: DVD Serial Number: 2D105B7D
libdvdnav: DVD Title (Alternative): FUTURAMA_SEASON_2_DISC_1
libdvdnav: Unable to find map file '/home/josh/.dvdnav/FUTURAMA_SEASON_2_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000130)
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: FUTURAMA_SEASON_2_DISC_1
libdvdnav: DVD Serial Number: 2D105B7D
libdvdnav: DVD Title (Alternative): FUTURAMA_SEASON_2_DISC_1
libdvdnav: Unable to find map file '/home/josh/.dvdnav/FUTURAMA_SEASON_2_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000130)
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 

```

Various installed packages:

```

ii  dvd+rw-tools                              7.1-2ubuntu1                          DVD+-RW/R tools
ii  dvd95                                     1.3p2-0ubuntu1                        DVD9 to DVD5 converter
ii  dvdauthor                                 0.6.14-3                              create DVD-Video file system
ii  libdvdcss2                                1.2.10-0.2medibuntu1                  Simple foundation for reading DVDs - runtime libraries
ii  libdvdnav4                                4.1.2-3                               DVD navigation library
ii  libdvdread3                               0.9.7-11ubuntu2                       library for reading DVDs
ii  lsdvd                                     0.16-3                                read the content info of a DVD
ii  libvlc2                                   0.9.4-1ubuntu3                        multimedia player and streamer library
ii  libvlccore0                               0.9.4-1ubuntu3                        multimedia player and streamer library
ii  vlc                                       0.9.4-1ubuntu3                        multimedia player and streamer
ii  vlc-data                                  0.9.4-1ubuntu3                        Common data for VLC
ii  vlc-nox                                   0.9.4-1ubuntu3                        multimedia player and streamer (without X support)
ii  kubuntu-restricted-extras                 25                                    Commonly used restricted packages
ii  linux-restricted-modules                  2.6.27.7.11                           Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12                           Non-free Linux kernel modules for version 2.6.27 on x86/
ii  linux-restricted-modules-common           2.6.27-7.12                           Non-free Linux 2.6.27 modules helper script
ii  linux-restricted-modules-generic          2.6.27.7.11                           Restricted Linux modules for generic kernels
ii  ubuntu-restricted-extras                  25                                    Commonly used restricted packages

```

8.10 Intrepid Ibex
Lenovo T400 with "DVD MULTI Recorder Blu-Ray Disc"

I can play DVDs from the "right" region, but I have this problem for different regions, regardless of whether I'm using vlc, mplayer, xine, etc.

---

### Post by mc4man on 2008-11-02
It sounds like your dvd drive is enforcing region coding, in other words when a region mismatch is encountered it will not allow access to encrypted sectors.

This behavior is usually only found on drives manufactured by matshita, though maybe also being a blu-ray drive is related. (a lot of laptop drives are mashita's

run sudo lshw -C disk to see make, model

If it is locking the disc then there is very little you can do about it, only a hacked firmware will solve.

If it's not locking access then there are some scenarios where open source players can't crack the keys when there is a region mismatch. (structure protection related

In those cases acquiring and placing the proper keys in the .dvdcss folder will solve (basically using another drive set to proper region to get the keys and copying the associated folder in .dvdcss, or having someone with exact same title do so for you

---

### Post by kikazaru on 2008-11-02
Thanks for the reply. I didn't know how to check the type of my drive, but it turns out it is a Matsushita. 

Allow me to proclaim: Matsushita suck big time!

I guess this is a fairly new device so there probably isn't any hacked firmware available yet...

There you have the offending article:

```

  *-cdrom
       description: DVD-RAM writer
       product: BD-MLT UJ232A
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: TC02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

```

---

### Post by mc4man on 2008-11-02
I've got one on a laptop myself, I'm hoping the drive dies before the warranty expires (3 yrs. so I got a shot)

You can always ck on this site but rpc1 firmware for laptop drives is rarely available

That why i call them matSHITa drives

[http://forum.rpc1.org/portal.php](http://forum.rpc1.org/portal.php)

---

### Post by kikazaru on 2008-11-02
Yup, it really is a crock isn't it...

I wonder if you can buy this drive in Australia or New Zealand where it's apparently illegal to enforce this region coding nonsense. It sounds too easy to imagine that there would be a legitimate firmware update for these regions available...

---

### Post by unixel on 2009-12-25
For those that are interested. Care of [http://blog.moybella.net/2007/03/25/setting-the-region-of-you-dvd-in-ubuntu/](http://blog.moybella.net/2007/03/25/setting-the-region-of-you-dvd-in-ubuntu/)

apt-get install regionset

run regionset as root, select the region you would like your DVD to be. 

Solved my Creative DVD doing this.

---

### Post by kikazaru on 2010-01-08
I think this drive only allows a limited number of changes -about four, so it's not a viable solution to change every time you want to read a different region. I set mine to 2 in the end, since I am in Japan and have a lot of British DVDs (both region 2).

My conclusion (based on mc4man's comments) the last time I looked at this was that unless someone hacks the firmware for this drive, there's nothing I can do about it...

A quick check on the firmware site reveals that there is still nothing for my drive... 

************************************
Remember: avoid MATSHITA / Panasonic
************************************

---

