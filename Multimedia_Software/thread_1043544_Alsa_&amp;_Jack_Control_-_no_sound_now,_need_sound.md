---
title: "Alsa &amp; Jack Control - no sound now, need sound, need EQ"
date: 2009-01-18
forum: Multimedia Software
---

### Post by DestroyerOfTheSeas on 2009-01-18
Hey I've been digging through forums for a couple hours trying to figure out what to do. I've been needing a graphic EQ and since the only thing I can find that may work as a general system-wide EQ is using Jack, I've been trying to get Jack configured but 2+2 seems to be wanting to be five.

Here is my Jack Control setup configs....

[http://deleonspringscommunity.com/Screenshot.jpg](http://deleonspringscommunity.com/Screenshot.jpg)

what is going on here? Jack starts and works(?), but doesn't play any sound. If jack is off, sound plays just fine. bagh.

---

### Post by markbuntu on 2009-01-18
Go here, it is an extensive guide to getting you sound configured properly and includes an UbuntuStudio and jack section that will provide you with some help. Be sure to follow the links

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by DestroyerOfTheSeas on 2009-01-18
Thanks so much for the above link!

I followed the advice very closely and completed all the tasks it described.. Now the I cannot get the Jack server to start and it obviously doesn't show up under PulseAudio Volume Control..

The little bit of script I wrote to be executed after Jack start-up I literally named "jack_startup," which is alright? It's not supposed to be "jack_startup.bin"? I made it executable with the command:

> chmod -x jack_startup

Was that right? Sorry if I'm showing "ignorance"... I'm trying my best to get the hang of this :P

I'm running Intrepid.

All my Jack settings are default with Runtime and Monitor ticked off.. Here is a screenshot: [http://www.deleonspringscommunity.com/Screenshot.jpg](http://www.deleonspringscommunity.com/Screenshot.jpg)

Here is the message I'm getting from Jack..

> 
20:20:12.951 Patchbay deactivated.
20:20:13.136 Statistics reset.
20:20:13.278 Startup script...
20:20:13.279 artsshell -q terminate
20:20:13.294 ALSA connection graph change.
20:20:13.722 Startup script terminated with exit status=256.
20:20:13.722 JACK is starting...
20:20:13.723 /usr/bin/jackd -R -t1000 -dalsa -dhw:0 -r44100 -p1024 -n3 -m
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209067856, from thread -1209067856] (1: Operation not permitted)
cannot create engine
20:20:13.734 JACK was started with PID=11301.
20:20:13.742 JACK was stopped successfully.
20:20:13.743 Post-shutdown script...
20:20:13.743 killall jackd
20:20:13.933 ALSA connection change.
jackd: no process killed
20:20:14.158 Post-shutdown script terminated with exit status=256.
20:20:15.980 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Does someone know what's going on?

~/Cheers!

---

### Post by DestroyerOfTheSeas on 2009-01-18
Do I need to download the RT kernel? I hear that it is pretty buggy with intrepid with Ubuntu Studio Audio installed..
Hello again all. maybe I am an ignoramus, maybe not. You decide.

I just did a reboot, now Jack WILL start, but I have no sound. Jack does not show up in the volume control of PulseAudio so it isn't sync'd..hmm..
I know starting Jack while an audio app is running generally recommended, but If I were to open Jack Audio Connection Kit while something is playing, it stops playing immediately preceding my opening of JACK. Does that mean anything besides I am an ignoramus?

Is the server state of Jack supposed to go from "started" to "active"?

I changed my driver from ALSA to OSS, then under "JACK > Connections" I connected "system" to "system" under "readable-input/writable-output" and the sound of silence at least came out of my speakers.. but nothing will actually play still and I'm getting a horrible about of XRUNS now.. Does that mean anything good or bad? Does the driver need to be set to ALSA or can it be OSS? Man I am confused, but I've still got a grip. 

If you just read this, thanks.

---

### Post by markbuntu on 2009-01-18
On Intrepid there is a problem with the real time kernel so you need to turn rt off in jack control.

Make sure that pulseaudio is running and that no application is using any sound when you start jack or pulseaudio will crash. If the jack modules are not showing up in pavucontrol or pulse sinks and sources in jack connections then maybe you missed something in the directions. You need to follow them very closely.

You maybe also need to change the interface setting in jackcontrol setup to your hardware instead of default.

You really just need to fool around with the settings. It can be a little tricky to get them setup the first time but once you do it will work.

---

### Post by DestroyerOfTheSeas on 2009-01-18
Thank you, sir.

---

