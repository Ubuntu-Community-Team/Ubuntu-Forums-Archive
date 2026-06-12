---
title: "Play MP4 files?"
date: 2012-11-13
forum: Multimedia Software
---

### Post by alexgo on 2012-11-13
I'm running lubuntu 12.10 and recently started downloading a video podcast. The file format is MP4 and when I hit play Gnome mplayer opens, but it doesn't play the file. I'm guessing this is just a missing codec or something, but I couldn't find anything through search.

---

### Post by cwsnyder on 2012-11-13
Have you installed the **lubuntu-restricted-extras** packages?  I am guessing not, and they contain most of the codecs needed for playing proprietary file formats, like mp3, avi, and mp4.

---

### Post by cybrsaylr on 2012-11-13
I'm also having problems playing mp4 files with movie player on 64 bit 12.04. Had no problems playing mp4 files with movie player with Natty. 

Just installed lubuntu-restricted-extras packages but movie play still won't play mp4 files. Do you need something else?

VLC plays these mp4 files fine.

---

### Post by cwsnyder on 2012-11-13
It depends on the particular mp4 file.  An .avi mp4 file, I believe uses .aac audio codec and the DivX video, but some mp4 files use the H264 video and/or .als audio encoding.  The H264 decoder is needed if the video is 'high-definition' 720p or 1080p or higher video definition, and I am not certain if that decoder is included.

---

### Post by alexgo on 2012-11-13
I hadn't installed that, but after installing, no change. It's mp4-large, which I don't think is HD.

---

### Post by cybrsaylr on 2012-11-13
The couple mp4 files I have are old. They always played fine on Windows and all Ubuntu versions before 12.04 Precise Pangolin.

---

### Post by andrew.46 on 2012-11-13
mp4 in this case is a *container* that can hold a variety of video and audio codecs, so I suspect it is not the mp4 container itself that is causing the problem. Can you give a link to any of these troublesome files?

---

### Post by quentinl on 2012-11-13
i use gnome mplayer and i think that it works

---

### Post by alexgo on 2012-11-13
Here's the link: [http://revision3.com/feed/channel/games/mp4-large](http://revision3.com/feed/channel/games/mp4-large)

The specific file I'm trying is dated 11/12/2012 at 08:00 PM and is called:  destructoid--0388--adam-sessler-joins-rev3games-editor-in-chief--large.h264.mp4

---

### Post by andrew.46 on 2012-11-13
This file should not give you too much trouble as it is h.264 video and aac sound, I have added a screenshot of the file playing with SMPlayer. For the repository MPlayer / SMPlayer / Gnome MPlayer you will need the libav* packages that have not been censored by the Ubuntu / Debian packagers. I am not on my Ubuntu VM at the moment but I believe that installing *libavcodec-extra-53* will drag a few friends with it and may get the file started up..

---

### Post by alexgo on 2012-11-13
Installed *libavcodec-extra-53* and no change.

---

### Post by andrew.46 on 2012-11-13
Hmmmm.... seems a little odd, vlc will play this file for you?

---

### Post by alexgo on 2012-11-14
Just downloaded VLC to test, it plays the audio, but the video is just a black screen.

---

### Post by andrew.46 on 2012-11-14
An easy test will be to alter the video output device for vlc. The setting is from Tools --> Preferences --> Video --> Display --> Output and experiment a little there. 

The MPlayer output for this file should look something like the following:

```

andrew@skamandros~/downloads$ **[COLOR="Red"]mplayer destructoid--0388--adam-sessler-joins-rev3games-editor-in-chief--large.h264.mp4 [/COLOR]**
MPlayer SVN-r35420-4.7.1 (C) 2000-2012 MPlayer Team

Playing destructoid--0388--adam-sessler-joins-rev3games-editor-in-chief--large.h264.mp4.
libavformat version 54.36.100 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  640x360  24bpp  29.970 fps  944.9 kbps (115.3 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 creation_time: 2012-11-12 23:12:34
 title: adam sessler is back! nuketown zombies in black ops ii, mass effect 4 new details, & more!
 album: destructoid
 encoder: Lavf53.32.100
 copyright: 2012 revision3 corporation
 description: today we found out the next mass effect game will use the frostbite 2.0 engine, activision is throwing nuketown zombies into all black ops ii season pass purchases, square enix is releasing a tomb raider collector's edition, and gabe newell has confirmed 
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.71.100 (internal)
**[COLOR="Red"]Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 102.2 kbit/7.25% (ratio: 12781->176400)
**[COLOR="Red"]Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 640x360 => 640x360 Planar YV12 
A:  42.9 V:  42.9 A-V:  0.000 ct:  0.057   0/  0  2%  0%  0.2% 0 0 

Exiting... (Quit)

```

It would be interesting to see what your MPlayer output shows.

---

### Post by alexgo on 2012-11-14
I don't know how to post the output like you did...I Tried each setting in order "x11 video output (XCB)" is what worked. Thanks!

---

### Post by andrew.46 on 2012-11-14
Great news :)

---

