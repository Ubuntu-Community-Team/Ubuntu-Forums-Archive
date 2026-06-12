---
title: "Help with kdenlive custom profile - clips for halloween"
date: 2011-10-24
forum: Multimedia Software
---

### Post by BFG on 2011-10-24
I have an optoma PK301 projector, which we're going to use to project some horror clips for a party on the weekend.

The PK301 comes with some windows software to convert files for playing on its SD card. It's a customised version of Arcsoft media convertor. The software settings as I can extract them from the arcsoft software are:

Video Resolution: 720x480
Video bitrate: 1536Kbps
Video Frame rate:	30.00
Video aspect ratio:	3:2
Video codec: Arcsoft H264 codec
Audio codec: PCM, 44100Hz

I'm a video editing newbie.  I'm using avidemux to extract clips (sources are a variety of different formats). And kdenlive to stitch them together.

I then have to render, and it makes sense to render directly into a format which the optoma will use. 
Is there a profile which matches this so I can prepare movies directly in kdenlive? Or how can I create a custom profile?

I don't really know a CIF NTSC from a VCD Pal, and selecting them gives me only half the info.  I've tried 10+ profiles now and it's taking ages so I could use some expert help :)

---

### Post by NarsilAnduril on 2011-12-11
The PK 301 only reads fixed bitrate MPEG-4 video with mono or stereo audio in MP3 or AAC encoding.

You can easily batch re-encode your files with [WinFF]("http://www.ubuntugeek.com/winff-gui-for-the-command-line-video-converter-ffmpeg.html").

You will find the presettings files here to encode in [800 kbps]("http://www.box.com/s/r30sn51c0m4asm199byf") (enough for me) or [1000 kbps]("http://www.box.com/s/mjkd0qbc4incf1a5qhpy").

---

### Post by sgtGarcia on 2011-12-11
I found it on KDEnLive forum:

```
f=avi vcodec=libx264 s=720x480 b=1536k aspect=%dar acodec=aac ab=128k ar=44100
```
+++++++++++++++++++++++++++++++++++++++++++++
PK301 accepts

video codec (vcodec) : h264 in fileformats (f) : mp4, avi, mov, 3gp [BASELINE]
video codec (vcodec) : mpeg4 in fileformats (f) : avi [SIMPLE PROFILE]
video codec (vcodec) : xvid in fileformats (f) : avi [BASELINE]
max resolution (s) : 720 x 480
audio codec (acodec) : AAC, MP3, PCM, ADPCM, WMA, OGG

In KDEnLive ( I have 0.8.2 ) choose Rendering->H.264
& then set bitrate of video & audio.

---

