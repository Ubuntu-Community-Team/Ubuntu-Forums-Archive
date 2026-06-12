---
title: "songbird - doesn't play ape (apemonkey) files !"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Klando on 2011-04-30
is there a way to make it work with .ape files? i try to open ape files and it will open instead a prompt window in songbird asking which program to open the file with.

---

### Post by happyyasu09 on 2011-06-09
i don't know for songbird, but at least try this steps:
go here: [http://debian-multimedia.org/pool/main/m/monkeys-audio/monkeys-audio.php](http://debian-multimedia.org/pool/main/m/monkeys-audio/monkeys-audio.php)
and find two packages:
- libmac2
- monkeys-audio
for your architecture, install'em, after that restart your player, and try playing ape files. Rythmbox is playing them after installing those packages ;)

---

### Post by andrew.46 on 2011-06-09
Don't know much about songbird I'm afraid but MPlayer and its friends (SMPlayer, UMPlayer, GNOME MPLayer) should be able to play these files 'out of the box':

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep ape[/COLOR]**
ffape       ffmpeg    working   FFmpeg Monkey's Audio  [ape]

```

Playing a [sample ape file]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.ape") here:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer luckynight.ape [/COLOR]**
MPlayer SVN-r33574-4.5.3 (C) 2000-2011 MPlayer Team

Playing luckynight.ape.
libavformat file format detected.
[lavf] stream 0: audio (ape), -aid 0
Clip info:
 Track: 9
 Year: 1995
 Genre: Soundtrack
 Title: Lucky Night
 Artist: Jody Marie Gnant
 Album: Treasure Quest Soundtrack
 Comment: 1-minute song sample demonstrating Monkey's Audio .ape compression
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
**[COLOR="Red"]Selected audio codec: [ffape] afm: ffmpeg (FFmpeg Monkey's Audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  60.1 (01:00.1) of 60.4 (01:00.3)  2.6% 


Exiting... (End of file)

```

---

### Post by Yellow Pasque on 2011-06-10
I can play it in rhythmbox, which also uses gstreamer (like songbird).

---

