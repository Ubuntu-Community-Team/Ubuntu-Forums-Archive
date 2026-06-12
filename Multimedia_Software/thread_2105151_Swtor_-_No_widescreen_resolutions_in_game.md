---
title: "Swtor - No widescreen resolutions in game"
date: 2013-01-15
forum: Multimedia Software
---

### Post by Haelind on 2013-01-15
Running Ubuntu 12.04 and a compiled version of wine 1.5.20 with the patch to run swtor.  Nvidia proprietary driver 304.64  Have all the necessary dll files loaded into wine.  Start the game with the res at 1000x614 so the login screen will work.  Get into the game fine but..  There are no widescreen options in game to choose from. The list is just the standard: 800x600, 1024x768 and so on, of which I can change to any of these without issue.  This happens with either, 1 installing the game in linux or 2 moving a copy from Windows over to the linux partition.  I usually play the game in Windows in 1440x900.  I guess my question is, What would cause me to loose or not have any widescreen resolutions in swtor in linux?  Any suggestions would be most appreciated as I've searched the net for days for an answer.

---

### Post by Haelind on 2013-01-16
Anyone?  Bueller Bueller?:popcorn:

---

### Post by Haelind on 2013-01-21
Ok, seeing as how I'm the only one on the planet that seems to have this issue lol

How about I address this a different way.

The following script that sets the launcher window so you can see it to login, actually passes the resolution of 1000x614 into the game list itself and becomes a choice in the graphic settings of swtor:.

```
#!/bin/sh
export WINEPREFIX="$HOME/WineBottles/swtor"
export LD_LIBRARY_PATH="/usr/lib32/:/usr/lib/"
export WINEARCH=win32
/var/chroot/wine/wine explorer /desktop=SW:TOR,1000x614 "C:\SWTOR\launcher.exe"
```Is there a way to pass more resolutions into the game via this bash script?
Does anyone else have widescreen resolutions in swtor in linux?

---

### Post by Haelind on 2013-01-31
> Does anyone else have widescreen resolutions in swtor in linux?     No one? really?  
Am I to believe that everyone who plays the game, plays it in a standard resolution?

---

