---
title: "mplayer: could not connect to socket ?"
date: 2014-03-26
forum: Multimedia Software
---

### Post by vasa1 on 2014-03-26
```
[11:12 AM] ~ $ mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga
mplayer: could not connect to socket
mplayer: No such file or directory
[11:12 AM] ~ $
```
The sound plays all right but what does the screen output mean? And why do I see these messages (or errors)?

---

### Post by andrew.46 on 2014-03-26
If you take out the *-really-quiet* option there should be a few more hints. I suspect it may be an lirc warning...

---

### Post by vasa1 on 2014-03-26
> **andrew.46 said:**
> If you take out the *-really-quiet* option there should be a few more hints. I suspect it may be an lirc warning...

```
[02:04 PM] ~ $ mplayer /usr/share/sounds/freedesktop/stereo/complete.ogaMPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /usr/share/sounds/freedesktop/stereo/complete.oga.
Detected file format: Ogg (libavformat)
[lavf] stream 0: audio (vorbis), -aid 0
Load subtitles in /usr/share/sounds/freedesktop/stereo/
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] Init failed: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.1 (01.0) of 1.1 (01.0)  0.9% 


Exiting... (End of file)
[02:04 PM] ~ $ 
```That's after dropping the **-really-quiet** option. Is that helpful?

---

### Post by andrew.46 on 2014-03-26
Perhaps try adding the following to your *$HOME/.mplayer/config* file:

```

lirc=no

```

and try again...

---

### Post by vasa1 on 2014-03-26
Perfect. Thank you!

Marked it [SOLVED]

---

### Post by andrew.46 on 2014-03-26
Good to see the issue is resolved :)

---

