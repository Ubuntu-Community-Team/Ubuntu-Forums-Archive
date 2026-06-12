---
title: "Ubuntu 9.04, Dell Vostro 1000 - Jack isn't working."
date: 2009-09-19
forum: Multimedia Software
---

### Post by ets2006 on 2009-09-19
Hello, I've recently got my new laptop, a Dell Vostro 1000, but i've been having a few problems getting it to work. It is running Ubuntu 9.04
My sound card identifies itself as a STAC9200.
I'm using Jack Control to start Jackd, with the default configuration. When I attempt to start jack, it fails. Logs;
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]15:22:38.363 JACK is starting...[/COLOR]
 [COLOR=#990099]15:22:38.364 /usr/bin/jackd -v -R -P24 -dalsa -dhw:0 -r44100 -p1024 -n3 -s -m -S -zr -H -M[/COLOR]
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 [COLOR=#999999]15:22:38.394 JACK was started with PID=24405.[/COLOR]
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_net.so
 getting driver descriptor from /usr/lib/jack/jack_freebob.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 server `default' registered
 cannot use real-time scheduling (FIFO at priority 10) [for thread -2061838608, from thread -2061838608] (1: Operation not permitted)
 cannot create engine
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 [COLOR=#999999]15:22:38.462 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]15:22:38.464 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:22:38.466 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]15:22:38.896 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]15:22:40.627 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```I have played around with the configuration, however it still doesn't work.
I had got it jack to start, but not play any sound, but every time I opened hydrogen, jack control would "disappear", and jackd would die.

Any ideas for a n00b?
Thanks in advance.

---

