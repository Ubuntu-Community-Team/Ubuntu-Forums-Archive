---
title: "LossLess ripping and encoding"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Tpolich on 2008-05-20
I am looking for a way to riper and encoding method that is totally LossLess. If someone could point out a program or method to do so I would much appreciate it. 

And maybe something else to check the rip

---

### Post by tamoneya on 2008-05-20
I would use grip and rip them to FLAC (Free Lossless Audio Codec)
[http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151)

---

### Post by Artemis3 on 2008-05-20
I say, [Rubyripper](http://getdeb.net/search.php?keywords=rubyripper) (gutsy packages work) with a [patched cdparanoia](http://www.nabble.com/cdparanoia-and-cache-td6662854.html) (see [rebuilding packages](http://www.debian-administration.org/articles/20)) if your drive [caches audio](http://www.daefeatures.co.uk/search.php).

Lossless encoding is useless if you can't have [proper ripping](http://wiki.hydrogenaudio.org/index.php?title=Secure_ripping)...

---

### Post by Tpolich on 2008-05-20
> **tamoneya said:**
> I would use grip and rip them to FLAC (Free Lossless Audio Codec)
[http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151)

Would that work for video was well, haven't looked into (not at my house) but its got Audio in the name.

---

### Post by tamoneya on 2008-05-20
> **Tpolich said:**
> Would that work for video was well, haven't looked into (not at my house) but its got Audio in the name.

as you guessed at FLAC just does audio.  You can however have a video file that has FLAC for its audio component.  For example: an AVI video is just a container format for a video file and a audio file.  You could choose for the audio to be flac if you wished and have mpeg2 or 4 as your video.  However flac can sometimes be a little problematic on windows which doesnt install the codecs for flac by default.  while it is not hard to get it working it isnt as plug and play as say mp3 files.

---

