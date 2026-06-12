---
title: "Can't play DVDs"
date: 2008-09-17
forum: Multimedia Software
---

### Post by George_ on 2008-09-17
Hi guys, I can't seem to play any encrypted DVDs. I run Ubuntu Hardy.

VLC just crashes. So does Ogle. MPlayer just freezes. Totem freezes up for a while, then says "Can not read from resource". GNOME MPlayer freezes, and comes up with "Fatal Error".

I've installed libdvdcss2 in Synaptic, but it doesn't seem to have done anything.

So, what do I do?

Thanks

George

---

### Post by tuxxy on 2008-09-17
**ubuntu-restricted-extras** package should provide DVD playback, specifically the libdvdcss2 and w32codecs packages.

---

### Post by mc4man on 2008-09-17
Another thing you should ck is whether a region has been set on the dvd drive. It only has to be set *once*

Instructions on regionset here (post 5

[http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset](http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset)

```
sudo apt-get install regionset
```

---

### Post by jonathan.david.lim on 2008-09-17
I'm having the exact same problem. As for me, ubuntu-restricted-extras is installed on my system. Should I try reinstalling that package? Also, regionset shows I've got it set for Region 1, which is exactly what I want. So I don't know what the problem is.

I got it to work on Gutsy at some point, but I don't remember how. I just remember using Kaffeine to play all my DVDs instead of Totem, but now even Kaffeine won't work. I don't understand what's going on; I just want to watch movies.

---

### Post by George_ on 2008-09-17
I read it, and I have one question. What's the mask?

```
regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 4, mask=0xF7

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:3
New mask: 0xFFFFFFFB, correct? [y/n]:

```

---

### Post by mc4man on 2008-09-17
you can usually get some good info by opening vlc from a terminal and then going file -> open disc. Post what the ternimal output is.

@ George 
> I read it, and I have one question. What's the mask?
The mask is just the region setting. I hope you read carefully because yours is already set, **don't change it** 

It only has to be set once for playback of most titles whether there is a region match between drive and title or not.

There are some rare exceptions and also Matshita laptop dvd drives will only allow playback when the region of the title and drive match.

Other than that open source players don't enforce region coding so leave the region setting alone once set.

---

### Post by George_ on 2008-09-17
Ok: this is what I get from a terminal with VLC on an encrypted DVD:

```

starting VLC root wrapper... using UID 1000 (george)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSlibdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdnav: vm: faild to open/read the DVD
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat media
No such file or directory
[00000292] main input error: no suitable access module for `media'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdnav: vm: faild to open/read the DVD
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat player
No such file or directory
[00000306] main input error: no suitable access module for `player'
[00000283] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: vm: faild to open/read the DVD
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
[00000311] dvdread demuxer error: DVDRead cannot open source: /dev/scd0

```

So...what does all this mean, exactly?

---

### Post by ad_267 on 2008-09-17
This is what I did to play dvds:

```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by George_ on 2008-09-17
I tried that...doesn't work. The media players still do the same thing...maybe that might be because the computer doesn't actually realize the disc's there? Cause when I go to Places -> Computer -> CD - RW/DVD +- RW Drive, it says there's no media in the drive. Yet when I put in a DVD I've made myself, it works fine.

---

### Post by jonathan.david.lim on 2008-09-17
George, are you getting a little DVD icon to show up on your desktop? I am, so to me that means my DVD drive recognizes there's a DVD in there. Also, using VLC and other programs, whenever I 'Open Disc' the title of the film shows up in the location bar (e.g. THE_COTTAGE). So it knows it's there, it just won't read it for some reason.

---

### Post by George_ on 2008-09-18
No, I don't get that. For some reason it doesn't mount when I put it in (but it mounts a non-encrypted dvd) :confused:...

---

### Post by kno712 on 2008-09-18
I have the same problem. When run from the command line, I've got error messages like this: 

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


Not long ago, everything was working perfectly.

---

### Post by chorca on 2009-01-01
Same thing for me. Have all the restricted-extras installed, and I'm getting the same issue with a Palm Pictures DVD I'm trying to play.

The errors happen in both VLC and GStreamer, so it's something to do with libdvdread or something..

VLC:
```
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: MICHEL_GONDRY_SIDE_A
libdvdnav: DVD Serial Number: c3218e06        
libdvdnav: DVD Title (Alternative): MICHEL_GONDRY_SIDE_A
libdvdnav: Unable to find map file '/home/chris/.dvdnav/MICHEL_GONDRY_SIDE_A.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
*** Zero check failed in ifo_read.c:1760
    for pgcit->zero_1 = 0xfbb7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1764 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xe092

*** libdvdread: CHECK_VALUE failed in ifo_read.c:766 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:784 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:786 ***
*** for pgc->cell_position_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:714 ***
*** for cell_playback[i].first_sector <= cell_playback[i].last_vobu_start_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:712 ***
*** for cell_playback[i].last_vobu_start_sector <= cell_playback[i].last_sector ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0x8893

*** libdvdread: CHECK_VALUE failed in ifo_read.c:766 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:784 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:785 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:786 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0x6893

*** libdvdread: CHECK_VALUE failed in ifo_read.c:766 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:784 ***
*** for pgc->program_map_offset != 0 ***

libdvdnav: ifoRead_PGCIT failed

```

GStreamer (Totem)
```
chris@latitude:~$ totem
** (totem:14748): DEBUG: Init of Python module
** (totem:14748): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:14748): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:14748): DEBUG: Creating Python plugin instance
** (totem:14748): DEBUG: Init of Python module
** (totem:14748): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:14748): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:14748): DEBUG: Creating Python plugin instance
*** Zero check failed in ifo_read.c:1365
    for vts_tmapt->zero_1 = 0x2236
*** Zero check failed in ifo_read.c:1539
    for c_adt->zero_1 = 0xaa00

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***

```

---

