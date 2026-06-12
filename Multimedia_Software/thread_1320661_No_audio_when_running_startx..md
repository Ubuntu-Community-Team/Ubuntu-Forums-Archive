---
title: "No audio when running startx."
date: 2009-11-09
forum: Multimedia Software
---

### Post by Argyled on 2009-11-09
Due to problems with X ([https://bugs.launchpad.net/bugs/471844](https://bugs.launchpad.net/bugs/471844)) and gdm ([https://bugs.launchpad.net/bugs/441638](https://bugs.launchpad.net/bugs/441638)), I had to disable gdm using the advice given here: [http://ubuntuforums.org/showthread.php?t=1305659](http://ubuntuforums.org/showthread.php?t=1305659).

However, this has highlighted a new problem that I can't seem to find a solution to.  Now that I'm logging into a terminal and starting X manually (startx), my audio no longer works.  It seems that my hardware isn't being detected in X.

In a gnome-terminal:
```
aplay -l
aplay: device_list:223: no soundcards found...

```However, if I use <ctrl><alt>F1 to get a virtual text console and enter the same command, I get:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Also, when I switch to the console, any audio that I have playing (i.e. music in rhythmbox) will suddenly become audible, but when I switch back to the gnome session, the music goes away again.

When gdm is running, X has no problem with audio.  I can't switch back to gdm, though, because actually logging in through it is quite an ordeal involving lots of crashes and losing access completely to my text consoles.  Also, if I startx as root (i.e. sudo startx), the audio works (but then I'm in a root session).

What am I doing wrong here?

---

### Post by Somme on 2009-11-09
```
adduser <username> audio

```

Restart your PC and let us know whether it works or not.

---

### Post by Argyled on 2009-11-09
Somme,

That did it, though I did have to add a "sudo" to the front of it.  You know, I looked everywhere I could think of for some indication that this was a permissions problem, but I didn't see anything in the log files.

Thanks for your help!

---

### Post by kirklander on 2009-12-12
Thanks. I was having the exact same problem, and going batty trying to figure it out. 

Can anyone point me towards a resource where I might learn why this fixes the problem, or just general information about this topic? Thanks.

---

### Post by 666f6f on 2010-04-19
It is possible that [Bug #483130]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130") prevents audio from working.

---

