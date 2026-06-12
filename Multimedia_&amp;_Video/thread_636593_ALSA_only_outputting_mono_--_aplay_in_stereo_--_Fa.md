---
title: "ALSA only outputting mono -- aplay in stereo -- Fast Track Pro"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by blue212 on 2007-12-10
Hi, 

I have a MAudio Fast Track Pro USB. It it recognized properly and shows up as USB Audio and USB Audio #1 in Gnome. The Fast Track Pro is actually two stereo dsp's in one unit hw:0,0 and hw:0,1

My problem is that when I play back audio from inside Gnome-> movie player, xmms, beep, totem, and so on, they all output MONO sound (at what seems like less than 44100 khz). It doesn't matter if I choose USB Audio or USB Audio #1

If I use aplay it outputs in stereo properly (the file s.wav is a stereo file with audio that shifts left->right)
```
:~$ aplay -D hw:0,0 s.wav
Playing WAVE 's.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

How do I get everything else to use stereo outputs?? The Fast Track Pro has external mixer controls, so there is no software mixer.

```
:~$ alsamixer
No mixer elems found

```

I am recently new to linux so (down with WINXP!!) ... small steps please

---

### Post by blue212 on 2007-12-10
speaker-test also works properly, but xmms, and other gnome applications still output mono

```
:~$ speaker-test -c2

speaker-test 1.0.14

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2229 to 17832
Period size range from 1114 to 1115
Using max buffer size 17832
Periods = 4
was set period_size = 1114
was set buffer_size = 17832
 0 - Front Left
 1 - Front Right

```

is there a config file somewhere that has settings for playback inside gnome? it doesn't matter what output device (ALSA or OSS) I use, it still only does mono playback inside Gnome

---

