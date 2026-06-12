---
title: "Help!!"
date: 2007-05-20
forum: Multimedia Production
---

### Post by xstevex on 2007-05-20
i'm trying to get jack working. first of all, my mic doesnt work when i try to record. i've set it up, its not muted, i can hear it coming from my speakers when i type/talk into it/tap it, and yet it doesnt record anything

and to top it all of, yesterday i tried starting jackd and got this:

i'm running ubuntu studio.

15:11:51.080 Patchbay deactivated.
15:11:51.114 Statistics reset.
15:11:51.132 JACK is starting...
15:11:51.132 jackd -R -dalsa -r44100 -p1024 -n2 -D -Chw:0 -P/dev/dsp -i4
15:11:51.141 JACK was started with PID=12681 (0x3189).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
15:11:51.153 MIDI connection graph change.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|hw:0|1024|2|44100|4|0|nomon|swmeter|-|32bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: cannot set channel count to 4 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
15:11:51.385 Could not connect to JACK server as client. Please check the messages window for more info.
could not attach as JACK client (server has exited)
15:11:51.607 JACK was stopped successfully.
15:11:53.649 MIDI connection change.

---

### Post by lyall on 2007-05-20
Hi
I am using Kubuntu and Kmix you can use only one input at a time.
You might have the Mic set for input
You need to change the type of input to Line, Phone or Aux.
In Kmix you have to have to dark green button change to light green, to active that jack.
Then you can only use one at a time Mic, Video, Phone, or Aux.
The one that is active will be light red and the others will be dark red.
I found this out by testing them , to get sound to work so that I could record some old LP to CDs using Audacity.
I do not know what the equal is for Ubuntu or Studio.
I think I found it - QAMix in the in UbuntuStudio listing
You need to check the Capture tab
You then need to select the Capture Source. You has 8 choices.
You need to also the ccheck the Ext. Source Playback tab- they might have the Mute checked.

Good Luck and do not give up

---

### Post by kayosiii on 2007-05-24
Jack is not starting because you have too many input channels configured...

Have a look in the settings in qjackctl and drop the number of inputs from 4 to 2...

if you still have issues post back

---

