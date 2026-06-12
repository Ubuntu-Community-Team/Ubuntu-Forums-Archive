---
title: "Youtube videos don't work in Chromium - damned HTML5"
date: 2010-07-01
forum: Multimedia Software
---

### Post by aneganov on 2010-07-01
Hi all,

Some time ago - month or so - Chromium started to use HTML5 on Youtube. I like this except this completely doesn't work. I see black sqare, HTML logo and video never starts.

I'm using nightly builds and update Chromium every day hoping one day this will work. But time passes, nothings is changing.

Any ideas how to use YouTube.com in Chromium? How to switch back on Flash?

---

### Post by aneganov on 2010-07-01
I don't see my message published!

---

### Post by aneganov on 2010-07-25
Bump. Now is on 10.04, still not playing anything on youtube.com - just loading icon "HTML5..."

---

### Post by kerry_s on 2010-07-25
go here to opt out:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

you need to have the "extra" codecs for html5

---

### Post by moore.bryan on 2010-07-25
I'm using Chromium's Daily PPA and I have no HTML5-YouTube issues...

---

### Post by aneganov on 2010-07-25
> **kerry_s said:**
> go here to opt out: ...
you need to have the "extra" codecs for html5

Thank you very much, Kerry! I installed that -ffmpeg-extra package, which replaced -ffmpeg and now HTML5 video on YouTube works!

---

### Post by Linye on 2010-07-25
Found this thread looking around and had the same problem which was resolve with the codecs package!

---

### Post by mrebanza on 2010-10-31
To get Chromium to work with HTML5 in uBuntu you have to first uninstall the free "open source only" package "chromium-codecs-ffmpeg" that ships with chromium (not chrome) with only supports OGG and WEBM video 


```
sudo apt-get remove --purge chromium-codecs-ffmpeg
```


and install the non-free proprietary version of the package named chromium-codecs-ffmpeg-nonfree  which has full support for MP3 and MP4 codecs . . . 

```
 sudo apt-get install chromium-codecs-ffmpeg-nonfree 
```


Enjoy.

---

