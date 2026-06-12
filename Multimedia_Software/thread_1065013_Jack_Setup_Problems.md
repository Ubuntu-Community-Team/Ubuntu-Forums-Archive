---
title: "Jack Setup Problems"
date: 2009-02-09
forum: Multimedia Software
---

### Post by ChrisB111 on 2009-02-09
I have installed the Ubuntu Studio tools and have used the sticky Sound Problems thread to setup my sound card. I have worked out that I think I need to setup jack to get things like rosegarden working. I have tried searching on the internet and wiki, and just messing around with the setting but I really have no clue what I am doing. This is my setup (see screenshot) and the output I get from jack when it fails.

Thanks,

Chris

```
18:37:38.043 Patchbay deactivated.
18:37:38.045 Statistics reset.
18:37:38.369 ALSA connection graph change.
18:37:38.604 ALSA connection change.
18:37:39.464 Startup script...
18:37:39.466 artsshell -q terminate
18:37:39.889 Startup script terminated with exit status=256.
18:37:39.890 JACK is starting...
18:37:39.892 /usr/bin/jackd -v -R -dalsa -dhw:0,2 -r44100 -p64 -n2 -m -Xseq
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209842000, from thread -1209842000] (1: Operation not permitted)
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'
18:37:39.918 JACK was started with PID=20723.
18:37:39.927 JACK was stopped successfully.
18:37:39.928 Post-shutdown script...
18:37:39.928 killall jackd
jackd: no process killed
18:37:40.363 Post-shutdown script terminated with exit status=256.
18:37:42.063 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by nlz on 2009-02-09
Options
1. untick 'realtime' under 'setup' in qjackctl and see if it works.

2. Tinker with priority, frames/period and sampleate and see if it works.

3. start Jack as root (type: 'sudo qjackctl' in a terminal)

Maybe this will get you going..

---

