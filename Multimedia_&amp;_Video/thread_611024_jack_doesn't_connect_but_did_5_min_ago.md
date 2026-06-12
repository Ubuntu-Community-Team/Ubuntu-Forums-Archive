---
title: "jack doesn't connect but did 5 min ago"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Bubs on 2007-11-12
using Ustudio.  started jack and ardour. ardour said my memlock was to low so I went to where it said to go and changed it.  tried to start jack again but now it says it can't connect to jack server as a client.  I did go back and change everything back to the original state

I tried reading other posts around here but they seem to be people who are just installing it.  I've had it running and used it before but now it won't run.

here is the messages window

```
15:45:43.863 Patchbay deactivated.
15:45:43.927 Statistics reset.
15:45:43.993 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
15:45:44.152 MIDI connection change.
15:45:45.555 Startup script...
15:45:45.556 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/bubs/.kde/socket-bubs-desktop.
15:45:45.817 Startup script terminated with exit status=256.
15:45:45.817 JACK is starting...
15:45:45.817 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
15:45:45.834 JACK was started with PID=5924 (0x1724).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1622826416, from thread 1622826416] (1: Operation not permitted)
cannot create engine
15:45:45.839 JACK was stopped successfully.
15:45:45.839 Post-shutdown script...
15:45:45.839 killall jackd
jackd: no process killed
15:45:46.055 Post-shutdown script terminated with exit status=256.
15:45:47.979 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

bubs

---

### Post by Bubs on 2007-11-12
restarted again and it works

---

