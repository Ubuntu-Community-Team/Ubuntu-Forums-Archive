---
title: "Program to convert video to Xvid"
date: 2011-03-02
forum: Multimedia Software
---

### Post by chris1379 on 2011-03-02
I am looking for a Linux program to crop, resize, and convert videos to Xvid. I have been using Staxrip at [http://staxmedia.sourceforge.net/](http://staxmedia.sourceforge.net/) to convert them in Windows. The source is mostly MPEG2 from TV recordings but is sometimes DVD, vob files, or h.264. I convert them to play on my DivX player or slower laptop. I don't have a problem with using Windows for this but a Linux equivalent would be nice.

Chris

---

### Post by babarosa on 2011-03-02
I'd give "handbrake" or "ffmpeg" a try. Be sure to test the most recent versions from a ppa launchpad.

---

### Post by sites on 2011-03-02
```
sudo apt-get install ffmpeg xterm winff
```

This will give you a gui to use ffmpeg.  Otherwise it's all cli.

---

### Post by chris1379 on 2011-03-02
WinnFF installed fine but gives me an error```
Unknown encoder 'libxvid'
```.

Handbrake is nice but the author chose to drop DivX and Xvid from the program without warning.

---

### Post by JohnAStebbins on 2011-03-02
> **chris1379 said:**
> WinnFF installed fine but gives me an error```
Unknown encoder 'libxvid'
```.

Handbrake is nice but the author chose to drop DivX and Xvid from the program without warning.

HandBrake never had a "DivX" encoder. It is true that we dropped the Xvid encoder.  But that doesn't mean we eliminated support for mpeg-4 part 2 entirely (that's the codec used in DivX).  We kept ffmpeg's mpeg-4 part 2 encoder.  Same format, different encoder.

But of coarse we also eliminated our broken implementation of avi and most DivX players will not play mkv or mp4 files.  So if this is the case with your player, HandBrake is not for you.

EDIT: "Without warning"?  What are we suppose to do, announce it on slashdot?  We discussed dropping these things for more than a year on IRC and our forums.

---

### Post by eerror on 2011-03-02
handbrake ([http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)) should do.
Be sure to check out the command line options if you run into issues with the gui.

---

### Post by FakeOutdoorsman on 2011-03-02
> **chris1379 said:**
> WinnFF installed fine but gives me an error```
Unknown encoder 'libxvid'
```

See options B or C in [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

---

### Post by chris1379 on 2011-03-02
> **JohnAStebbins said:**
> HandBrake never had a "DivX" encoder. It is true that we dropped the Xvid encoder.  But that doesn't mean we eliminated support for mpeg-4 part 2 entirely (that's the codec used in DivX).  We kept ffmpeg's mpeg-4 part 2 encoder.  Same format, different encoder.

But of coarse we also eliminated our broken implementation of avi and most DivX players will not play mkv or mp4 files.  So if this is the case with your player, HandBrake is not for you.

EDIT: "Without warning"?  What are we suppose to do, announce it on slashdot?  We discussed dropping these things for more than a year on IRC and our forums.
Sorry, didn't mean to offend. I didn't spend time in the forums discussing HandBrake because it just worked. What I meant was I didn't see any mention of the change when I downloaded the new version. I was caught by surprise. I still use HandBrake for my Ipod.

I'm surprised no one has mentioned Avidemux at [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/). It seems to be a good one for Xvid.

---

### Post by shantiq on 2011-03-03
> **chris1379 said:**
> I am looking for a Linux program to crop, resize, and convert videos to Xvid. I have been using Staxrip at [http://staxmedia.sourceforge.net/](http://staxmedia.sourceforge.net/) to convert them in Windows. The source is mostly MPEG2 from TV recordings but is sometimes DVD, vob files, or h.264. I convert them to play on my DivX player or slower laptop. I don't have a problem with using Windows for this but a Linux equivalent would be nice.

Chris


kdenlive in your software centre will do this beautifully to Xvid4 if that is what you are looking for

---

### Post by chris1379 on 2011-03-03
I will definitely be trying kdenlive. Before I jump in too deep, I'm wondering if 64-bit Ubuntu will make a huge difference over 32-bit. I am running an AMD Athlon 64 X2 6000+ with 2GB RAM. I hear 64-bit can be buggy and some programs won't run correctly so I've been hesitant to try it.

---

### Post by FakeOutdoorsman on 2011-03-03
I've been using a 64-bit Linux distro for a year now with few issues (notably Flash being annoying). As for 64-bit, encoding with x264 is generally a little faster, but you may not notice the difference. I'm not sure about other encoders.

---

