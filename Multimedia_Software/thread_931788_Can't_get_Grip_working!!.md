---
title: "Can't get Grip working!!"
date: 2008-09-27
forum: Multimedia Software
---

### Post by yelserpdog on 2008-09-27
Hi there,

I;m trying to get Grip to rip and encode some cds. I've used this guide

[http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

I'm able to rip the files to a wav file without any problem. If however I choose Rip and encode all i'm left with is a 128kb size mp3!

My encoder settings are:

Executable: /usr/bin/lame
Command line: -h-V 3 %w %m
file extension: mp3
File format: ~/mp3/%A/%d/%n.%x

Does anyone know what i'm doing wrong?

cheers
Yd

---

### Post by mc4man on 2008-09-27
try removing the -h
from your encoder command line

and if you'd like to have grip number the tracks (the way I access music it's a must
use this line instead of yours
> ~/mp3/%A/%d/%t- %n.%x

will add a 1-,2- ect to front of track name

---

### Post by yelserpdog on 2008-09-27
No luck, it still produced a 128kbit file that can't be played :-(

---

### Post by mc4man on 2008-09-27
> it still produced a 128kbit file
That's usually a sign of the encoder failing.
I reset grip to the default install (deleted all the .grip files in home folder) and did exactly what you did, same settings, ect. Works fine.

Maybe try reinstalling lame

Edit:
Do you have liblame0 installed?

---

### Post by yelserpdog on 2008-09-28
I deleted all the .grip files you mentioned, tried again and it worked!!! woohoo thanks for your help :guitar:

---

