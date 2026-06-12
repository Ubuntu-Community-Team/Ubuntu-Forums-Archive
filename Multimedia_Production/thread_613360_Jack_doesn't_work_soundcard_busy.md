---
title: "Jack doesn't work: soundcard busy"
date: 2007-11-14
forum: Multimedia Production
---

### Post by ciacnorris on 2007-11-14
After having worked for a few sessions, JACK has stopped working.
When I try starting it whith Qjackctl it says that the soundcard is busy, probably in use by another program. I tried killing some programs and disabling esd, but without any result.
Please help me!

---

### Post by Stochastic on 2007-11-14
what programs are listed as running in system monitor?

---

### Post by ciacnorris on 2007-11-15
I don't understand... now the error message has changed. I copy and paste from QJackCtl's "Messages" window:

```
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
01:13:05.496 Server configuration saved to "/home/myuser/.jackdrc".
01:13:05.501 Statistics reset.
01:13:05.543 Client activated.
01:13:05.548 Audio connection change.
01:13:05.561 Audio connection graph change.
JACK tmpdir identified as [/dev/shm]
Enhanced3DNow! detected
SSE2 detected
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
01:13:08.758 Shutdown notification.
01:13:08.762 Client deactivated.
01:13:08.768 JACK was stopped successfully.
01:13:08.769 Post-shutdown script...
01:13:08.770 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
01:13:09.006 Post-shutdown script terminated with exit status=256.
```
What does this mean?

---

