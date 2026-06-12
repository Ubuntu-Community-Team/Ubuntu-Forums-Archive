---
title: "JACK Audio Problem"
date: 2009-06-24
forum: Multimedia Software
---

### Post by Lord Noxarethor on 2009-06-24
Hello, I installed Jack, but whenever I want to start it, it fails. Here's the message log:
```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:40:55.933 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:40:56.058 Statistics reset.[/COLOR]
 [COLOR=#66cc99]13:40:56.078 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]13:40:56.481 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:41:46.628 Startup script...[/COLOR]
 [COLOR=#990099]13:41:46.629 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:41:47.031 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:41:47.033 JACK is starting...[/COLOR]
 [COLOR=#990099]13:41:47.034 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -m[/COLOR]
 [COLOR=#999999]13:41:47.041 JACK was started with PID=17750.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1211398464, from thread -1211398464] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]13:41:47.074 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]13:41:47.075 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:41:47.076 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]13:41:47.523 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]13:41:49.134 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```What can I do?

---

### Post by druid23 on 2009-06-24
Looks like you are trying to start Jack with the Real-Time option enabled and that's causing the failure. Perhaps you aren't running a realtime kernel.

Try unchecking the realtime option in the setttings panel (the Setup button opens this dialogue) and trying to start it again.

There may well be further errors before you can get it running but take it one step at a time.

---

### Post by Lord Noxarethor on 2009-06-24
Works! Thanks :popcorn:

---

