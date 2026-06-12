---
title: "JACK help please"
date: 2007-12-07
forum: Multimedia Production
---

### Post by daka on 2007-12-07
I have been trying for a while to get Rosegarden working.. but no success.. seems to have something to do with JACK.....Last time I tried to run Ardour I got this panel of messages:

19:50:54.609 Patchbay deactivated.
19:50:54.824 Statistics reset.
19:50:54.871 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
19:50:55.031 MIDI connection change.
19:50:57.615 Startup script...
19:50:57.615 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
19:50:58.674 Startup script terminated with exit status=256.
19:50:58.697 JACK is starting...
19:50:58.697 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
19:50:58.705 JACK was started with PID=28662 (0x6ff6).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
19:50:58.715 JACK was stopped successfully.
19:50:58.716 Post-shutdown script...
19:50:58.716 killall jackd
jackd(24480): Operation not permitted
jackd: no process killed
19:50:59.516 Post-shutdown script terminated with exit status=256.
19:51:01.161 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

It says:  the playback device "hw:0" is already in use

... but I don't have anything open!!

Any suggestions???

Daka

---

