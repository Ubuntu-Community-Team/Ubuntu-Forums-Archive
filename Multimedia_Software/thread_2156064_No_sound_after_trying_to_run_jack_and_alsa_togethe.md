---
title: "No sound after trying to run jack and alsa together"
date: 2013-06-20
forum: Multimedia Software
---

### Post by rva1945 on 2013-06-20
I followed these guidelines in both a desktop PC and a laptop (both running 12.04), it didn't work in the laptop:

aptitude search pulseaudio

sudo aptitude install pulseaudio-module-jack

sudo gedit /etc/pulse/default.pa

(added these lines where it says "### Load audio drivers statically...", under #load-module module-pipe-sink):

load module module-jack-sink
load module module-jack-source
(save)

The next step was killing Pulseaudio, I forgot it and restarted the system. Now there is no sound controls, I mean, no input and output devices in sound settings, but I can hear an mp3 or even an internet video.  I tried killall pulseaudio PulseAudio but
[COLOR=#000000][FONT=liberation sans]
[/FONT][/COLOR]pulseaudio: no process found
PulseAudio: no process found

ps -e doesn't list pulseaudio at all

In Sound Settings, no input, no output device. I run Qjackctl and Guitarix and Rakarrack work, but then no other sound (I need to play an mp3 while playing the guitar). If I delete those both lines in default.pa and restart the system, the sound comes back.

I don't know if this is useful or not: I tried pulseaudio in terminal


E: [pulseaudio] main.c: Unknown command: load module module-jack-sink
E: [pulseaudio] main.c: Failed to initialize daemon.


So?

---

