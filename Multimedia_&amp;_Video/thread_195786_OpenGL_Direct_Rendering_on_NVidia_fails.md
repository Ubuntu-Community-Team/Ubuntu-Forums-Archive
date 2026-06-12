---
title: "OpenGL Direct Rendering on NVidia fails"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by Juzz on 2006-06-13
I have installed the 8762 drivers from NVidia - the NVidia X Server Settings claims that OpenGL direct rendering is active, but in Cedega my system fails the OpenGL Direct Rendering :( 
It worked under Breezy, both with 7676 and the 8762 drivers and I just upgraded to Dapper this week, but I need the OpenGL Direct Rendering.

Have you any ideas how I can test and/or getting it working again?

My system is:
PIV 2.8GHz
NVidia 6600GT
2GB Ram
SB Audigy
Atheros based wireless network (module for this is separately compiled from the source from madwifi.org)
And of course Ubuntu Dapper 6.06

For reference here is my post at transgaming:
[http://transgaming.org/forum/viewtopic.php?t=6166](http://transgaming.org/forum/viewtopic.php?t=6166)

---

### Post by bruce89 on 2006-06-13
Are you using XGL, as direct rendering doesn't work with XGL.

---

### Post by Juzz on 2006-06-14
No, I had it in shortly, but it has been removed now.

---

### Post by anttch360 on 2006-06-15
I also have the same problem.
P4 3 GHz
Nvidia 6600 GT
1.5 Gigs Ram
Ubuntu 6.06
Here is a screenshot.
Edit forgot to add that I'm also using the 8762 driver

---

### Post by Juzz on 2006-06-16
This is weird, if I go into a terminal and do this:

cedega .cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl

(And have 'SET gxApi "opengl"' in my Config.wtf)
Then I can run the game with OpenGL rendering and it is actually running a lot better than ever...

---

