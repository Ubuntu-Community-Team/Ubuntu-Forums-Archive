---
title: "mplayer could not initialize audio device -&gt; no sound"
date: 2008-10-18
forum: Multimedia Software
---

### Post by jithin1987 on 2008-10-18
When I open a video file from dolphin I get this error cannot initialize audio device no sound
But when i invoke it from terminal it plays with sound. Can anyone help me out?
I use kubuntu 8.10 beta.
-- Regards
Jithin Emmanuel

---

### Post by jithin1987 on 2008-10-19
Actually mplayer is working fine. Its gmlayer which is causing the problem.
When from terminal mplayer works correctly there is proper sound.
But if I issue gmplayer there is no sound.

---

### Post by anubhavrocks on 2008-10-19
I guess you should change the gmplayer settings and see what works.

---

### Post by Dufangoer on 2008-10-19
&#12288;&#12288;A Jewish guy rings his mother. She picks up the phone and says 'Hello'. &#12288;&#12288;He says 'Hi, how are you?' &#12288;&#12288;'Fine', she says. &#12288;&#12288;'Sorry', he says, 'I must have the wrong number'. cheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

### Post by jithin1987 on 2008-10-20
I set audio to alsa and it's working . Why is it not working with pulse audio. Is there any fix?

---

### Post by andrew.46 on 2008-10-21
Hi,

Well it *can* be done as I demonstrate below with an Ubuntu 'sample' file:

```
andrew@skamandros:/usr/share/example-content$  mplayer -ao pulse fables_01_01_aesop.spx
MPlayer dev-SVN-r27800-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing fables_01_01_aesop.spx.
[Ogg] stream 0: audio (Speex), -aid 0
Ogg file format detected.
==========================================================================
Opening audio decoder: [speex] Speex audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->88200)
Selected audio codec: [speex] afm: speex (Speex Audio Decoder)
==========================================================================
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  -0.6 (unknown) of inf (-24.-8)  1.7% 

Exiting... (End of file)

```

But the trick is that your copy of MPlayer has to have been compiled the right way. You can see what audio output options are available to you by using the following method:

```
andrew@skamandros:~$ mplayer -ao help 
MPlayer dev-SVN-r27800-4.3.2 (C) 2000-2008 MPlayer Team
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

andrew@skamandros:~$ 

```

I am using a compiled copy of the svn MPlayer under Intrepid Ibex.

  Andrew

---

### Post by jithin1987 on 2008-10-21
When I try that I am getting error
AO: [pulse] Failed to connect to server: Connection refused
Could not open/initialize audio device -> no sound.
Audio: no sound

---

### Post by anubhavrocks on 2008-10-24
Go to System->Prefrences->Sound
Here In SOunds tab check the ESD option.
Also make sure pulse server is actually running.

---

### Post by jithin1987 on 2008-10-31
with pulse i am getting the error. I switched to alsa. Now its working.
May be pulse is broken with mplayer.

---

