---
title: "Jack crashing after 10.04 update"
date: 2010-05-04
forum: Multimedia Software
---

### Post by mikeymo1741 on 2010-05-04
I upgraded to 10.04 this weekend.   The first time I tried to run Jackctl, I got an error that I was not in the audio group.  Easily fixed with usermod.  Jack ran fine, and I was able to launch Ardour. 


Now, though, I cannot get Jack to run at all.   I keep getting the following errors:
> 
1028:43.594 Patchbay deactivated.
10:28:43.606 Statistics reset.
10:28:43.687 Startup script...
10:28:43.687 artsshell -q terminate
10:28:43.693 ALSA connection graph change.
sh: artsshell: not found
10:28:44.120 Startup script terminated with exit status=32512.
10:28:44.121 JACK is starting...
10:28:44.122 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    763725
10:28:44.135 JACK was started with PID=4645.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
10:28:44.329 ALSA connection change.
10:28:45.207 JACK was stopped successfully.
10:28:45.208 Post-shutdown script...
10:28:45.209 killall jackd
10:28:45.209 JACK has crashed.
jackd: no process found
10:28:45.677 Post-shutdown script terminated with exit status=256.
10:28:46.418 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info. 

I have tried changing to hw:1, disabling realtime, and booting to the prior kernel.  Jack is also crashing window selector and workspace switcher.   Any thoughts?

---

### Post by mikeymo1741 on 2010-05-12
Nothing, huh?

---

### Post by h-man on 2010-06-24
I have the same problem.  10.04 is the first Ubuntu version I have used.  Have you found a resolution to this issue?  There appears to be no further details as to why jackd is dying, it just crashes.  I'd love to have an answer to this problem.

---

