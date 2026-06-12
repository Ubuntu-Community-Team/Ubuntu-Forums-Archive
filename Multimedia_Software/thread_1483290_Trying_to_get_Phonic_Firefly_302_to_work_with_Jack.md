---
title: "Trying to get Phonic Firefly 302 to work with Jackd"
date: 2010-05-14
forum: Multimedia Software
---

### Post by kidsil on 2010-05-14
Hello, I'm running Ubuntu 10.04 and I have an external Sound card: Phonic Firefly 302. 

I've connected the device, installed Jackd, added the lines:

 @audio - rtprio 99 
 @audio - memlock 500000 
 @audio - nice -10 to /etc/security/limits.conf 
 logged out, logged back in, ran qjackctl (sudo qjackctl to be exact), ran the settings and chose "firewire" on the driver option, pressed "Start" and that was the output: 
20:10:19.450 Patchbay deactivated.
20:10:19.578 Statistics reset.
20:10:19.601 ALSA connection graph change.
20:10:19.828 ALSA connection change.
20:10:21.293 Startup script...
20:10:21.293 artsshell -q terminate
sh: artsshell: not found
20:10:21.695 Startup script terminated with exit status=32512.
20:10:21.695 JACK is starting...
20:10:21.695 /usr/bin/jackd -dfirewire -r44100 -p1024 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
20:10:21.704 JACK was started with PID=22176.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
20:10:21.819 JACK was stopped successfully.
20:10:21.819 Post-shutdown script...
20:10:21.822 killall jackd
jackd: no process found
20:10:22.230 Post-shutdown script terminated with exit status=256.
20:10:23.865 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Error: "/tmp/kde-user" is owned by uid 1000 instead of uid 0.

---

### Post by kidsil on 2010-05-18
anyone?

---

### Post by Arizon_Dread on 2010-08-09
Hey!

Did you get this to work? I'm contemplating buying a firefly 302

---

