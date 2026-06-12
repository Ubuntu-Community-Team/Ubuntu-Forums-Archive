---
title: "PulseAudio: choppy sound playing MONO MP3 files (e. g. audio books)"
date: 2013-10-27
forum: Multimedia Software
---

### Post by syntaxerror74 on 2013-10-27
Hello, you can see my (sub-)distro on the right, although I guess it won't really be relevant here...

This issue is definitely related to PulseAudio dealing with **mono** MP3 files ONLY.
And it should be tested always with a **speech** file, not with music, as otherwise you might not hear the difference to what it should sound normally. Plus, there might probably only be a handful of cases where you *would* really keep music in mono, e. g. for some early 1930s/40s...

For testing this, you will need a MONO mp3 file with speech and no music. A cookie-cutter audio book with one narrator and no background audio will be perfect (no, refrain from audio dramas)
The following things will occur:

- File will play absolutely flawlessly for one minute or more.
- Just out of thin air, audio will get as choppy as sounding like an old tape recording with the tape broken...
- "Rewinding" just a few seconds will get the sound back in sync ... until the next problem occurs (it surely will!)

The problem is perfectly reproducible in an on/off-switch fashion, not only on media-playing software, but even on console:

```
$ mplayer -ao alsa monofile.mp3
```
-> PERFECT

```
$ mplayer -ao pulse monofile.mp3
```
-> [COLOR=red]choppy audio![/COLOR]

```
$ mplayer -ao pulse stereofile.mp3
```as well as
```
$ mplayer -ao alsa stereofile.mp3
```
-> BOTH PERFECT

Unfortunately, I have no idea what happens, since deadbeef doesn't let me inspect my audio backend that it uses at deeper debug level.
Am I the only one who has experienced this problem?

Related issue: (claimed to be "fixed")
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/419271](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/419271)

---

### Post by dotancohen on 2014-08-28
I can confirm this issue. This is the choppy file:

```

$ mplayer Zz86ME2dJne1nY1.wav
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Zz86ME2dJne1nY1.wav.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
Audio only file format detected.
Load subtitles in ./
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11025->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 11025Hz 1ch u8 (1 bytes per sample)
Video: no video
Starting playback...
A:   0.1 (00.1) of 0.8 (00.8) ??,?% 
Audio device got stuck!
A:   0.1 (00.1) of 0.8 (00.8)  0.0% 
Audio device got stuck!
A:   0.5 (00.4) of 0.8 (00.8)  0.0% 


Exiting... (End of file)

```


This is the non-choppy file:
```

$ mplayer /home/dotancohen/test.wav 
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/dotancohen/test.wav.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
Audio only file format detected.
Load subtitles in /home/dotancohen/
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  39.2 (39.1) of 185.0 (03:05.0)  0.1% 


MPlayer interrupted by signal 2 in module: play_audio
A:  39.3 (39.3) of 185.0 (03:05.0)  0.1% 

Exiting... (Quit)

```

---

### Post by dotancohen on 2014-08-28
The forum software would not let me attach the example .wav file, so here it is on an example site:
[http://www.filedropper.com/zz86me2djne1ny1](http://www.filedropper.com/zz86me2djne1ny1)

---

