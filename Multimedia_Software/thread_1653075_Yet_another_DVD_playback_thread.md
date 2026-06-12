---
title: "Yet another DVD playback thread"
date: 2010-12-26
forum: Multimedia Software
---

### Post by dvalp on 2010-12-26
Ok, so here it goes, yet another "Ubuntu won't play my DVD" thread. Yes I've seen the other threads, yes I've tried everything I could find, and yes the DVD is in good (brand new) shape. I've tried various guides, including the ubuntu community documentation and 'sudo /usr/share/doc/libdvdread4/install-css.sh'. 

I'm running Maverick with recent updates. Some DVDs will play fine, but others won't. I'm starting to assume that this is some sort of DRM problem, but I don't know how to confirm that. And finally, I am able to rip the DVD to my hard drive, but the video programs still won't play the actual DVD.

The DVD is set to regions 2 and 4, my drive is region 1. AFAIK this should not be a problem for VLC, and I am able to play other region 2 DVDs. It reads the title keys fine and stores them. It then simply stops reading. Using verbose output I get the following messages:

```
[0x8508134] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x836c884] dvdread demux error: read failed for 1/4 blocks at 0x01
```

or:

```
libdvdcss error: read error
libdvdcss error: read error
[0x90b94a4] dvdnav demux warning: cannot get next block (Error reading from DVD.)
```

and that's the end of it, it won't try any further.

Totem, in debug mode, gives me:

```
** Message: Error: Could not read from resource.
resindvdsrc.c(1098): rsn_dvdsrc_step (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading from DVD.
```

Entering 'sudo aptitude search libdvd' gives me:

```
p   libdvd-dev                      - extract video and audio tracks - devel fil
p   libdvd0                         - extract video and audio tracks - runtime f
v   libdvdcss                       -                                           
p   libdvdcss-dev                   - Simple foundation for reading DVDs - devel
i   libdvdcss2                      - Simple foundation for reading DVDs - runti
p   libdvdnav-dbg                   - DVD navigation library (debug)            
p   libdvdnav-dev                   - DVD navigation library (development)      
i A libdvdnav4                      - DVD navigation library                    
p   libdvdread-dbg                  - library for reading DVDs (debug)          
p   libdvdread-dev                  - library for reading DVDs (development)    
i A libdvdread4                     - library for reading DVDs

```

---

### Post by mc4man on 2010-12-26
There are a couple of structure protections that libdvdread4 (dvdnav) has problems with.
Have you tried having vlc open the main movie title directly? (Media - Open disc, enter the title number, or try dvdsimple (no menus) or from cli where X is title number
vlc dvd://@X

While there aren't many xine base players worth using anymore they do use a different dvdnav that's better at navigating some of the sp titles.
You could try xine-ui I guess.
(I've keep totem-xine going thru natty just for this purpose, it's not available, one has to build.

---

### Post by dvalp on 2010-12-26
Trying the chapters on their own I get the dvdnav demux problem along with some other stuff I'm assuming isn't important. I'm adding it anyway, just in case.

```
Warning: call to srand(338822)
[0xb6847a6c] avcodec decoder warning: refusing to decode non validated subtitle codec
[0x8c78954] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x8c78954] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x89a89ac] qt4 interface warning: Input option: dvdread-caching=300

```

With dvdsimple (no menu) I get the 1/4 blocks problem.

```
[0xb68071f4] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x96799c4] dvdread demux error: read failed for 1/4 blocks at 0x01

```

xine gives me "event too old, discarding" and puts up a message saying that it can't read the source, and that maybe I don't have enough rights or the source doesn't contain data. I know I have the rights because I can play other DVDs, and I know it is readable since Handbrake can rip it.

---

### Post by mc4man on 2010-12-26
Well xine players (exception of totem-xine), are a pita.

There may not be any sp, if you wish to mention the disc title do so.

While may be of no use if you want to take a closer look at what's happening w/ libdvdcss you could try this.
Insert the dvd, close out any player if it opens. _Then_  go into home folder and delete either the complete .dvdcss folder or open it up and delete the folder associated with the dvd in question (if unsure just delete .dvdcss itself
following that 2 commands
 ```
export DVDCSS_VERBOSE=2 
export DVDCSS_METHOD=title && vlc dvd:// > vlc_output.log 2>&1
```
Then close out vlc and see if the log in home dir. has anything interesting

---

### Post by dvalp on 2010-12-26
That certainly gave me a lot of information, but I'm not sure which part is useful. The titles may or may not be getting cracked...

```
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a8
libdvdcss debug: cracking title key at block 424
libdvdcss error: read error
libdvdcss debug: read error at block 426, resorting to secret arcanes to recover
libdvdcss debug: opening target `/dev/scd0'
libdvdcss debug: using libc for access
libdvdcss error: read error
libdvdcss debug: end of title reached
libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2
libdvdcss debug: no scrambled sectors found
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
```

Similar information is given for each title, but it all looks about the same. In the end, it leaves me with:

```
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 4
Warning: call to srand(508462)
libdvdcss error: read error
libdvdcss error: read error
libdvdcss error: read error
libdvdcss error: read error
libdvdnav: Using dvdnav version 4.1.3
libdvdnav: DVD Title: SOMETHING_COMPLETELY_DIFFERENT  
libdvdnav: DVD Serial Number: 3E5F1DEB___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ratboy/.dvdnav/SOMETHING_COMPLETELY_DIFFERENT^_^A.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
```

This is one DVD from a box set. I've been playing around with some of the others, and on at least one it fails to break css on several of the titles.

I guess the questions I have at this point are: 1) Why does libdvdcss2 fail sometimes, and 2)Why does libdvdnav have so much trouble finding a map file? (And does that failure even mean anything?)

I'll include the full log, in case it helps in anyway.

---

