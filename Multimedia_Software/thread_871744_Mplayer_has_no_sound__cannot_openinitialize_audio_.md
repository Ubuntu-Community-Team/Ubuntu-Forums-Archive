---
title: "Mplayer has no sound : cannot open/initialize audio device"
date: 2008-07-27
forum: Multimedia Software
---

### Post by chineseli on 2008-07-27
it cannot play sound now but it can show video.

The software worked well after installation, but after rebooting, the problem came. 

My sound device works well, as I can play music using other software.

What should I do?

Thank you!

---

### Post by shirilover on 2008-07-27
You can try specifying the audio output by using any of the following in the command line switch:

-ao alsa or
-ao oss or
-ao sdl or
-ao pulse

---

### Post by panfist on 2008-11-12
I tried all of those options and I still can't get sound in mplayer.

---

### Post by andrew.46 on 2008-11-14
Hi,

Try the command:

```
$ mplayer -ao help
```

On my system this gives:

```
andrew@skamandros:~$ mplayer -ao help
MPlayer dev-SVN-r27904-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	arts	aRts audio output
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

```

And then you should be able to select one of these with the -ao option.

  Andrew

---

