---
title: "red video playback-- weird..."
date: 2011-03-06
forum: Multimedia Software
---

### Post by chips24 on 2011-03-06
so, i have reinstalled the adobe backage several times and restarted many times, and my video playback on youtube is... red 
it did work before... (and only on youtube -- youtube links outside of youtube work :S)
here's an example

[http://www.youtube.com/watch?v=WBfqTQ4vhIM&feature=channel_video_title](http://www.youtube.com/watch?v=WBfqTQ4vhIM&feature=channel_video_title)

---

### Post by chips24 on 2011-03-06
and here is the same thing on a link outside of youtube...

---

### Post by cchhrriiss121212 on 2011-03-06
Right click on any flash video or element, then disable hardware acceleration under settings.

---

### Post by travisp on 2011-03-08
> **cchhrriiss121212 said:**
> Right click on any flash video or element, then disable hardware acceleration under settings.

I've got red playback on youtube too. When I right click on the video, "settings" is grayed out so I can't select it. Any more ideas? I reported the problem to youtube but have yet to hear back.

---

### Post by cchhrriiss121212 on 2011-03-08
Try viewing a flash video on another site, then change the setting from there.

---

### Post by zebutron on 2011-03-13
just wanted to note that I have the same problem. Youtube only, right-click "settings" grayed out, embedded video not a problem.

---

### Post by beew on 2011-03-14
> **travisp said:**
> I've got red playback on youtube too. When I right click on the video, "settings" is grayed out so I can't select it. Any more ideas? I reported the problem to youtube but have yet to hear back.

You can go find any flash video from another site and do the right clicking, or you can clean up the cache for flash (use bleachbit, for example), after cleaning the cache the settings option for youtube wouldn't be greyed out anymore. Maybe you can just delete all Youtube cookies from  Firefox, but I haven't tried that.

---

### Post by dirty_harry on 2011-03-14
You can edit /etc/adobe/mms.cfg to disable hw-acceleration:
```
$ cd /etc/adobe
/etc/adobe$ sudo nano mms.cfg
```just change:
```
EnableLinuxHWVideoDecode=0
```this is very useful for me, because I use betterprivacy for firefox which delets all flash-cookies but also the settings. >> [http://blogs.adobe.com/penguinswf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguinswf/2008/08/secrets_of_the_mmscfg_file_1.html)

there is this also a big tread about this problem over here:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

I personally use flash-aid for firefox to do all this and I must confess that currently flash seems to ignore mms.cfg. but this is maybe because I choose npwrapper.libflashplayer.so for 32bit compatibility.

---

