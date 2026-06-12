---
title: "spdif audio with nforce4 Ubuntu Hardy only stereo and not ac3 5.1"
date: 2008-08-09
forum: Multimedia Software
---

### Post by cioccolato on 2008-08-09
I cannot make working my ac3 spdif in 5+1 in Ubuntu! >:(
It run only in 2.0!

I have checked many many guides without success.  :'(

This is my configuration:

integrated soundboard with chip nforce4 and SPDIF coaxial output.
My aplay-l:

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In VLC I can see Ac3 trough A52 but I dont hear nothing... should I configure A52? Where? What I must do?

:'(

---

### Post by markbuntu on 2008-08-09
If you have a surround sound card and the surround is not working but you get front speaker output, 
edit etc/pulse/daemon.conf and change the line:

```

default-sample-channels = 2

```
to
```

default-sample-channels =5

```

for 4.1surround or 6 for 5.1 surround or 8 for 7.1 surround.

---

### Post by cioccolato on 2008-08-09
OK, I have set 6 (I have a 5+1 set from Creative connected with a coaxial cable.

Now I see 5+1 but at the end is allways 2.0 and when I set 5+1 I cannot hear the center channel (and probably the back channels are replicated).

](*,)

---

### Post by markbuntu on 2008-08-09
Check in the mixer that you have all the channels turned up. For many cards the center and rear speakers are separate in the mixer. 

I use the gnome-alsamixer myself, it is very convenient and far easier to use than alsamixer from the command line.

---

### Post by cioccolato on 2008-08-11
Already done... with alsamixer. :(

---

### Post by jocko on 2008-08-11
> **cioccolato said:**
> In VLC I can see Ac3 trough A52 but I dont hear nothing... should I configure A52? Where? What I must do?
A52 is an ac3 decoder, which means it will take a digital ac3 sound stream and convert it to an analog sound stream (and often downmix to stereo unless you have set up alsa to use 6 channels by default). If you want to output ac3 directly to your external reciever, you need to make sure vlc use s/pdif passthrough, not decoding.
Open up the settings window in vlc, and in  the sound tab, activate "Use S/PDIF if available" and set "Force identification of Dolby Surround" to "Auto" or "On".
In mplayer, you need to make sure the preferred audio codec family is set to "hwac3", otherwise it will be decoded with a52.

---

### Post by cioccolato on 2008-08-11
> **jocko said:**
> If you want to output ac3 directly to your external reciever, you need to make sure vlc use s/pdif passthrough, not decoding.
Open up the settings window in vlc, and in  the sound tab, activate "Use S/PDIF if available" and set "Force identification of Dolby Surround" to "Auto" or "On".

In mplayer, you need to make sure the preferred audio codec family is set to "hwac3", otherwise it will be decoded with a52.

1) Already done in VLC without effect :(
2) In mplayer I have only:

Available audio output drivers (what is the right?!):
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

and codec: AC3/DTS passtrough maybe?

---

### Post by jocko on 2008-08-11
> **cioccolato said:**
> 
and codec: AC3/DTS passtrough maybe?
Yep. That's the one. It should work.
Otherwise try to run it from a terminal like this:
```
mplayer -ao alsa -afm hwac3 [COLOR=Blue]filename[/COLOR]
```, where filename is a video file with ac3 surround sound.

I just tried vlc with the settings I gave you and by some reason it still used a52 for me too... I'll see if I can figure it out...
Edit: Just started vlc from a command line:
```
vlc --spdif [COLOR=Blue]filename[/COLOR]
```and by some reason it now works, even when I start vlc without adding the --spdif option (the command line still says the audio stream is decoded by a52, but if I right click the video window and go to the audio device menu entry I can see that it uses "A/52 over S/PDIF").

---

### Post by cioccolato on 2008-08-11
I hear nothing... :-(
(with vlc only a big "SCREATTCH" when the play begin).

```
mplayer -ao alsa -afm hwac3 test.ac3
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.ac3.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Forced audio codec: mad
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Video: no video
Starting playback...
A:   9.0 (08.9) of 9.3 (09.2)  0.1% 

Exiting... (End of file)
```

```
vlc --spdif test.ac3
VLC media player 0.8.6e Janus
[00000315] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000341] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000283] main playlist: nothing to play
[00000283] main playlist: stopping playback

```

Motherboard: Asus A8N-SLI with integrated soundboard and coaxial out (chip nforce4)
The coaxial port is connected trough a cable to a DD decoder (Creative - Cambridge Soundworks DTT2500 )

With the movie player and the setting "ac3", it switchs to 5+1 and then play

front left = ok
center= trough left & right
front right = ok
back left = from front left
back right = from front right
lfe = dont know! (but I hear something).
front righ

---

### Post by zsolt320i on 2008-10-13
Hy,

a very simple solution for Dolby with optical connection:
- install smplayer
- then go to option/settings/general and at the sound choose OSS
- save&restart
and the dolby should work!

Have fun!



> **cioccolato said:**
> I cannot make working my ac3 spdif in 5+1 in Ubuntu! >:(
It run only in 2.0!

I have checked many many guides without success.  :'(

This is my configuration:

integrated soundboard with chip nforce4 and SPDIF coaxial output.
My aplay-l:

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In VLC I can see Ac3 trough A52 but I dont hear nothing... should I configure A52? Where? What I must do?

:'(

---

