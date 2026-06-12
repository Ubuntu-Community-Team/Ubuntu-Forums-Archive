---
title: "jack won't start with ASA"
date: 2008-12-12
forum: Multimedia Software
---

### Post by Colin@oxford on 2008-12-12
I can only get jACK to start if it uses OSS.  If I set the driver to ALSA, I get these messages:
[INDENT]
```

15:32:09.681 Patchbay deactivated.
15:32:09.750 Statistics reset.
15:32:09.780 ALSA connection graph change.
15:32:09.968 ALSA connection change.
15:32:16.959 Startup script...
15:32:16.960 artsshell -q terminate
15:32:17.573 Startup script terminated with exit status=256.
15:32:17.574 JACK is starting...
15:32:17.575 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3
15:32:17.577 JACK was started with PID=24023.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: got smaller periods 2 than 3 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
15:32:17.668 JACK was stopped successfully.
15:32:17.669 Post-shutdown script...
15:32:17.669 killall jackd
jackd: no process killed
15:32:18.086 Post-shutdown script terminated with exit status=256.
15:32:19.592 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```
[/INDENT]
What am I missing?  I'm on Hardy, if it makes any difference.

---

### Post by markbuntu on 2008-12-12
Most likely you are missing libasound2 and libasound2-plugins which you need for alsa to work with jack. You can get them with Synaptic or apt-get.

---

### Post by Colin@oxford on 2008-12-13
I had libasound, but not the plugins.  I added them, but get the same message.

---

### Post by markbuntu on 2008-12-13
You need to make sure that nothing else is trying to use the sound device.

---

### Post by Colin@oxford on 2008-12-13
I have just rebooted.  I have ESD switched off.  Jack does not start if using ALSA.  It does start if using OSS.

---

