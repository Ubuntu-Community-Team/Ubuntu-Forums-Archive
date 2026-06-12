---
title: "[SOLVED] Codecs - MKV , RealVideo/Audio"
date: 2008-07-28
forum: Multimedia Software
---

### Post by owain123 on 2008-07-28
I've been trying to get some .mkv's to work but they wont play at all. VLC is supposed to be able to play them. I ran Gspot on my windows install and it says they are encoded with Real Video and Audio.
GomPlayer plays them fine in windows, and WMP11 plays them after some codec packs.

Any ideas?

---

### Post by Rhubarb on 2008-07-28
Matroska is just a container, most video players in ubuntu can play them if it has the correct codecs to play them.

In this case you need real audio / video playback support.
(I don't understand why the video isn't just in a rm container, matroska brings little benefits in this particular case).

I can't help you much here, as I have no experience in getting real video / audio codecs working in ubuntu.

You could try using the medibuntu repositories, and getting w32codecs.
And perhaps mplayer may be able to play them back.

---

### Post by owain123 on 2008-07-28
ok, tryed it on MPlayer (thought i had already tried that!)
Sound works but not video.

here is my MediaInfo output:

Format               : Matroska
File size            : 64.2 MiB
PlayTime             : 23mn 11s
Bit rate             : 387 Kbps
Encoded date         : UTC 2004-05-11 12:19:57
Writing application  : mkvmerge v0.8.8 built on Apr 23 2004 19:08:32
Writing library      : libebml v0.7.0 + libmatroska v0.7.0

Video #0
Codec                : Real 4
Codec/Info           : RealVideo 4.0 aka RealVideo 9
PlayTime             : 23mn 11s
Width                : 400 pixels
Height               : 300 pixels
Aspect ratio         : 4/3
Frame rate           : 30.000 fps
Language             : English

Audio #0
Codec                : RealAudio 7
Codec/Info           : Real Audio Cook Codec (codename: Gecko)
Channel(s)           : 2 channels
Sampling rate        : 44 KHz
Resolution           : 16 bits
Language             : English

Text #0
Codec                : UTF-8
Codec/Info           : UTF-8 Plain Text
Language             : Chinese

Text #1
Codec                : UTF-8
Codec/Info           : UTF-8 Plain Text
Language             : English



What are these Win32 codecs your talk about for MPlayer?

---

### Post by owain123 on 2008-07-28
ok, so i have downloaded the MPLayer codec pack. and also different realmedia codecs, put them into /usr/local/lib/codecs
and i have installed realplayer11 as one site said would help as Mplayer will read its directory or something.

Still no luck though!!

Are there any settings in Mplayer is should set?

---

### Post by Tony Sivori on 2008-07-28
I too recently encountered mkv files, and what worked for me was installing VLC player, I think it was in the medibuntu repository. Anyway after the VLC Player install, my preferred media player (Xine) plays mkv files perfectly.

---

### Post by owain123 on 2008-07-28
Yeah, VLC plays most MKV, except since mine uses Real audio and video ( which VLC Does not support ) they will not work will VLC.

Seems im close to getting it to work with MPlayer

---

### Post by owain123 on 2008-07-28
Ok fixed it.

Downloaded drv43260.dll

put it in /usr/local/lib/codecs and now works with MPlayer.

Only thing is when i skip scenes, the audio becomes choppy, but at least its working now! :)

---

