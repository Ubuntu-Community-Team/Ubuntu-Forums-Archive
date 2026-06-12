---
title: "DVD problems with 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by BobvanderPoel on 2009-10-30
I'm having nothing but problems with my DVD drives with a recently installed 9.10 (Karmic).

After getting all the restricted packages and different players (totem, mplayer and vlc) I find the same problems ... jerky or slow playback. If I start to play from the start of a disc it appears to be alright. But, if I move a pointer to the middle of a movie the player either pauses for minutes or crashes.

Reading other bits around the web I _think_ this is a DMA problem. Not idea how to fix it. I have 2 drives on a (parallel) IDE connector. The drives show up as /dev/sr0 and /dev/sr1.

BTW, I have uninstalled and re-installed pulseaudio with no changes in the DVD issue.

Any ideas/solutions appreciated.

Thanks.

---

### Post by ajhunt on 2009-10-30
Hi!

Have you seen this thread: [http://ubuntuforums.org/showthread.php?t=1306282&highlight=play+dvd](http://ubuntuforums.org/showthread.php?t=1306282&highlight=play+dvd)

Worked for me :popcorn:

---

### Post by BobvanderPoel on 2009-10-30
Thanks ... but no joy :(

I have verified that I have libdvdcss2, libdvdread4, and w32codecs installed for the current repositories.

And, the video does sort-of work. If it was a codec problem I'd not be seeing anything at all or getting errors. I'm seeing the video and not seeing any error messages!

Just a tad slow to start, jerky and no ability to jump around. Plus, crashes.

I'm sticking with my guess that there is a DMA or other problem. Anyone know how I could check that???

These drives and discs worked just fine with my earlier version of ubuntu (8.04). So, it's most likely not my hardware.

Help, help, help!!!

---

### Post by mc4man on 2009-10-30
Start vlc from a terminal and then try playback, see what it says.

If nothing relevant then go 
```
vlc -vv or vlc -vvv
```

or try mplayer like such
mplayer dvd://
or 
mplayer dvd://[COLOR="Blue"]2[/COLOR]
Where the blue is the main movie title ( the first command assumes title one, dvd:// assumes default drive - sr0

Do you have video drivers installed?

You could try a different video output 

vlc - tools -> preferences -> video, try OpenGl or X11 in the 'output' dropdown

mplayer - add a -vo to command 
-vo x11
-vo gl2
-vo sdl

---

### Post by BobvanderPoel on 2009-10-30
Okay. Did a few of the suggestions and I get a lot of printing ... but, I'm not sure what I'm looking for. From vlc I get at the startup:

bob$ vlc 
VLC media player 1.0.2 Goldeneye
[0x915e2a0] main interface error: no interface module matched "globalhotkeys,none"
[0x915e2a0] main interface error: no suitable interface module
[0x90b5140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x90b5140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

Once I select a title from the disc:

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: StorageLabs UDF Volume
libdvdnav: DVD Serial Number: 327F5428449C86B7
libdvdnav: DVD Title (Alternative): X17FD1480 TinyUDF Volume Set ID
libdvdnav: Unable to find map file '/home/bob/.dvdnav/StorageLabs UDF Volume.map'
*** Zero check failed in ifo_read.c:517
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00002200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00004000
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0xb7300d38] main input error: ES_OUT_RESET_PCR called
[0xb7300d38] main input error: ES_OUT_RESET_PCR called
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead

... and a lot more language lines.

And a (suspect??) line:

*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***

Once playing:

[0xb7300d38] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7312930] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:256000
[0xb732bfb8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***
...multiple lines like the last one.

And when I try a seek, I get a bunch of the above again.

Does this mean anything???

---

### Post by mc4man on 2009-10-30
Well it appears vlc is having difficulty reading the disk. 

Do you have any other dvds to try, preferably  from another producer?

If you have mplayer installed then try it to compare, It appears that the dvd has only one title so go ( with the dvd in your sr0 drive

mplayer dvd:// -ao pulse


( whether or not an issue for vlc the audio output should generally be set to pulse also

---

### Post by BobvanderPoel on 2009-10-31
Yes, seek problems. I don't think it's a problem with vlc since mplayer and totem give similar problems. 

I've tried a number of different discs and they all give similar results.

Again, this is happening with both by drives connected via PATA interface. That is why I am guessing that the problem is with an initialization of the kernel and not the players. I could be wrong on this!

Probably the easiest thing to do is to pick up a new SATA drive and try that. But, one of the "features" of linux is the ability to use old hardware ... and the drives I've got really aren't that old ... well, I'm much older myself :)

Ideas still appreciated!

---

### Post by BobvanderPoel on 2009-11-01
Installed xine and all seems to be fine now. I've not tried totem-xine, but gxine and plain xine both work perfectly. Thanks for the help on this!

---

