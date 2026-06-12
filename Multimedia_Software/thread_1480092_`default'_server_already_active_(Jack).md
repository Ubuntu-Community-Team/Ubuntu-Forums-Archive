---
title: "`default' server already active (Jack)"
date: 2010-05-11
forum: Multimedia Software
---

### Post by Jordii on 2010-05-11
Jack doesn't run because of this:
> [COLOR=#999999]15:41:31.798 Patchbay deactivated.[/COLOR] [COLOR=#999999]15:41:31.812 Statistics reset.[/COLOR]
 [COLOR=#999999]15:41:31.907 Startup script...[/COLOR]
 [COLOR=#990099]15:41:31.908 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]15:41:31.912 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:41:32.311 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:41:32.312 JACK is starting...[/COLOR]
 [COLOR=#990099]15:41:32.312 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -m[/COLOR]
 [COLOR=#999999]15:41:32.326 JACK was started with PID=2513.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 `default' server already active
 [COLOR=#999999]15:41:32.380 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]15:41:32.381 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:41:32.381 killall jackd[/COLOR]
 [COLOR=#cccc99]15:41:32.525 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:41:32.792 Post-shutdown script terminated successfully.[/COLOR]
 [COLOR=#ff0000]15:41:34.530 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


---

### Post by hxcobd on 2010-05-11
*posts same thing for the 5th time today*

TOP 2 REASONS JACK DOESN'T START:

1.) You already have something open that's either using your soundcard or WAS using your soundcard. This includes all media players, web browsers, games, and so on. CLOSE EVERYTHING BEFORE YOU START JACK.

2.) Your settings are wrong in JACK. Buffer, periods/buffer, and samplerate are the most common incorrect settings.

---

