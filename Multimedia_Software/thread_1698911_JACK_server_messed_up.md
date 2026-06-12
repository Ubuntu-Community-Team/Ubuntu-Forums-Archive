---
title: "JACK server messed up :/"
date: 2011-03-02
forum: Multimedia Software
---

### Post by dknife9 on 2011-03-02
Hi - so I borked JACK somehow, not sure exactly what I did. I'm running Ubuntu Studio 10.10. I was trying to get JACK to work with my usb keyboard I just got and was trying different programs as I am rather new to Ubuntu still in the first place. While I was trying out different things (I think I was messing with Patchage at the time - I'm not sure what else I was running) and the screen flashed kindof and when it came back up I had a default "windows 98" looking theme running instead of my normal one. I restarted the computer, and now things LOOK normal, but the JACK server won't start up for either JACK Control or Patchage. :confused:

Help? - Below I put the message output from JACK Control when it tries to start. it just keeps trying to start the over and over, doubling the wait time between each try. the first bit about cannot connect to server socket is repeated each time it trys.

I've tried reinstalling all the jack packages with synaptic package manager and I've tried reinstalling jack via the ubuntu software manager, but I still get the exact same results.

Thanks,
Ben

---


20:05:41.597 Startup script...
20:05:41.598 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
20:05:42.001 Startup script terminated with exit status=32512.
20:05:42.001 JACK is starting...
20:05:42.002 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
20:05:42.019 JACK was started with PID=3946.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xe4700000 irq 45
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
20:05:42.320 JACK was stopped with exit status=255.
20:05:42.324 Post-shutdown script...
20:05:42.325 killall jackd
jackd: no process found
20:05:42.736 Post-shutdown script terminated with exit status=256.
20:05:44.180 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by cchhrriiss121212 on 2011-03-03
> Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xe4700000 irq 45
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
This means another program is using the soundcard, so shut down everything else before starting jack and try again.

---

### Post by dknife9 on 2011-03-03
How do I do that? I'm guessing it's a background process or something because it will do this immediately after freshly rebooting without any extra programs running.

---

### Post by cchhrriiss121212 on 2011-03-04
On a fresh boot, there won't be anything set to use the sound card. Are you sure that you get the exact same message when doing a fresh boot?
If you are sure, open up system monitor and check the processes tab, post it here if you want.

---

### Post by dknife9 on 2011-03-04
fixed it. (not sure if it's permenant yet.) aparrently 'jackd' wasn't starting or somehow wasn't working, but I started it via terminal and then tried jack control again and now it works.

---

