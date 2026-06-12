---
title: "JACK doesn't want to start in 44.1 kHz"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by bramvandijk on 2007-01-16
Hi,
I want to use Ardour with 44.1 kHz sample rate.
Ardour takes its sample rate from Jack, thus I need to start Jack with a sample rate of 44.1kHz.

With qjackctl I put the Sample Rate at 44100 and then when I start Jack, I get the following output:

> 
21:01:40.208 Startup script terminated with exit status=32512.
21:01:40.208 JACK is starting...
21:01:40.208 jackd -R -P2 -dalsa -dhw:0 -r44100 -p128 -n2 -S
21:01:40.226 JACK was started with PID=5965 (0x174d).
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
21:01:42.372 Server configuration saved to "/home/jongetje/.jackdrc".
21:01:42.373 Statistics reset.
21:01:42.391 Client activated.
21:01:42.410 Audio connection change.
21:01:42.418 Audio connection graph change.

Which seems to give a sample rate of 44100, but in fact I get a sample rate of 48000](*,) .
It is probably something vary simple, but I don't know.

---

### Post by sgx on 2007-01-16
try starting jackd with this command:

jackd -d alsa -r 44100

...then start qjackctl, and change its default setting
from 48000 to 44100. Reboot, and try starting jackd
from qjackctl, and see if the change is in effect.
Hope this helps...

---

### Post by bramvandijk on 2007-01-17
Thanks, but no luck. The weird thing is that Jack starts, and says 

> jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for playback


so, it would seem indeed Jack starts with a sample rate of 44100 Hz, but when I start either Ardour, or qjackctl, they tell me that Jack has sample rate 48000. Could this be a bug in Jack?

---

### Post by brainstuff on 2008-07-23
Hey, same thing happening here. What soundcard you using? I'm just mucking about with Ubuntu Studio on my lounge PC (onboard AC97 - argh!), but I'm seriously thinking about sticking it on my music machine. Just hope it's more stable with my EMU :)

---

