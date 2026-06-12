---
title: "flash stopped working"
date: 2008-08-21
forum: Multimedia Software
---

### Post by c-m on 2008-08-21
I recently installed flash and had been successfully watching the olympics and other video via the bbc iplayer.

Today I came to my computer and noticed that no flash video will work. Instead I am greeted with a blank grey screen where I would normally expect to see this video.

about:plugins shows:

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0.0 d569

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Any ideas?

---

### Post by wolfen69 on 2008-08-21
completely remove any flash you have on your pc.
do
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then
```
sudo apt-get install flashplugin-nonfree
```
do this with firefox closed.

---

### Post by SunnyRabbiera on 2008-08-21
I sometimes have this issue when running too many flash apps running like youtube.

---

### Post by c-m on 2008-08-24
well i closed firefox and loaded it again and all was well. It has tried to do it agian a few times, but loads at the last minute.

---

