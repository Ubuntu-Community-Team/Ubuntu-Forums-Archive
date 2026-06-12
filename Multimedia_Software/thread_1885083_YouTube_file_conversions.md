---
title: "YouTube file conversions"
date: 2011-11-22
forum: Multimedia Software
---

### Post by dik909 on 2011-11-22
Okay, this may seem basic, but I'm having a helluva time converting .MP3s to a supported YouTube format.  

I'm just digitizing some records to upload to YT, and so I don't really want/need fancy graphics - just wanna overlay a simple .JPG image of the album cover.  

Tried VLC Player first, but I'm finding that it seems to only go from video to audio.

I have tried using Avidemux and Videoporama to make a straight up "movie", but those don't seem to be cooperating - perhaps it's just me?, I don't have any video editing experience.

Thusly, I'm hoping for some advice/suggestions on the simplest way to convert .MP3 to .AVI, with the added possibility of layering one simple photo over the "movie".

Anyone ?  Bueller ??

---

### Post by satanselbow on 2011-11-22
Install openshot from USC or 

```
# apt-get install openshot
```

Import your tune into track 1

import you picture into track 2

edit the properties of you picture track to the same duration as the tune - or the picture will disappear half way through the tune...

Export as... well pretty much anything mpg / avi and upload away :D

only use tunes to which you own the copyright obviously... :popcorn:

---

### Post by jimmydean886-2 on 2011-11-22
Openshot, as mentioned above, is a GREAT program for that kind of thing. One problem: it can be fairly confusing sometimes. Try using PiTiVi, and if that crashes on you, go straight to Openshot. Personally, I use both because one has features the other doesn't, but overall, PiTiVi is easier for straight conversion and overlaying audio with a picture.

---

### Post by dik909 on 2011-11-22
> **satanselbow said:**
> Install openshot from USC or 

```
# apt-get install openshot
```

Import your tune into track 1

import you picture into track 2

edit the properties of you picture track to the same duration as the tune - or the picture will disappear half way through the tune...

Export as... well pretty much anything mpg / avi and upload away :D

only use tunes to which you own the copyright obviously... :popcorn:

yeehaw, got it workin !  THANK YOUUUU !!!!

---

### Post by FakeOutdoorsman on 2011-11-22
You can do it in one command with ffmpeg:
```
ffmpeg -loop_input 1 -i image.jpg -i audio.mp3 -qscale 2 -acodec copy -shortest output.mkv
```
or if you're using a more recent ffmpeg:
```
ffmpeg -loop 1 -i image.jpg -i audio.mp3 -qscale 2 -acodec copy -shortest output.mkv
```

---

