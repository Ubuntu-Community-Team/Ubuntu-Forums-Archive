---
title: "Jack Issues"
date: 2011-01-09
forum: Multimedia Software
---

### Post by tg103 on 2011-01-09
I have a clean Ubuntu 10.10 install

jackd --version gives: jackdmp 1.9.6

When I try to start jack I get the following:
16:14:02.829 ALSA connection graph change.
16:14:03.025 ALSA connection change.
16:14:07.401 Startup script...
16:14:07.402 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:14:07.804 Startup script terminated with exit status=32512.
16:14:07.805 JACK is starting...
16:14:07.805 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2
16:14:07.809 JACK was started with PID=2810.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
Cannot lock down memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdfffc000 irq 45
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery

which continues until it times out. 

My setup uses no parameters (no soft mode, no realtime, etc) and I have 1024 frames/period, 44100 sample rate, and 2 periods/buffer with a 500ms timeout. 

Any ideas?

---

### Post by cchhrriiss121212 on 2011-01-09
Jack works better in realtime mode. Open a terminal and do this:
```
sudo dpkg-reconfigure -p high jack && adduser "yourusername" audio
```
Agree to any modifications. Then reboot and start jack again with the realtime box checked.

---

### Post by tg103 on 2011-01-09
Note, I had to reconfig the package jackd2, not jack.

Seemed to get rid of some of the errors, but the messages still looks like:

18:33:19.005 Patchbay deactivated.
18:33:19.020 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
18:33:19.040 ALSA connection graph change.
18:33:19.236 ALSA connection change.
18:33:21.945 Startup script...
18:33:21.945 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
18:33:22.348 Startup script terminated with exit status=32512.
18:33:22.348 JACK is starting...
18:33:22.349 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
18:33:22.352 JACK was started with PID=1673.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdfffc000 irq 45
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle

---

### Post by tg103 on 2011-01-12
still can't figure this out, anyone have any ideas?

---

### Post by backu on 2011-05-23
Don't know if your still kicking around with this, but I would try some different settings in the Qjackctl, like the sample. Most keep sample at 48000 and it works quite well. Myself, I use No memory lock and Softwode with a 512 Frames/Period.. but then I'm also using all 6 channels of my sound card *grin*

---

