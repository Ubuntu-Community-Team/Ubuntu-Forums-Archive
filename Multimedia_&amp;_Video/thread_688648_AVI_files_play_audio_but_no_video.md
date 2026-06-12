---
title: "AVI files play audio but no video"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by Monsuco on 2008-02-05
I can't seem to get video to play in some AVI files of mine. I have yet to get them to work on Linux. I have tested it in Totem (using Xine), Kaffeine, VLC, and MPlayer. I get audio but the video isn't showing up, (this happened on Windows until I installed K-Lite). I have Kubuntu-Restricted-Extras installed but it seems I still need a codec? Any thoughts?

---

### Post by wolfen69 on 2008-02-05
try
```
sudo apt-get install libavformat1d
```

---

### Post by Monsuco on 2008-02-06
I already have it installed, any other ideas.

---

### Post by gsmanners on 2008-02-06
In VLC Preferences, if you check Advanced options and go to Video/Output modules, you should be able to change the Video output module. Make sure to try XVideo, X11, and OpenGL.

---

### Post by Monsuco on 2008-02-07
Nope, I think it is a codec issue. Windows Media Player did the same thing on my Windows Vista partition until I installed the K-Lite Codec pack. I suspect I need to install something. I remember it said something about not having a codec (I think it was the DV-80 codec or something.) when I played it in one of the media players, but I can't remember which one. The rest just play audio (with visualizations) but video doesn't play. What are all the codecs that AVI files could possibly use?

---

### Post by gsmanners on 2008-02-07
If you load the file in mplayer from a console, one of the messages should be what the codec is and what problems it has (if any).

---

### Post by Monsuco on 2008-02-07
I need the VP 70 codec apparently. Where do I find that?

---

### Post by gsmanners on 2008-02-08
I think you need w32codecs for that.

See: [http://ubuntuforums.org/showthread.php?t=502179](http://ubuntuforums.org/showthread.php?t=502179)
[http://www.on2.com/index.php?359](http://www.on2.com/index.php?359)

---

### Post by Monsuco on 2008-02-09
> **gsmanners said:**
> I think you need w32codecs for that.

See: [http://ubuntuforums.org/showthread.php?t=502179](http://ubuntuforums.org/showthread.php?t=502179)
[http://www.on2.com/index.php?359](http://www.on2.com/index.php?359)

I have them installed, but is there any way to add the VP70 codec, I don't want to have to convert all these movies since it would probably hurt quality and of course it would take a long time.

---

### Post by Giannis68 on 2008-02-09
download binary codec for MPlayer
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

