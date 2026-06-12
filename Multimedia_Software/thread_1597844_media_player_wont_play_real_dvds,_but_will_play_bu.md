---
title: "media player wont play real dvds, but will play burned."
date: 2010-10-15
forum: Multimedia Software
---

### Post by gibz117 on 2010-10-15
i just installed 10.10 on my girls laptop (Acer Aspire 5735z) hoping it would fix the old problem i had with playing real dvd's.  it didnt.  it keeps saying "Could not read from Resource".  when i try with VLC is say "Could not read from file".  but if i put in a burned movie, it plays fine.  i checked and it has libdvdcss2, libdvdnav4, and libdvdread4 installed.  i get the same problems with my laptop (toshiba portege m400 tablet) which runs fedora 13.

---

### Post by mc4man on 2010-10-15
It may prove useful to identify the drive (looking for matshita 

in a terminal
```
sudo lshw -C disk
```

just the *-cdrom info

---

### Post by gibz117 on 2010-10-15
description: dvd-ram writer
prouduct: dvdrw ad-7580S
vendor: optiarc.

---

### Post by mc4man on 2010-10-15
> optiarc
Not sure if they absolutely need the region set like matshita (and possibly already done

For starters put a dvd in the drive, close out any player or popup. Then open the home folder - View -> 'Show hidden files'
Scroll down, find the .dvdcss folder and delete it.

Open a terminal and run
```
 vlc dvd://
```
Post the terminal output

---

### Post by gibz117 on 2010-10-24
here is what i get.  i dont undertand any of it.

vlc dvd://
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x93a68fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb748b0c4, 0xb748b038)
Warning: call to signal(13, 0x1)
Warning: call to srand(1288565029)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3788): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
libdvdnav: Using dvdnav version 4.1.4
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BUTTERFLY_EFFECT
libdvdnav: DVD Serial Number: 307b06e4
libdvdnav: DVD Title (Alternative): BUTTERFLY_EFFECT
libdvdnav: Unable to find map file '/home/Gibz/.dvdnav/BUTTERFLY_EFFECT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
Warning: call to srand(902340)
Warning: call to rand()
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libdvdnav: Using dvdnav version 4.1.4
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BUTTERFLY_EFFECT
libdvdnav: DVD Serial Number: 307b06e4
libdvdnav: DVD Title (Alternative): BUTTERFLY_EFFECT
libdvdnav: Unable to find map file '/home/Gibz/.dvdnav/BUTTERFLY_EFFECT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
Warning: call to srand(889514)

[s]the two smilies are supposed to be an 8 with ) after it.[/s]

---

### Post by sir4taye on 2010-10-24
> **mc4man said:**
> Not sure if they absolutely need the region set like matshita (and possibly already done

For starters put a dvd in the drive, close out any player or popup. Then open the home folder - View -> 'Show hidden files'
Scroll down, find the .dvdcss folder and delete it.

Open a terminal and run
```
 vlc dvd://
```
Post the terminal output

I followed these directions cause my DVD rom doesn't recognize even having dvd's in the drive. I just used it to install 10.10 so the drive works for reading and writing cd's


home@BigBox-Neighbor:~$ vlc dvd://
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xbd5120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f85afd85b20, 0x7f85afd85a80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1287943918)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2582): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/dvd for reading
[0x124f420] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0x7f85a0000aa0] main input error: open of `dvd://' failed: (null)

This is the drive with a dvd in it.

home@BigBox-Neighbor:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD reader
       product: RW/DVD GCC-4482B
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

---

