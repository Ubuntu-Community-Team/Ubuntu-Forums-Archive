---
title: "Crackly Sound on Ubuntu 14.04"
date: 2014-06-12
forum: Multimedia Software
---

### Post by tails2k5 on 2014-06-12
Hello, I've been using Ubuntu for 7 years now, so I'm comfortable with the terminal, but I'm certainly no kernel hacker.  Anyway, I just built a new PC with an intel i7-4790S and Gigagbyte GA-Z97X-Gaming 7 motherboard, and the sound is crackly and skips sometimes (I've tried mp3s and youtube).  I'm at a loss for what to do, I've tried searching but most of the advice is for 12.04 and older.  I'm using headphones connected to either the motherboard audio or the front audio jack.

The output of:
```

[COLOR=#333333][FONT=Ubuntu]wget -O alsa-info.sh [/FONT][/COLOR][http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)[COLOR=#333333][FONT=Ubuntu] && chmod +x ./alsa-info.sh && ./alsa-info.sh --upload
[/FONT][/COLOR]
```
is here:
[http://www.alsa-project.org/db/?f=9d0fd47eac1878fa0e072b5097eceb70be7ff701](http://www.alsa-project.org/db/?f=9d0fd47eac1878fa0e072b5097eceb70be7ff701)

Thanks!!

Actually, I just tried installing the Realtek HD audio drivers.  Now there is no sound whatsoever.  New alsa-info output is here: [http://www.alsa-project.org/db/?f=354182b46a8bd0b41d65e191da1410196c7be03e](http://www.alsa-project.org/db/?f=354182b46a8bd0b41d65e191da1410196c7be03e).

Further, I can't even open sound settings or system settings because I get 
[CODE]
(gnome-control-center.real:3458): Gdk-ERROR **: The program 'gnome-control-center.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
[\CODE]
(I'm using gnome fallback)

---

### Post by Yellow Pasque on 2014-06-12
Seems to be a general problem with ALC1150 codec:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)

Try the workaround listed in that bug.

> Actually, I just tried installing the Realtek HD audio drivers.
I can't remember the last time those drivers actually helped a user. More often then not, it doesn't end well... (It is nice that Realtek provides the info to ALSA devs though.)

---

