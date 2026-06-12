---
title: "JACK fail ( could not connect to jack server ). EG. Rosegarden"
date: 2011-05-23
forum: Multimedia Software
---

### Post by Nbala on 2011-05-23
[COLOR=Green]Hi, I love Ubuntu- its all good[/COLOR]. But the sound is not working with audio apps like: rosegarden, muse score, etc, only one its AOK for is Audacity. (?)
EVERY audio editor, every notation program, anything to do with music creation software comes up with this error [COLOR=Red]**"Could not connect to JACK server as client"**[/COLOR]
I tried using Qsynth instead, & tried installing the JACK control panel etc, no dice, every time- JACK fails. Ive tried workarounds to NOT use this damn JACK thing, but nothing works so far.
Music works, video works, in movies etc. Not a 'sound' problem- Qsynth functions for some things but isnt what the applications demand.
**Here's the output from JACK**- the 'obvious' errors in bold.
This has been a big frustration- and help is  greatly appreciated!!!!!!

**OUTPUT**:

[COLOR=Blue]11:06:02.333 Patchbay activated.
11:06:02.487 Statistics reset.
11:06:02.608 Startup script...
11:06:02.609 artsshell -q terminate
11:06:02.743 ALSA connection graph change.
**sh: artsshell: not found**
**11:06:05.905 Startup script terminated with exit status=32512.**
11:06:05.906 JACK is starting...
11:06:05.907 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n15 -s -S -Xraw -H
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|15|44100|0|0|hwmon|swmeter|soft-mode|16bit
control device hw:0
[COLOR=Blue]**the playback device "hw:0" is already in use. Please stop the application using it and run JACK again**[/COLOR]
[COLOR=Blue]**cannot load driver module alsa**[/COLOR]
11:06:06.144 JACK was started with PID=4627.
11:06:06.144 ALSA active patchbay scan...
11:06:06.147 ALSA connection change.
11:06:06.321 JACK was stopped successfully.
11:06:06.322 Post-shutdown script...
11:06:06.322 killall jackd
11:06:06.363 ALSA active patchbay scan...
jackd: no process found
11:06:06.761 Post-shutdown script terminated with exit status=256.
**11:06:08.254 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. **Please check the messages window for more info.[/COLOR]

---

