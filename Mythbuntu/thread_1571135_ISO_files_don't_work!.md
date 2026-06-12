---
title: "ISO files don't work!"
date: 2010-09-09
forum: Mythbuntu
---

### Post by MauroKTM on 2010-09-09
Good Day,

After ripping a DVD if you try to play from the video browser it start to open the DVD player and not the ISO file in the folder videos>

> 
2010-09-09 12:53:42.733 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-09-09 12:53:43.566 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1169
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
2010-09-09 12:53:43.573 Failed to open DVD device at /dev/dvd


Of course if the file is an .AVI it plays.

In the "Files Type" ISO file is mached with Internal player

Any Idea?

Thank you
M.

---

### Post by murchball on 2010-09-09
Are you using storage groups? ISO files won't play if you are. I'm not sure when (or if) this will be fixed, but I'm hoping for .24.

From the wiki: [http://www.mythtv.org/wiki/MythVideo#Disadvantages](http://www.mythtv.org/wiki/MythVideo#Disadvantages)

---

### Post by tgm4883 on 2010-09-09
> **murchball said:**
> Are you using storage groups? ISO files won't play if you are. I'm not sure when (or if) this will be fixed, but I'm hoping for .24.

From the wiki: [http://www.mythtv.org/wiki/MythVideo#Disadvantages](http://www.mythtv.org/wiki/MythVideo#Disadvantages)

ISO's in storage groups is fixed in 0.24

[http://www.mythtv.org/wiki/Release_Notes_-_0.24#Major_Changes](http://www.mythtv.org/wiki/Release_Notes_-_0.24#Major_Changes)

---

### Post by murchball on 2010-09-09
That's awesome! I hadn't checked the .24 release notes. Storage groups were a huge improvement (especially with multiple frontends), but the lack of ISO support was a bummer. Three cheers to the development team!

---

### Post by MauroKTM on 2010-09-09
Thanx a lot,

I disabled the Video storage group... Now it works!

But on 0.24.... I hope...

Thanx
M.

---

