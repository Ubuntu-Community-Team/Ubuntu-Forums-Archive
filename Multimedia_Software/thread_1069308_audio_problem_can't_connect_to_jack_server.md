---
title: "audio problem: can't connect to jack server"
date: 2009-02-13
forum: Multimedia Software
---

### Post by iseeclouds on 2009-02-13
jack worked fine at first. then i removed some programs that i never use (from the ubuntu studio package) using "sudo apt-get remove". now i get an error when starting Jack. did i accidentally remove a wrong file?
in the 'jack audio connection kit' is get these errors in messages:
> 02:35:03.027 Patchbay deactivated.
02:35:03.080 Statistics reset.
02:35:22.724 Startup script...
02:35:22.725 artsshell -q terminate
Error: "/home/brecht/.kde/socket-brecht" is not a link or a directory.
Error: "/home/brecht/.kde/socket-brecht" is not a link or a directory.
Error: "/home/brecht/.kde/socket-brecht" is not a link or a directory.
(The previous message was repeated 1 times.)
can't create mcop directory
02:35:23.147 Startup script terminated with exit status=256.
02:35:23.147 JACK is starting...
02:35:23.147 /usr/bin/jackd -R -t5000 -dalsa -dhw:0 -r44100 -p64 -n4 -m
02:35:23.149 JACK was started with PID=6605.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210743120, from thread -1210743120] (1: Operation not permitted)
cannot create engine
02:35:23.158 JACK was stopped successfully.
02:35:23.158 Post-shutdown script...
02:35:23.159 killall jackd
jackd: no process killed
02:35:23.567 Post-shutdown script terminated with exit status=256.
02:35:25.364 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info
i really have no idea how to fix this.

---

### Post by neu2buntu on 2009-02-13
try running it without the "realtime" option (just untick it in qjackctl)first to see and let us know the result!  did you always run it in realtime before too?  and go to > synaptic package manager > file > history. and post the uninstall log of the packages you removed that you think may have caused the problem.  im thinking maybe the error about "kde" could be something to do with the removal dependency. if im not mistaken qjackctl depends on kde or qt package

---

### Post by iseeclouds on 2009-02-14
thanks for the help, i really appreciate it!
> **neu2buntu said:**
> try running it without the "realtime" option ...did you always run it in realtime before too?
yes, it used to run in realtime. unchecking the realtime option made it work. but what's the difference? does it work slower without realtime?
i do get the same "problem" as before. when i open renoise (music program), the Jack icon in the panel turns red. what does this mean and how can i solve it?

[QUOTE=synaptic blog]Commit Log for Sun Feb  8 16:39:21 2009
Removed the following packages: 
bluez-gnome 
bug-buddy 
ekiga 
tomboy 
transmission-gtk 
tsclient 
vinagre

Installed the following packages: 
gstreamer0.10-ffmpeg (0.10.3-6) 
gstreamer0.10-plugins-ugly (0.10.7-3ubuntu1) 
libavformat1d (3:0.cvs20070307-5ubuntu7.1) 
libdc1394-13 (1.1.0-5ubuntu1) 
libdvdread3 (0.9.7-8ubuntu1) 
libmpeg2-4 (0.4.1-1) 
libpostproc1d (3:0.cvs20070307-5ubuntu7.1) 
libsidplay1 (1.36.59-4)
alsa-oss (1.0.15-1) 
asoundconf-gtk (1.6-0ubuntu1) 
cabextract (1.2-2) 
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-1) 
gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1) 
gstreamer0.10-plugins-bad (0.10.6-5ubuntu0.1) 
gstreamer0.10-plugins-bad-multiverse (0.10.6-1) 
gstreamer0.10-plugins-ugly-multiverse (0.10.7-1) 
java-common (0.28ubuntu3) 
libasound2-plugins (1.0.15-1ubuntu3) 
libcdaudio1 (0.99.12p2-3) 
libfaac0 (1.26-0.1ubuntu1) 
libgmyth0 (0.7.debian1-1~hardy1) 
libiptcdata0 (1.0.2-2) 
liblame0 (3.97-0.0) 
libmjpegtools0c2a (1:1.8.0-0.2ubuntu5) 
libopenspc0 (0.3.99a-2) 
libsoundtouch1c2 (1.3.0-2.2ubuntu0.1) 
libwildmidi0 (0.2.2-2) 
libx264-57 (1:0.svn20071224-0.0ubuntu1) 
libxvidcore4 (2:1.1.2-0.1ubuntu3) 
msttcorefonts (2.4) 
odbcinst1debian1 (2.2.11-16build1) 
sun-java6-bin (6-07-3ubuntu2) 
sun-java6-jre (6-07-3ubuntu2) 
sun-java6-plugin (6-07-3ubuntu2) 
ubuntu-restricted-extras (15.2) 
unixodbc (2.2.11-16build1) 
unrar (1:3.7.8-1) 
soundconverter (1.0.1-0ubuntu2)
sooperlooper (1.0.8c-3ubuntu1)
jamin

Commit Log for Sat Feb 14 01:41:28 2009
Removed the following packages: 
linux-rt

Installed the following packages: 
alsamixergui (0.9.0rc2-1-9) 
libaudio-mixer-perl (0.7-2) 
mixer.app (1.8.0-4)

Installed the following packages: 
alsamixergui (0.9.0rc2-1-9) 
libaudio-mixer-perl (0.7-2) 
mixer.app (1.8.0-4)
gnome-applets (2.22.2-0ubuntu2) 
gnome-applets-dbg (2.22.2-0ubuntu2)

Removed the following packages: 
qarecord[/QUOTE]
it's strange that this log says i removed linux-rt. in synaptic it's still checked and when i try to install it in a terminal it also says linux-rt is already installed. so, i have no idea what else it could be.
i'd like it to work in realtime again. i know it can work, because it worked before. i just don't know what i did wrong.

---

### Post by neu2buntu on 2009-02-14
i think realtime really gives jack top priority, so for say recording a session in ardour you will not get any (or as many) x-runs,which can gives audible glitches in the recording.   not sure about the qjack icon turning red i dont use it. there is a workaround to get realtime working.
[1] goto .> system > administration .> users and groups > unlock > manage groups > add group > then add the group... audio , and in >properties tick your username as a group member to audio.

[2] now open terminal and do: ```
sudo gedit /etc/security/limits.conf
``` and add this before #end of line 
```
@audio          -       rtprio          99
@audio          -       memlock         unlimited
@audio          -       nice            -19

``` and save , restart and try qjackctl with realtime again to see!!!

---

### Post by iseeclouds on 2009-02-16
this worked. thanks a lot! just out of curiosity, what do you use instead of qjack?

i have another unrelated question, but maybe you know how to solve it. when i plug in my headphone, the internal laptop speakers don't mute. any idea how this could be fixed?

---

### Post by neu2buntu on 2009-02-16
no i do use qjackctl i just didnt tick the "enable system tray icon" and i have added qjackctl to start up so no need to start it manually everytime., i did this method by going to > system > preferences > sessions > +add... and added title: jack command : qjackctl
   also i have jack setup to link with pulseaudio so everything can play through jack ie .mnp3 cd's firefox etc ...   i followed this tutorial here    
[http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

---

### Post by neu2buntu on 2009-02-16
just noticed you question about headphones.and yes i have had to do this for my advent k4000 laptop... follow this post which is a sub post of the 1 above [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by iseeclouds on 2009-02-17
i tried those topics but it didn't get me any further. but at least i can run renoise through jack now. thanks again !

---

