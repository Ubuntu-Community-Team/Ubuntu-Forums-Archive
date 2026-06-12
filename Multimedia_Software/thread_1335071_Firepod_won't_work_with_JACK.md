---
title: "Firepod won't work with JACK"
date: 2009-11-23
forum: Multimedia Software
---

### Post by marxspeakstruth on 2009-11-23
Hey guys,
Trying to set up a PreSonus FirePod on my friends Compaq Presario SR2177CL (AMD Athlon X2 64-Bit) and having a little trouble. I followed a guide on this forum ( [http://ubuntuforums.org/showthread.php?t=713695](http://ubuntuforums.org/showthread.php?t=713695) ) but I still can't get it to work. When I hit "Start" on JACK I get this error:

Could not connect to JACK server as client
     -Overall operation failed
     -Unable to connect to server
Please check the Messages window for more info.

Messages info gives this information:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]03:25:48.562 Startup script...[/COLOR]
 [COLOR=#990099]03:25:48.563 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]03:25:48.967 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]03:25:48.967 JACK is starting...[/COLOR]
 [COLOR=#990099]03:25:48.969 /usr/bin/jackd -R -P70 -dfreebob -r44100 -p128 -n3 -D[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 [COLOR=#999999]03:25:49.010 JACK was started with PID=2553.[/COLOR]
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 Freebob using Firewire port 0, node -1
 Ieee1394Service::initialize: Could not get 1394 handle: Invalid argument
 Is ieee1394 and raw1394 driver loaded?
 [31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
 [0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
 FreeBoB ERR: FREEBOB: Error creating virtual device
 cannot load driver module freebob
 [0m
 [COLOR=#999999]03:25:49.397 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]03:25:49.397 Post-shutdown script...[/COLOR]
 [COLOR=#990099]03:25:49.398 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]03:25:49.810 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]03:25:51.232 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


[COLOR=#ff0000][COLOR=Black]I'm pretty sure it has to do with the firewire drivers, but I don't know how to remedy this. Help me if you can, please! Thanks so much![/COLOR]
[/COLOR]

---

### Post by marxspeakstruth on 2009-11-23
so i figured out that if i run this:

 sudo chmod 777 /dev/raw1394

in the terminal before trying to run JACK, it works. I'm not sure why, and I have to do it every time I restart my comp. Anyone know why, or how I could fix it for good?

---

