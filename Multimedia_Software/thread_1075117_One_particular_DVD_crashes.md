---
title: "One particular DVD crashes"
date: 2009-02-19
forum: Multimedia Software
---

### Post by CPesyna on 2009-02-19
I sat down yesterday and attempted to watch a disc of The Wire, but instead ended up with this head scratcher.

I have a fairly fresh install of 8.10 and DVD playback generally works fine.
When I attempt to watch this particular disc in VLC, the menus behave as they ought to, but upon selecting an episode, the program crashes to the desktop with the following terminal output:

```
[00000001] main libvlc debug: translation test: code is "C"
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: THE_WIRE_S3_D2
libdvdnav: DVD Serial Number: 34B65FCA
libdvdnav: DVD Title (Alternative): THE_WIRE_S3_D2
libdvdnav: Unable to find map file '/home/colin/.dvdnav/THE_WIRE_S3_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
[00000461] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000457] main decoder error: decoder is leaking pictures, resetting the heap
[00000458] main video output error: picture to date 0x8f552bc has invalid status 6
[00000458] main video output error: picture to display 0x8f552bc has invalid status 6
LibVLC fatal error locking mutex in thread 2956979088 at video_output/vout_subpictures.c:1365: 22
 Error message: Invalid argument at:
/usr/lib/libvlccore.so.0(vlc_pthread_fatal+0xb5)[0xb8044cc5]
Aborted
```

The bizarre part comes when trying to watch the same video using totem. There it seems to work *almost* all the time, but about 1 in 10 times (I can't reproduce it) it crashes at exactly the same spot. 

Any ideas? Perhaps this is more a question for the VLC people.

---

