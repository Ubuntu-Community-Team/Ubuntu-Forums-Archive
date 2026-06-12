---
title: "Cannot start Ardour 2 (JACK won''t initialze)"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Mblackwell on 2007-06-03
When I try to start Ardour I get this message
```

$ ardour2
Ardour/GTK 2.0beta10
   (built using 1266 and GCC version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5))
Copyright (C) 1999-2006 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
Loading ui configuration file /usr/local/etc/ardour2/ardour2_ui.rc
theme_init() called from internal clearlooks engine!
exec of JACK server failed: No such file or directory
ardour: [ERROR]: Unable to connect to JACK server
ardour: [ERROR]: Could not connect to JACK server as  "ardour"
ardour: [ERROR]: Could not connect to JACK server as  "ardour"

```

Okay so it can't start a JACK server you say. 

Well if I try to use the JACK Control Kit I get:

```

13:41:40.031 Startup script...
13:41:40.031 artsshell -q terminate
can't create mcop directory
Creating link /home/jon/.kde/socket-jon.
13:41:40.371 Startup script terminated with exit status=256.
13:41:40.371 JACK is starting...
13:41:40.372 jackd -p128 -dalsa -dhw:0 -r48000 -p1024 -n2
13:41:40.381 JACK was started with PID=11126 (0x2b76).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
13:41:43.432 Could not connect to JACK server as client. Please check the messages window for more info.

```

No matter what settings I've tried it refuses to connect.

If I start JACK in the terminal (via jackd -d alsa) I get:

```

$ jackd -d alsa
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

```

And it sits there happily running with no complaints (and no xruns) until I kill it.

Unfortunately Ardour still won't start (same message as the first one I posted) so I'm really at a loss as to what to do!

MetalMusicAddict once offered up saying I should put **sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'** into a terminal and log out and in but this still didn't fix the problem.

And yes I'm using a lowlatency kernel. :)

---

### Post by Mblackwell on 2007-06-04
bump

---

