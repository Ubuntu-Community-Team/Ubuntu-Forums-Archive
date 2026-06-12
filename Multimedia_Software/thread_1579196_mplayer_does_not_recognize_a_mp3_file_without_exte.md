---
title: "mplayer does not recognize a mp3 file without extension"
date: 2010-09-21
forum: Multimedia Software
---

### Post by GeoMX on 2010-09-21
When trying to play a MP3 file without extension, mplayer shows this message:

> 
$ mplayer file
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.
MPEG-PES file format detected.
MPEG: No audio stream found -> no sound.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
No stream found.


Exiting... (End of file)

If renaming it to file.mp3, it plays correctly:

> 
$ mv file file.mp3
$ mplayer file.mp3 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.mp3.
Audio only file format detected.
Clip info:
 Title: Track 01
 Artist: Unknown
 Album: Unknown
 Year: 
 Comment: 
 Track: 8
 Genre: Other
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  11.2 (11.2) of 188.0 (03:08.0)  0.4% 
Exiting... (Quit)

It does not happen with all the files I've tested, but only some of them, is there an option to indicate mplayer that the file is actually in mp3 format?

Thanks in advance for your help.

---

### Post by andrew.46 on 2010-09-21
Hi Geo,

You could try forcing the audio codec:

```
mplayer -ac mp3 filename
```

or perhaps even:

```
mplayer -audio-demuxer 17 filename
```

Unfortunately I could not test this as MPlayer recognised all of my mp3s even with the .mp3 :(.

Andrew

---

### Post by GeoMX on 2010-09-22
The files I'm trying to play are the result of a previous processing, this process takes any media file as input, and outputs a file without extension letting mplayer guess the format, I used to think the processing did not alter the files, but now I have realized it may be the cause of the problem, so I have to work with this first, thanks for your help.

---

