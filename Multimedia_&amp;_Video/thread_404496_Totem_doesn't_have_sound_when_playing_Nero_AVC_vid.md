---
title: "Totem doesn't have sound when playing Nero AVC video"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by Rizlaw on 2007-04-08
I just copied a few of my Nero AVC mp4 video files from my Windows XP installation to my new Ubuntu 6.10 installation. When I click to play the Nero created MP4 video files, the video plays fine in Totem, but there is no sound.

I have checked Totem's audio settings and tried "stereo", "5.1" and "AC3 pass through" but nothing works. I have installed ALL of the gstreamer multimedia plugins (good, bad, ugly, multiverse), including faac and faad.

When I play the same movie files in VLC, they playback fine with perfect 5.1 AAC audio.

Am I missing something, or does Totem simply not play any type of AVC mp4 video file.:confused:

Can I make VLC the default video file player instead of Totem (if Totem can't be made to work) when I double click a video file? How?

---

### Post by krussell on 2007-04-09
Hello :-)
Firstly if you haven't done this: replace totem-gstreamer with totem-xine package.
secondly, install libxine-extracodecs and other libs related to sound/video (a52, FAAC, FAAD, mp4, ffmpeg etc etc).

---

### Post by Rizlaw on 2007-04-09
> **krussell said:**
> Hello :-)
Firstly if you haven't done this: replace totem-gstreamer with totem-xine package.
secondly, install libxine-extracodecs and other libs related to sound/video (a52, FAAC, FAAD, mp4, ffmpeg etc etc).

Thanks. It worked.:)

---

