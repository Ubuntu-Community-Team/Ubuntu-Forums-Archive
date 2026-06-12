---
title: "Convert HD .mkv movie to Xbox compatible .avi"
date: 2009-09-25
forum: Multimedia Software
---

### Post by gobberpooper on 2009-09-25
Okay so I have the Director's Cut Gladiator in 1080p in .mkv format. I want to convert it to .avi to play on the 360. I just got an HDMI cable for 1 cent and it looks great. I completely forgot how to convert movies. The video/audio info is:
**Video**
*Dimensions:* 1920 x 816
*Codec:* H246
*Framerate:* 24 frames per second
*Bitrate:* N/A

**Audio**
*Codec:* DTS
*Channels:* Surround 5.1
*Sample Rate:* 4800 Hz
*Bitrate:* 80kbps

Help please. Thanks!

---

### Post by gobberpooper on 2009-09-26
bump

---

### Post by gobberpooper on 2009-09-27
bump
I tried to use MediaTomb until I found out it's only for the PS3. So then I used fuppes but the 360 still only shows "myserver" which is the ushare server name. I tried the ps3mediaserver which apparently has xbox support but I can't configure it to connect to the xbox. I restarted the computer and 360 so it doesn't show the ushare server. But now it's not showing the fuppes or ps3mediaserver. How do I get it to recognize fuppes so I can transcode .mkv files on-the-fly?

---

### Post by gobberpooper on 2009-09-28
Okay I think I messed up my computer somehow. Now I can't convert anything, it keeps telling me that I don't have the libraries. It keeps saying "Unknown encoder 'libmp3lame'" or "Unknown encoder 'msmpeg4'" which is ridiculous because I've converted several things before.

---

### Post by rsambuca on 2009-09-28
I just use Avidemux to convert the x264.mkv files for the xbox.  The settings I use:  

Video -> copy
Audio -> AAC, stereo
Container -> mp4

File name must be .mov for the XBox360 to play it.
I then use ushare to stream to the XBox.

---

### Post by burntresistor on 2009-09-28
Handbrake would do it.[http://handbrake.fr/]("http://handbrake.fr/")

---

### Post by war59312 on 2010-01-17
> **rsambuca said:**
> I just use Avidemux to convert the x264.mkv files for the xbox.  The settings I use:  

Video -> copy
Audio -> AAC, stereo
Container -> mp4

File name must be .mov for the XBox360 to play it.
I then use ushare to stream to the XBox.That works but then I cant fast-forward/rewind or skip chapters.

Just goes back to xbox media menu when I try.

---

### Post by rsambuca on 2010-01-19
> **war59312 said:**
> That works but then I cant fast-forward/rewind or skip chapters.

Just goes back to xbox media menu when I try.

Strange.  I don't seem to have those problems.

---

### Post by war59312 on 2010-01-20
Whoops, have to use safe mode. ;)

---

