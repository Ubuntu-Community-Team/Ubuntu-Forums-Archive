---
title: "mplayer in fiesy help"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by firstc624 on 2007-04-24
ok i have been running mplayer since dapper and this is the first time i have had this problem.

When i open any type of media file it opens like normall but since i told fiesty to install the restricted drivers, fglrx, when i tell the media file to play in fullscreen mode it just scales the window up not the video.

Has anyone had that problem and if so how did you fix it?

I have uninstalled fglrx and everything plays correctly again, fullscreen and everything.

Thanks for any info you have to help fix this

---

### Post by firstc624 on 2007-04-26
anyone?:confused:

---

### Post by ebishop on 2007-04-26
I have the same problem.  I upgraded from edgy a week ago.  I have a Geforce 4, using the nvidia drivers.  When I play a movie in mplayer and go to fullscreen, the video stays the same size and the rest of the screen fills up with black space.  On the plus side the audio sync problems in xine seem to be fixed.

Does anybody know what's going on or have a workaround?

---

### Post by lbyrd33 on 2007-04-26
I had the same problem and I just changed the video output to x11.

---

### Post by andreimatei on 2007-04-27
try launching mplayer with -zoom option

---

### Post by firstc624 on 2007-04-27
have tried switching drivers and stays the same.

i also can't view files from the gui so i use the command line to get them to play.

the -zoom option doeesnt work either.

anyone else have an idea as to why  is?  possible ati driver issue?

---

### Post by sdowney717 on 2007-04-27
are you using mplayer or gmplayer?

for example here:

root@scott-desktop:~# gmplayer
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

---

### Post by firstc624 on 2007-04-27
mplayer.   i have setup a run command to assosiate a file type to .avi or whaterever.

i put the gui in the last comment just to say i can't even play a file thru it at all.


edited to add screenshot.

---

### Post by lucas42 on 2007-04-30
I had this problem - I solved by editing ~/.mplayer/config  I just added the line:

```
zoom=yes
```

that seemed to do the trick

---

### Post by firstc624 on 2007-05-01
that did it lucas thank you.

for all those who may have this problem to to terminal and type

```
sudo gedit /etc/mplayer/mplayer.conf
```


in there just scroll down untill you see #zoom=yes

just remove the #  so that the change will take effect.

First_c

---

### Post by jaywee on 2007-05-04
Thanks a lot.it helps me!

---

