---
title: "Jack Control problems"
date: 2009-10-19
forum: Multimedia Software
---

### Post by karimruan on 2009-10-19
Every time i start Jack Control, and press start, it gives me the following message:

08:56:10.846 Patchbay deactivated.
08:56:11.197 Statistics reset.
08:56:11.268 ALSA connection graph change.
08:56:11.882 ALSA connection change.
08:56:17.582 Startup script...
08:56:17.584 artsshell -q terminate
sh: artsshell: not found
08:56:17.989 Startup script terminated with exit status=32512.
08:56:17.991 JACK is starting...
08:56:17.992 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
08:56:17.999 JACK was started with PID=5136.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1212119360, from thread -1212119360] (1: Operation not permitted)
cannot create engine
08:56:18.369 JACK was stopped successfully.
08:56:18.370 Post-shutdown script...
08:56:18.371 killall jackd
jackd: no process killed
08:56:18.807 Post-shutdown script terminated with exit status=256.
08:56:20.099 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

This is the input from the message window, as far as I know. What do I need to get it to connect?

---

