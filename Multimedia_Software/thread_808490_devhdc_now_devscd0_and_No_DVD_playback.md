---
title: "/dev/hdc now /dev/scd0 and No DVD playback"
date: 2008-05-26
forum: Multimedia Software
---

### Post by coolaj86 on 2008-05-26
[SOLVED] see post below

On a particular system a fresh install of Hardy Heron and now the dvd and dvdrw drives link to /dev/scd0 and /dev/scd1 rather than /dev/hdc and /dev/hdd like they used to.

The system in question has the restricted packages installed. Data DVDs will mount and read fine, however, movies won't play.

vlc reports
```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: LOVEBUG_US
libdvdnav: DVD Serial Number: 304606c6
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/user/.dvdnav/LOVEBUG_US.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

```

totem reports
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***

```

---

### Post by mc4man on 2008-05-26
Go here and add medibuntu to your sources, then install libdvdcss2 and you should be good [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by coolaj86 on 2008-05-30
Solution:
```
wget http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb
sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Problem:
Even though I got a message something like "Cannot play the requested media though the correct plugin is installed"... it was wrong.

Apparently libdvdcss2 has been taken out of the restricted extras package. LAME! (and that's no reference to the mp3 encoder). Stupid copyright issues... You know, I would be willing to pay $15 to buy all of those stupid codecs and whatnot if someone would make them commercially available in a .deb.

```
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

---

### Post by skralljt on 2008-06-05
I have enabled the medibuntu sources and all of that and installed all the libdvdcss's and whatnot, but still can't watch a dvd.  When I open a disc in vlc it spits out lots of errors about not being able to read it and then starts playing the dvd as an audio cd!  All kinds of terrible squeaks emanate from my computer.

---

