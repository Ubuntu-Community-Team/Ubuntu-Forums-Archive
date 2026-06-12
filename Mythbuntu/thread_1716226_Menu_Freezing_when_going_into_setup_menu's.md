---
title: "Menu Freezing when going into setup menu's"
date: 2011-03-28
forum: Mythbuntu
---

### Post by beardos on 2011-03-28
I'm at the very early stages of a new build using a AMD E350 APU.
When using QT render engine I can go into all the sub-menus in the system (Setup menu's) but when I use OpenGL, when stepping into the Setup menu's or any menu come to that matter, the screen doesn't go into the bottom screen. This is the same for the Backend and front end (Both on the same system).
I'm using the Catalyst 11.2 drivers with the setup proces I followed here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

to get into these menu's I have to reset the frontend (mthtv fronend -- reset) command, but again, re-enabling the OpenGL does exactly the same thing.
I'm also unable to play any media at all with OpenGL enabled, but can with QT engine.

I do realise that I'm using very new hardware and the drivers may not be up the job yet, but I was under the impression that AMD drivers have come on leaps and bounds over the last year or so and that for playback of media, this should be fine.

Any help advice would be greatly appreciated.

---

### Post by nickrout on 2011-03-30
is opengl working? Play with glxinfo, glxgears etc.

---

