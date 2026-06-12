---
title: "No sound in mplayer2: Can't open audio device /dev/dsp: No such file or directory"
date: 2015-08-27
forum: Multimedia Software
---

### Post by Daniyal_Javani on 2015-08-27
Hello
There is something wrong with my mplayer2 in Ubuntu 14.04 .
Could you please help me? You're my last hope!
For no sound problem this the output:
```
$ mplayer weary.mp3
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing weary.mp3.
libavformat version 54.6.100 (internal)
Audio only file format detected.
Load subtitles in ./
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
DVB card number must be between 1 and 4
AO: [null] 44100Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:   0.5 (00.5) of 0.7 (00.7)  0.4%                                            


Exiting... (End of file)
```
I have no alsa driver in mplayer:
```
$ mplayer -ao help
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
Available audio output drivers:
    oss    OSS/ioctl audio output
    mpegpes    DVB audio output
    v4l2    V4L2 MPEG Audio Decoder output
    null    Null audio output
    pcm    RAW PCM/WAVE file writer audio output
```
with oss driver:
```
$ mplayer Documents/Anki/User\ 1/collection.media/weary.mp3 -ao oss
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing Documents/Anki/User 1/collection.media/weary.mp3.
libavformat version 54.6.100 (internal)
Audio only file format detected.
Load subtitles in Documents/Anki/User 1/collection.media/
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)
```
```
$ mplayer Documents/Anki/User\ 1/collection.media/weary.mp3 -ao mpegpes
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing Documents/Anki/User 1/collection.media/weary.mp3.
libavformat version 54.6.100 (internal)
Audio only file format detected.
Load subtitles in Documents/Anki/User 1/collection.media/
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
DVB card number must be between 1 and 4
Failed to initialize audio driver 'mpegpes'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)
```
```
$ mplayer Documents/Anki/User\ 1/collection.media/weary.mp3 -ao v4l2
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing Documents/Anki/User 1/collection.media/weary.mp3.
libavformat version 54.6.100 (internal)
Audio only file format detected.
Load subtitles in Documents/Anki/User 1/collection.media/
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
Failed to initialize audio driver 'v4l2'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)
```
```
$ mplayer Documents/Anki/User\ 1/collection.media/allege.mp3 -ao pcm 
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing Documents/Anki/User 1/collection.media/allege.mp3.
libavformat version 54.6.100 (internal)
Audio only file format detected.
Load subtitles in Documents/Anki/User 1/collection.media/
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format floatle
[AO PCM] Info: Faster dumping is achieved with -benchmark -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:   0.9 (00.8) of 0.9 (00.8)  0.2%                                             


Exiting... (End of file)
```
There is nothing in "Software & Updates" -> "Additional drivers" !

---

### Post by Yellow Pasque on 2015-08-27
Where did you get your version of mplayer/mplayer2? It wasn't even built with support for ALSA or mpg123 like the stock 14.04 version. It seems like the person that built it was not real experienced with building from source.
```
apt-cache policy mplayer mplayer2
```

---

### Post by Daniyal_Javani on 2015-08-27
> **Temüjin said:**
> Where did you get your version of mplayer/mplayer2? It wasn't even built with support for ALSA or mpg123 like the stock 14.04 version. It seems like the person that built it was not real experienced with building from source.
```
apt-cache policy mplayer mplayer2
```

```
$ sudo apt-cache policy mplayer mplayer2
mplayer:
  Installed: (none)
  Candidate: 2:1.1+svn37434~trusty
  Version table:
     2:1.1+svn37434~trusty 0
        500 http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.1+dfsg1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
mplayer2:
  Installed: 2.0-701-gd4c5b7f-2ubuntu2
  Candidate: 2.0-701-gd4c5b7f-2ubuntu2
  Version table:
 *** 2.0-701-gd4c5b7f-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```
So what should I do now?

Thanks for your attention.

---

### Post by mc4man on 2015-08-28
> **Daniyal_Javani said:**
> ```

mplayer2:
  [COLOR="#0000CD"]Installed: 2.0-701-gd4c5b7f-2ubuntu2[/COLOR]
  Candidate: 2.0-701-gd4c5b7f-2ubuntu2
  Version table:
 *** 2.0-701-gd4c5b7f-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

That & this don't jive up, - 

> **Daniyal_Javani said:**
> mplayer -ao help
[COLOR="#FF0000"]MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team[/COLOR]
Available audio output drivers:
    oss    OSS/ioctl audio output
    mpegpes    DVB audio output
    v4l2    V4L2 MPEG Audio Decoder output
    null    Null audio output
    pcm    RAW PCM/WAVE file writer audio output

Here - with mplayer2 installed (14.04),
> ~$ mplayer -ao help
[COLOR="#0000CD"]MPlayer2 2.0-701-gd4c5b7f-2ubuntu2[/COLOR] (C) 2000-2012 MPlayer Team
Available audio output drivers:
	pulse	PulseAudio audio output
	alsa	ALSA-0.9.x-1.x audio output
	oss	OSS/ioctl audio output
	jack	JACK audio output
	sdl	SDLlib audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output
Do you have an old mplayer binary somewhere in your $PATH?

If so get rid of, then 
sudo apt-get purge mplayer2
sudo apt-get install mplayer

run /usr/bin/mplayer to ck., against mplayer in terminal, should produce same as in :
~$ mplayer
MPlayer SVN-r37401 (C) 2000-2012 MPlayer Team

---

### Post by Yellow Pasque on 2015-08-28
Are you sure that you didn't build/install  a local copy?
```
which mplayer
```

---

### Post by Daniyal_Javani on 2015-08-28
WoW!
Thank you so much!
You solve my old and big problem.
And you solve my another problem [http://ubuntuforums.org/showthread.php?t=2282941&page=2](http://ubuntuforums.org/showthread.php?t=2282941&page=2)
Really thanks!

---

