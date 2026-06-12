---
title: "JACK with Hydrogen?"
date: 2009-06-11
forum: Multimedia Software
---

### Post by IBUA on 2009-06-11
Hey,

I'm trying to get JACK to work with hydrogen, but every time i load JACK it automatically "kills" it's self

This is the information from the Messages.

I followed the How-to configure jack page, but i still don't know whats going wrong

```
14:32:18.923 Patchbay deactivated.
14:32:18.991 Statistics reset.
14:32:19.503 Startup script...
14:32:19.505 artsshell -q terminate
14:32:19.517 ALSA connection graph change.
sh: artsshell: not found
14:32:19.926 Startup script terminated with exit status=32512.
14:32:19.929 JACK is starting...
14:32:19.937 /usr/bin/jackd -R -p128 -t5000 -dalsa -r48000 -p64 -n2 -D -Chw:0 -Phw:0 -S
14:32:19.977 JACK was started with PID=16365.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1212008768, from thread -1212008768] (1: Operation not permitted)
cannot create engine
14:32:20.071 JACK was stopped successfully.
14:32:20.073 Post-shutdown script...
14:32:20.075 killall jackd
14:32:20.190 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
14:32:26.085 ALSA connection change.
jackd: no process killed
14:32:26.363 Post-shutdown script terminated with exit status=256.
```

Anyhelp?

Cheers

---

