---
title: "Jack &amp; IDJC Issues"
date: 2012-05-09
forum: Multimedia Software
---

### Post by Sableyes on 2012-05-09
Hello

I am on Ubuntu 64 bit.

I have used this guide to set up my Jack & IDJC pretty much scince it went up :

[http://naiux.wordpress.com/2010/03/20/idjc-shoutcast-setup-guide/](http://naiux.wordpress.com/2010/03/20/idjc-shoutcast-setup-guide/)

It worked untill some point a few months ago on Oeniric where my Mic just kept turning itself off.

In 12.04 I am having even more troubles, namely this when I try to start Jack.

> 18:33:50.313 Patchbay deactivated.
18:33:50.410 Statistics reset.
18:33:50.461 ALSA connection change.
18:33:50.858 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
18:33:50.869 ALSA connection graph change.
18:33:52.924 Startup script...
18:33:52.924 artshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: 1: artshell: not found
18:33:53.329 Startup script terminated with exit status=32512.
18:33:53.534 D-BUS: JACK server could not be started. Sorry
Wed May  9 18:33:53 2012: Starting jack server...
Wed May  9 18:33:53 2012: JACK server starting in non-realtime mode
Wed May  9 18:33:53 2012: control device hw:0
Wed May  9 18:33:53 2012: control device hw:0
Wed May  9 18:33:53 2012: Acquired audio card Audio0
Wed May  9 18:33:53 2012: creating alsa driver ... hw:0,0|hw:0,0|256|2|44100|0|0|nomon|swmeter|-|32bit
Wed May  9 18:33:53 2012: control device hw:0
Wed May  9 18:33:53 2012: [1m[31mERROR: 
ATTENTION: The playback device "hw:0,0" is already in use. Please stop the application using it and run JACK again[0m
Wed May  9 18:33:53 2012: [1m[31mERROR: Cannot initialize driver[0m
Wed May  9 18:33:53 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Wed May  9 18:33:53 2012: [1m[31mERROR: Failed to open server[0m
Wed May  9 18:33:54 2012: Saving settings to "/home/mutty/.config/jack/conf.xml" ...
18:33:55.638 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

Sometimes it turns on and works. Sometimes it fails and looses.

Any suggestions for either the disapearing mic issue or the Jack log error?

---

### Post by Sableyes on 2012-05-19
A brief update to this. 

With the mic turning itself off mid show, it happens when I change the volume on the volume applet on the Unity desktop (or any desktop for that matter!). Im guessing Pulse (/alsa? what do we use now?) does not like being changed when Jack is on. 

Again, if anyone has any suggestions, please yell. This bug is killin me :( 

Need to use IDJC and Jack 8 times a week.

---

### Post by Sableyes on 2012-05-19
A development!

Banged this into terminal today :

```
sudo apt-get install pulseaudio-module-jack
```

Did a show with no issues at all. Might have done the trick!

Paws crossed! Ill give it a week and if its all good I will mark the thread as solved. 

:guitar:

---

