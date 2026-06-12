---
title: "No sound in mplayer"
date: 2010-11-22
forum: Multimedia Software
---

### Post by mikeserv on 2010-11-22
So I'm running Ubuntu 10.10 64-bit on an HP Mini 210-1190NR. Everything runs fine except mplayer. I installed mplayer from the repos but when I try to play a video I get no sound. I can't figure out why.

Here's the output:
```
mplayer star.wars.the.clone.wars.s03e10.720p.hdtv.x264-ctu.mkv 
MPlayer SVN-r32636-4.4.5 (C) 2000-2010 MPlayer Team
160 audio & 350 video codecs

Playing star.wars.the.clone.wars.s03e10.720p.hdtv.x264-ctu.mkv.
Cache fill:  3.12% (262144 bytes)   

libavformat file format detected.
[matroska,webm @ 0x22324c0] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (ac3), -aid 0
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  1280x720  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Cache not responding!
Cache not responding!
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
DVB card number must be between 1 and 4
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12  [fs]
A:   0.7 V:   0.7 A-V:  0.000 ct: -0.000   0/  0 143% 23%  2.6% 4 0 1%                                                                                                                                          

Exiting... (Quit)

```

And this: 
```
mplayer -ao help
MPlayer SVN-r32636-4.4.5 (C) 2000-2010 MPlayer Team
160 audio & 350 video codecs
Available audio output drivers:
	oss	OSS/ioctl audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

Anybody got any ideas?
I've got sound everywhere else in the system, just not in mplayer, and I need mplayer because most of my videos are 720p .mkv and this netbook sucks at playing them.

-Mike

---

### Post by SeijiSensei on 2010-11-22
> **mikeserv said:**
> 
```
mplayer -ao help
MPlayer SVN-r32636-4.4.5 (C) 2000-2010 MPlayer Team
160 audio & 350 video codecs
Available audio output drivers:
	oss	OSS/ioctl audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

If that's really from the repositories, I don't understand why it doesn't have alsa and pulse as audio outputs.  Ubuntu 10.10 uses pulseaudio by default, so you need the pulse driver, or you need to convert your Ubuntu to OSS.  I did that once a year or so ago; I'd suggest trying a different route!

I build mplayer from source so I can't help you with the repository versions.  However you might consider adding [this PPA]("https://launchpad.net/~rvm/+archive/ppa"), then installing mplayer (and, I'd recommend, smplayer), and see if you have better success.  

If you've got some experience with compilation, you can roll your own mplayer.  Try [this thread](http://ubuntuforums.org/showthread.php?t=1542240) or follow the instructions I gave [here]("http://ubuntuforums.org/showpost.php?p=10106966&postcount=10").

---

### Post by mc4man on 2010-11-22
Some builds of mplayer seem to default to oss as the -ao, and oss is no longer usable/enabled in 10.10 even if you have the alsa-oss package installed.
From the cli just use -ao pulse or -ao alsa.

(though you could do this, no advantage, wouldn't bother, more useful for apps that must use oss
padsp mplayer <whatever>

Or just go to ~/.mplayer/config and add an ao line
Ex. for pulse
> # Write your default config options here!
ao=pulse

---

### Post by SeijiSensei on 2010-11-22
> **mc4man said:**
> Or just go to ~/.mplayer/config and add an ao line

I don't think that will help since "-ao help" doesn't show that a pulse driver is compiled into the mplayer binary.

---

### Post by mc4man on 2010-11-22
> I don't think that will help since "-ao help" doesn't show that a pulse driver is compiled into the mplayer binary.
Hmm I did miss that - saw he's saying installed from repo's which, due to the svn # seemed likely to be the mplayer daily ppa ( current svn SVN-r32636

I can't imagine it ( any any ppa) building mplayer without pulse and alsa support and having a dep on libasound2 and libpulse0

Ex. here ( from daily ppa
>  mplayer -ao help
MPlayer [COLOR="Blue"]SVN-r32636[/COLOR]-4.4.5 (C) 2000-2010 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	nas	NAS audio output
	sdl	SDLlib audio output
	openal	OpenAL audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

I'd say give it a try from cli and see what happens

Worst case as mentioned - 
> $ padsp mplayer -ao oss '/home/doug/Desktop/03 - Cheap Day Returns.ogg' 
MPlayer SVN-r32636-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Desktop/03 - Cheap Day Returns.ogg.
libavformat file format detected.
[lavf] stream 0: audio (vorbis), -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   8.6 (08.5) of 85.4 (01:25.4)  0.4%

---

### Post by tg_nightnight on 2012-03-06
My solution was simple.  My video for mplayer was fine, but there was no sound. I thought that maybe the volume was set to 'low' or mute for some reason, and I eventually found that I was right.  I looked up the volume controls in the mplayer man & that solved my problem for my purposes.  From mplayer manual:

              + and -
                   Adjust audio delay by +/- 0.1 seconds.
              / and *
                   Decrease/increase volume.
              9 and 0
                   Decrease/increase volume.
              ( and )
                   Adjust audio balance in favor of left/right channel.
              m
                   Mute sound.

You can also modify volume for each application in ubuntu independently by going:
Ubuntu Sound Control -> Sound Preferences -> Application tab
and adjusting each applications' volume independently of the system/main volume.

---

### Post by nothingspecial on 2012-03-06
Thank you for the information but this thread is old.

Closed.

---

