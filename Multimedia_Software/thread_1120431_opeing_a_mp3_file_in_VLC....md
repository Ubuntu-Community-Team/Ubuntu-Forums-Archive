---
title: "opeing a mp3 file in VLC..."
date: 2009-04-09
forum: Multimedia Software
---

### Post by brijith on 2009-04-09
Hai Friends,

I have set vlc player as default player for mp3 files. of course it working fine. My issue is each time double click on an mp3 file it opens and plays new instance of VLC. I would like to open the and play the already running VLC player...

How can I do that.... 


Thanks For Your Help

---

### Post by mc4man on 2009-04-09
For that you need the "allow only one instance" option available in any 0.9.x or 1.0 version. (but not in 0.8.6.x

If your using intrepid it's in the settings, for hardy you'll need to build or find a .deb package set somewhere (there should be some ppa's that have 0.9.x for hardy (0.9.8a or 0.9.9a preferred, possibly harder to find for hardy than earlier versions will be


Edit; 
One minor issue with the one instance is that I have yet to see it work in conjunction with the"enqueue files in playlist when in one instance mode" .The effect is that while additional files are added to playlist they also start playing.

The work around is that when creating the file association (r. click, properties, open with) to not use vlc. Use a 'custom command' instead
```

vlc --playlist-enqueue
```

related thread (nautilus actions) and how to name the custom command (if desired

[http://ubuntuforums.org/showthread.php?p=6924573#post6924573](http://ubuntuforums.org/showthread.php?p=6924573#post6924573)

---

