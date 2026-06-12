---
title: "mplayer won't play ogg file - have codec"
date: 2013-10-11
forum: Multimedia Software
---

### Post by uh-huh on 2013-10-11
```
$ ogginfo Music/various-speedo.ogg
Processing file "Music/various-speedo.ogg"...

New logical stream (#1, serial: 57378e5f): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: Xiphophorus libVorbis I 20010615 (1.0 rc1)
Channels: 2
Rate: 44100

Nominal bitrate: 128.000000 kb/s
Upper bitrate not set
Lower bitrate not set
User comments section follows...
	title=Speedo
	artist=various
	date=1999
	album=RnB56
	tracknumber=13
Vorbis stream 1:
	Total data length: 2337983 bytes
	Playback length: 2m:23.333s
	Average bitrate: 130.492074 kb/s

```

But 
```
$ mplayer Music/various-speedo.ogg
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not open config files /home/cordyceps/.lircrc and /etc/lirc/lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.

Playing Music/various-speedo.ogg.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: audio (vorbis), -aid 0, Speedo
No stream found.


Exiting... (End of file)

```

VLC plays ogg files but I prefer mplayer.

---

### Post by SeijiSensei on 2013-10-11
I'm not sure where you got that version of mplayer, but current Ubuntu versions ship with [mplayer2](http://www.mplayer2.org).  There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/libav/+bug/992971") for "Mismatching header version 53.19.0" filed at launchpad, but the problem was dismissed as something that needed to be dealt with by the mplayer authors.

I suggest uninstalling and reinstalling mplayer and confirming that mplayer2 was installed.  You can tell by the header when you run mplayer from the command line.  On my 13.10 machine, I can play audio and video Ogg Vorbis files without problem.

```

$ mplayer file.ogg
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.ogg.
Detected file format: Ogg (libavformat)
[lavf] stream 0: audio (vorbis), -aid 0, &#20104;&#20806;
Load subtitles in .
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 112.0 kbit/7.94% (ratio: 14000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   8.8 (08.7) of 101.5 (01:41.5)  0.4% 

```

---

### Post by uh-huh on 2013-10-11
mplayer2 doesn't play anything:( I pointed it at a playlist and got a string of these:

 ```
Detected file format: MPEG audio layer 2/3 (libavformat)
[mp3 @ 0x27783a0]max_analyze_duration reached
[mp3 @ 0x27783a0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (mp3), -aid 0
No stream found
```

Same for direct play of individual tunes.

I used Synaptic Pkg Mgr. Maybe should have used command line? 

Note: I always update whenever the red update icon appears in the lower corner of the desktop.

---

### Post by mc4man on 2013-10-12
If there was any way to provide a sample of a troublesome ogg could take a look at 
(the binary used to encode your file is a bit aged but really shouldn't be an issue with mplayer though hard to say from afar.

(I keep fairly current mplayer builds that use FFmpeg (internal) in ppa for precise, raring &  saucy if you wanted to try...

---

### Post by andrew.46 on 2013-10-12
Interesting.... does *ogg123* play the file for you?

---

### Post by SeijiSensei on 2013-10-14
> **uh-huh said:**
> mplayer2 doesn't play anything:( I pointed it at a playlist and got a string of these:

 ```
Detected file format: MPEG audio layer 2/3 (libavformat)
[mp3 @ 0x27783a0]max_analyze_duration reached
[mp3 @ 0x27783a0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (mp3), -aid 0
No stream found
```


This thread originally concerned files file encoded in Ogg Vorbis, but these errors are about MP3.  For that format, which is encumbered by patents, you need to install **ubuntu-restricted-extras** (or the version for your flavor of Ubuntu like kubuntu-restricted-extras).

---

