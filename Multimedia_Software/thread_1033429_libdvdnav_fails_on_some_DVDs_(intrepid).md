---
title: "libdvdnav fails on some DVDs (intrepid)"
date: 2009-01-07
forum: Multimedia Software
---

### Post by efjen on 2009-01-07
Hello all.

Libdvdnav won't show the menus on many of my DVDs. I can start each title/chapter myself by my entering the numbers, and in that case it plays back properly. However, as soon as the chapter is ended, playback stops, and I have to manually start it from the next chapter. It's very annoying, to say the least.

Here is the output from VLC on one such disc (Lost season 4).

```

libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: LO4-0E-UT4_DES
libdvdnav: DVD Serial Number: UNDEFINED
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/fuje/.dvdnav/LO4-0E-UT4_DES.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.

```

I've searched for information about this, but haven't found anything useful.

I've also tried the CVS version of libdvdnav, but with the same result. (I then got "Using dvdnav version 0.2cvs from http://dvd.sf.net" or something similar, so I know it was using the new version.)

Can anyone please help me with this?

---

### Post by wolfen69 on 2009-01-07
perhaps you should check vlc's settings. menus in vlc have always worked for me in vlc on every install.

---

### Post by mc4man on 2009-01-07
the 0.9.x versions of vlc can have problems navigating a few titles, especially if there is structure protection. Regions 2,4 are more likely to have s.p. than region 1.

You can always try resetting vlc's config (if you made any audio, video output changes they'll have to be redone.

```
vlc --reset
``` 

You could also try totem-xine on problem disks (requires libxine1-ffmpeg

---

### Post by efjen on 2009-01-07
Thank you for your replies. I have worked around the problem by installing totem-xine (and removed totem-gstreamer). Now menus/chapter changes are working in Totem. (I forgot to mention in my original post that the problem included Totem.)

VLC still has the same problem as before. Maybe this can be fixed by making VLC use xine somehow; I haven't looked into that yet. As long as I have at least 1 functioning player, I'm happy.

From what I gather, Xine is using a different method than libdvdnav, and I guess that's why it's working.

---

