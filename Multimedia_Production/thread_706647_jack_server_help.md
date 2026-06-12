---
title: "jack server help"
date: 2008-02-24
forum: Multimedia Production
---

### Post by secondstage on 2008-02-24
Whenever I start jack, it will count to 1 second, and then an error comes up saying
"Could not connect to JACK server as client. Please check the messages windows for more info."

The messages say:

16:39:04.245 Patchbay deactivated.
16:39:04.251 Statistics reset.
JACK tmpdir identified as [/dev/shm]
16:39:04.286 MIDI connection graph change.
16:39:04.458 MIDI connection change.
16:39:05.923 Startup script...
16:39:05.924 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/john/.kde/socket-john.
16:39:06.143 Startup script terminated with exit status=256.
16:39:06.143 JACK is starting...
16:39:06.143 /usr/bin/jackd -dalsa -ddefault -r44100 -p1024 -n2
16:39:06.144 JACK was started with PID=6889 (0x1ae9).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... default|default|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
16:39:06.182 JACK was stopped successfully.
16:39:06.182 Post-shutdown script...
16:39:06.182 killall jackd
jackd: no process killed
16:39:06.389 Post-shutdown script terminated with exit status=256.
16:39:08.275 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

Any help would be greatly appreciated!

---

### Post by pdxken on 2008-02-24
Hi secondstage.
I am trying to get this stuff to work too. I got the same message.

After fiddling for a while I finally went into jack setup and changed frames/period from 1025 to 512 and jack started. I suspect a lower number may be ever better. Don't remember why.

Don't have a clue how all this stuff works but was happy to at least get jack started.

Ken.:popcorn:

---

### Post by secondstage on 2008-02-25
works perfectly thanks :popcorn:

---

