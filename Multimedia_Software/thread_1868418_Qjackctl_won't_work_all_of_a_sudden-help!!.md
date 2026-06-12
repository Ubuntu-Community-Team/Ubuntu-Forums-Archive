---
title: "Qjackctl won't work all of a sudden-help!!"
date: 2011-10-24
forum: Multimedia Software
---

### Post by davidlondonuk on 2011-10-24
Hi,

Qjackctl was working perfectly (xubuntu 11.10) and I had ardour, seq24 etc all working and running well.

Now when I try to start qjackctl I get a grey box for say 45 secs, then the gui appears with the stop and transport buttons all greyed out (the stop button is also pressed).

Pressing start, starts jack for less than a second followed by this error message:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:31:56.758 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:31:56.782 Statistics reset.[/COLOR]
 [COLOR=#cccc99]13:31:56.796 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:32:46.877 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot open qjackctl client
 [COLOR=#66cc99]13:32:51.907 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]13:33:00.038 JACK is starting...[/COLOR]
 [COLOR=#990099]13:33:00.039 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p1024 -n2[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Cannot create thread 1 Operation not permitted
 [COLOR=#999999]13:33:00.099 JACK was started with PID=3419.[/COLOR]
 Cannot create thread 1 Operation not permitted
 `default' server already active
 Failed to open server
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]13:33:00.135 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]13:33:07.112 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client


Anyone know how to fix this? I am at a loss.

---

