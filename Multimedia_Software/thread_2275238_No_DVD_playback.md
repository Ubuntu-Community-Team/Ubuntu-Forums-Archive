---
title: "No DVD playback"
date: 2015-04-25
forum: Multimedia Software
---

### Post by chris352 on 2015-04-25
I've installed all the extras and followed all the usual instructions, but I still can't get my DVDs to play. Things worked perfectly well with 12.04, but since I upgraded to 14.04, the only message I get is "DVD cannot be read". Can I get a little help here?

EDIT:

Here's the readout when I open it with VLC:
```
$ vlc /dev/sr0
VLC media player 2.1.6 Rincewind (revision 2.1.6-0-gea01d28)
[0xb74118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.1
libdvdnav: DVD Title: HARRY_POTTER_SORCERERS_STONE
libdvdnav: DVD Serial Number: 3716B143
libdvdnav: DVD Title (Alternative): HARRY_POTTER_SORCERERS_STONE
libdvdnav: Unable to find map file '/home/<user>/.dvdnav/HARRY_POTTER_SORCERERS_STONE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0x7f83f40009b8] main input error: ES_OUT_RESET_PCR called

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00028052
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00028052)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00031c8e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00031c8e)!!
libdvdread: Elapsed time 1
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 1
[0x7f83f40009b8] main input error: ES_OUT_RESET_PCR called
[0x7f83f40009b8] main input error: ES_OUT_RESET_PCR called
[0x7f83f40009b8] main input error: ES_OUT_RESET_PCR called
```

And here's what Totem reports:
```
$ totem /dev/sr0

** (totem:15742): CRITICAL **: bacon_video_widget_has_previous_track: assertion 'BACON_IS_VIDEO_WIDGET (bvw)' failed

** (totem:15742): CRITICAL **: bacon_video_widget_has_next_track: assertion 'BACON_IS_VIDEO_WIDGET (bvw)' failed
libdvdread: Attempting to use device /dev/sr0 mounted on /media/<user>/HARRY_POTTER_SORCERERS_STONE for CSS authentication
libdvdnav: Using dvdnav version 4.2.1
libdvdread: Attempting to use device /dev/sr0 mounted on /media/<user>/HARRY_POTTER_SORCERERS_STONE for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/<user>/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00028052
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00028052)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00031c8e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00031c8e)!!
libdvdread: Elapsed time 1
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 2

```

---

### Post by mc4man on 2015-04-25
I'm heading out so can't hang but maybe try what's in this post, make sure to delete .dvdcss folder
[http://ubuntuforums.org/showthread.php?t=1440147&p=9037249&viewfull=1#post9037249](http://ubuntuforums.org/showthread.php?t=1440147&p=9037249&viewfull=1#post9037249)
(- also 1st re-install libdvdcss2 with this, then try from above link
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by chris352 on 2015-04-25
Thanks for the suggestion. Turns out the problem was that my laptop's CD-ROM needed to have its region setting fixed. I had tried over and over again to use regionset to do it, but kept getting an error saying that it couldn't read the drive. I finally found the needle in the haystack with this solution: [http://askubuntu.com/a/512792/390372](http://askubuntu.com/a/512792/390372)

---

