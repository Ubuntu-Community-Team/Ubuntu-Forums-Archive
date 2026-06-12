---
title: "mplayer keyboard input when called from mythfrontend"
date: 2009-03-16
forum: Mythbuntu
---

### Post by nblender on 2009-03-16
I have a 9.04 (upgraded from 8.10) Early 2009 MacMini (3,1?) as a mythfrontend.  I'm using an apple aluminum bluetooth keyboard as my 'remote'.  I have gdm configured to automatically log in as user 'mythtv' and launch mythfrontend from a script called via /usr/share/xsessions/mythtv.desktop. Keyboard input works just fine within the mythfrontend menus and using the Internal player.  However, if I cause mplayer to be executed due to some video file that is configured to play with mplayer instead of the Internal player, then mplayer does not receive any of my keyboard input while showing the video...  Instead, all keys that I hit seem to get buffered until I pkill mplayer. Those keys then are read by mythfrontend. 

I've tried specifically passing a -input argument to mplayer via the mythfrontend configuration... 

Other frontends that I have don't suffer this problem but this is the only frontend on which I'm running the normal desktop. Other frontends I just run OpenBox...

Anyone have any ideas?

---

### Post by nblender on 2009-03-16
addendum:

If I run mplayer from an xterm instead, it gets keyboard input just fine.  Only when mplayer is called from mythfrontend does it not receive input.

My current theory is that even though mplayer is run fullscreen, it somehow doesn't have window manager focus.. I've tried various alt-tab and so forth but nothing seems to work...

---

### Post by Lorenzo1985 on 2009-04-01
I have exactly the same problem after an upgrade.

Anyone got any ideas?

---

### Post by nickrout on 2009-04-01
such problems are often caused by mplayer not receiving focus, which is why most myth setups are recommended to have a window manager.

strange to see it popping up at this stage though, I haven't seen this issue on the lists for a long time.

You could try using alt-tab to try and switch focus (dunno what the mac keyboard equivalent is)

EDIT: oops just read the second post, looks like you figured what I was saying already, sorry for the noise.

EDIT2: can you craft a custom command to run mplayer from a terminal. something like ```
xterm -e mplayer [mplayer options] 
```

Dunno if this will make a difference or not!

---

### Post by gooberto on 2009-09-08
I was having a similar problem where mplayer would stop responding to keyboard input commands like spacebar for pause/play. By running mplayer in a terminal window I was able to see the following repeatedly:
No bind found for key 'JOY_RIGHT'.-JOY_AXIS2_MINUS-JOY_AXIS5_MINUS-JOY_AXIS3_PLUS-JOY_AXIS4_MINUS-SPACE 

my xbox 360 controller was interfering with the keyboard input and I was able to resolve it by disabling the joystick in /etc/mplayer/mplayer.conf by adding nojoystick=1 at the bottom

---

