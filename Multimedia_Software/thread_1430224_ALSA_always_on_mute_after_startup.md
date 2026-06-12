---
title: "ALSA always on mute after startup"
date: 2010-03-15
forum: Multimedia Software
---

### Post by frederikbjerreandersen on 2010-03-15
Hi,

I have a little but annoying problem: every time i start Ubuntu (9.10), the speakers are on mute and the level at zero - so I have to open the ALSA mixer to it and unmute and turn up the level.

Any way to make the mixer save and start up with the last used sound settings instead?

---

### Post by garvinrick4 on 2010-03-15
Audio mute fix
Works everytime for me,
This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore


Now set audio where you like and log-out on log-on to make
sure of fix.

---

### Post by frederikbjerreandersen on 2010-03-15
it seems to work, thanks!

---

### Post by Chuck_N on 2010-03-31
I would love to try that
inasmuch as that is a problem I'm having
but I have no idea how to do it.

---

### Post by dirkbo on 2010-04-25
After upgrading from karmic to lucid, alsa was always muted after Login so there was no sound. 

Commenting out 
load-module module-device-restore
in /etc/pulse/default.pa 
solved the problem, thanx!

---

### Post by pebe on 2010-04-26
I have this problem that in other cases too but mainly when I listen to music in spotify the volume goes to zero almost everytime a new song starts. I tested this trick and restarted Ubuntu. 

Now when I start a new song the volume doesn't mute, but now the sound is gone allthough volume is on max. 

Help would be very appreciated.

---

### Post by garvinrick4 on 2010-04-26
> **pebe said:**
> I have this problem that in other cases too but mainly when I listen to music in spotify the volume goes to zero almost everytime a new song starts. I tested this trick and restarted Ubuntu. 

Now when I start a new song the volume doesn't mute, but now the sound is gone allthough volume is on max. 

Help would be very appreciated.
That is not the same mute problem uncomment back the line you commented.

---

### Post by garvinrick4 on 2010-04-26
> **Chuck_N said:**
> I would love to try that
inasmuch as that is a problem I'm having
but I have no idea how to do it.
Open a terminal and type in Code;:

gksudo gedit /etc/pulse/default.pa

gedit will open and find the line:

load-module module-device-restore
and put a # in front of that line and hit save.

gksudo opens gedit with root priviledges so be carefull and focus.

gedit is a text editor. 

The # in front of a line comments it out, if it does not have a # it is a working line of code.

"Ubuntu pocket guide and references" is the name of a Ubuntu book you can download 
 in .pdf file and keep on hand, will be good reading for you.

---

### Post by pebe on 2010-04-26
thanks for the reply, yes I know its not the sam problem. just wanted to test if it could do something and report here. did the uncommenting and works like before.

---

### Post by Psimon on 2010-04-30
I still have this problem on Lucid (fresh install) and the recommended mod:

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore

didn't fix it.

I've had this problem on karmic and it's driving me mad. Any other suggestions?

Cheers

---

### Post by pebe on 2010-05-04
fixed my problem, it seemed to be a problem with the dedault wine not working properly with the pulseaduio system. the solution I did was to change in wine configuration (under the Audio tab) unclick anything else and change to the EsounD driver as pulseaudio is able to emulate EsounD. Another fix that I havenät tested is to get a pulseaudio enabled version of wine.

heres a link with guide to a repository with pulseaudio enabled wine, made for ubuntu 9.10, maybe it works for 10.04 alsa..

hope others get helped by this, strange if ubuntu don't have pulseaudio enabled in their default wine as standard

---

