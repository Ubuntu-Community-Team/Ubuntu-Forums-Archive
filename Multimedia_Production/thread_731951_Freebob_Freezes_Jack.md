---
title: "Freebob Freezes Jack"
date: 2008-03-22
forum: Multimedia Production
---

### Post by samiscooking on 2008-03-22
Hi everebody, I connected my new Firewire sound card Edirol Fa-66 through Jack and Freebob. Randomly jack doesn't start and I get an error message like this :
```

17:46:29.723 Patchbay activated.
17:46:29.741 Statistics reset.
JACK tmpdir identified as [/dev/shm]
17:46:29.854 MIDI connection graph change.
17:46:29.962 MIDI active patchbay scan...
17:46:29.964 MIDI connection change.
17:46:30.165 MIDI active patchbay scan...
17:46:30.994 Startup script...
17:46:30.994 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/sam/.kde/socket-studionull.
17:46:31.274 Startup script terminated with exit status=256.
17:46:31.274 JACK is starting...
17:46:31.275 /usr/bin/jackd -R -P18 -u -dfreebob -dhw:0 -r48000 -p512 -n3 -D -I3 -O3
17:46:31.278 JACK was started with PID=8980 (0x2314).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
17:46:32.300 MIDI connection graph change.
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
FreeBoB ERR: Could not start streaming threads
LibFreeBoB ERR: Could not do CMP for connection 0
DRIVER NT: could not start driver
cannot start driver
17:46:32.377 MIDI active patchbay scan...
17:46:32.378 MIDI connection change.
17:46:32.580 MIDI active patchbay scan...
17:46:37.616 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
could not attach as JACK client (server has exited)
17:46:37.703 MIDI connection graph change.
jackd watchdog: timeout - killing jackd
17:46:37.709 JACK was stopped successfully.
17:46:37.711 Post-shutdown script...
17:46:37.712 killall jackd
jackd: no process killed
17:46:37.950 Post-shutdown script terminated with exit status=256.
17:46:38.540 MIDI active patchbay scan...

```
Sometimes I can solve it by shutting down and restarting the sound card. I guess this is a very strange way to solve a problem, anybody could help me?

---

