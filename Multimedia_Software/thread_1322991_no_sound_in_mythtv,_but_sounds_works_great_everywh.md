---
title: "no sound in mythtv, but sounds works great everywhere else? After 9.10 upgrade"
date: 2009-11-11
forum: Multimedia Software
---

### Post by bgiannes on 2009-11-11
I just upgraded to 9.10, mythtv upgrade from 0.21 to 0.22 all packages updated.

Two problems;

1) The sound in mythtv stopped working, i'v tryed going through the different sources in the sound setup but nothing?

funny thing when ubuntu reboots, and mythtv auto-loads the welcome chime is cut short, as if mythtv kills it mid way?

2) in mythvideo videos are paused and don't play the screen just shows a static frame.

Note:  mplayer, vlc, xbmc, sound tests all work 100% sound a pictures are great.

help please.

---

### Post by bgiannes on 2009-11-12
answer:

1) goto /home/[yourusernamegoeshere]/.profiles file and add this line to the end of the file

export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1 

reboot

(i did install pavcontrol and set all the volumes to full, but i don't think this is a part of the fix?)

2) Go into media setting menu find the commandline command for the mplayer, and change it to "Internal".  mythtv said they will fix this bug w/ the 0.23 update.  But for now, i can watch my stuff.

---

