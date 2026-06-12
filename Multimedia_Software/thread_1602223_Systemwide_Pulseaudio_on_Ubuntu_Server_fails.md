---
title: "Systemwide Pulseaudio on Ubuntu Server fails"
date: 2010-10-21
forum: Multimedia Software
---

### Post by PureW on 2010-10-21
Hello

I'm building myself a light htpc with Ubuntu 10.10 Server without Gnome, but with XBMC and I'd like the ability to stream sound from my other computers to the htpc which is connected to the soundsystem.

But I can't get it to work. Alsa (before I started with Pulseaudio) played the sound from Xbmc. After that I installed pulseaudio, removed my user from the audio-group and added myself to the pulse-access-group. I also tried to set the default alsa-device to pulse (see attached .asoundrc at the bottom) since the default setup didn't work for me.

When I try to play a sound file, I get this error message.
> $ ogg123 ACDC_-_Back_In_Black-sample.ogg 
ERROR: Failed to load plugin /usr/lib/ao/plugins-4/libesd.so => dlopen() failed

Audio Device:   Advanced Linux Sound Architecture (ALSA) output

Playing: ACDC_-_Back_In_Black-sample.ogg
Ogg Vorbis stream: 2 channel, 48000 Hz
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ao_alsa ERROR: Unable to open ALSA device 'default' for playback => Connection refused
ERROR: Cannot open device alsa.


Something that is strange (to me) is that even when I tell pulseaudio that it is oke to load modules, pulseaudio tells me that --disallow-module-loading is not set.
> $ sudo pulseaudio **--disallow-module-loading=0**
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, **but --disallow-module-loading not set!**
N: main.c: Running in system mode, forcibly disabling exit idle time!
W: main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
W: main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
W: main.c: Please read [http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode](http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode) for an explanation why system mode is usually a bad idea.
W: module.c: module-detect is deprecated: Please use module-udev-detect instead of module-detect!



Some files:
/etc/pulse/daemon.conf [http://pastebin.com/XQPzpKPy](http://pastebin.com/XQPzpKPy)
.asoundrc [http://pastebin.com/5jwiZtjR](http://pastebin.com/5jwiZtjR)

---

### Post by PureW on 2010-10-21
The reason I'm trying to use Pulseaudio as a system-wide instance is because I made it work in 10.04 somehow but I'm not sure how anymore.

And I'm not sure which settings to edit when it is running configured for per-user-sessions.

---

### Post by PureW on 2010-10-23
I'm now trying to run pulseaudio from my user. And I can play a sound from inside the pulseaudio command line:
> $ pulseaudio -C
Welcome to PulseAudio! Use "help" for usage information.
>>> play-file /home/anders/Strings.wav 0
>>> 

But when I try to play from the outside, from normal applications, i just get:
> $ aplay Strings.wav -d pulse
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

aplay: main:654: audio open error: Connection refused


**EDIT: I get the same connection refused regardless if pulse is running or not, what should I do?**

---

