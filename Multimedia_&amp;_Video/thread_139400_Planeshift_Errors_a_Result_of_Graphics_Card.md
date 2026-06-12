---
title: "Planeshift Errors a Result of Graphics Card?"
date: 2006-03-04
forum: Multimedia &amp; Video
---

### Post by BitTorrentBuddha on 2006-03-04
Hi, I have an onboard graphics card at this moment, I also have the game, Planeshift, installed correctly (or so I believe.) However on the screen the visual doen't display right, everything moves with extreme delay and the mouse doesn't disappear from it's old location, just appears also at the new one and 5 places between the two points. I am hoping this is an issue with my graphics card, but before I go out and buy a new one I would like to be sure. 
[PS; If I need a new card, I should look for nvidia, right? It's ati that doesn't support linux if I remember.]
[PPS; here's my output when running it ```
DEBUG: Sound System: Software Renderer Initializing..
DEBUG: Sound System: Configured for driver [crystalspace.sndsys.software.driver.oss]
Sound System: OSS driver for software sound renderer initialized.
  Indirect rendering may indicate a flawed OpenGL setup if you run on a local
  X server.

planeshift.application.client:
  PlaneShift Crystal Blue
  This game uses Crystal Space Engine created by Jorrit and others
  0.99 r0 [Unix-x86-GCC]
All LOGS are off.
Mounting skin: /this/art/skins/default.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.

```]

---

### Post by BitTorrentBuddha on 2006-03-04
here is an image incase I wasn't clear about what the visual looked like
[[IMG]http://img163.imageshack.us/img163/8028/screenshotcrystalspaceapplicat.th.png[/IMG]](http://img163.imageshack.us/my.php?image=screenshotcrystalspaceapplicat.png)

---

### Post by BitTorrentBuddha on 2006-03-04
bump

---

### Post by Aewheros on 2006-03-04
Planeshift in its current stages needs much more powerful hardware than it should due to poor optimization. It is also rather unstable and buggy. Running it on an onboard graphics card is nothing I would recommend in any case.

Considering a new graphics card, you're perfectly right: Nvidia provides official linux drivers.;)
But don't get a new one just because of Planeshift. It is not worth it, the game is in pre-alpha stage and just a tech demo this far.

I know the Planeshift forums can be chaotic, spammed and full of noobs... but I'm afraid the right place to get support is over there.

---

### Post by BitTorrentBuddha on 2006-03-04
ahh, thanks for the advice, but I really would like to play it and in all honesty I need a new graphics card anyway, and the geforce4 is pretty cheap. But I'll go check out the ps forums then.

---

### Post by mattmill30 on 2008-05-19
hi,

I had a simular issue, with 0.4.0.0, very jumpy graphics, about a seconds mouse latency.

After messing around with my graphics drivers, i removed libgl1-mesa-swx11 and installed libgl1-mesa-glx.

If anyone else is still having this problem, try that.

I also installed several other packages, but i think its the one that i've mentioned above that sorted the problem.

If not the full list of applications i installed and removed was:

Removed the following packages:
libgl1-mesa-swx11

Installed the following packages:
libgl1-mesa-dev (7.0.3~rc2-1ubuntu3)
libgl1-mesa-glx (7.0.3~rc2-1ubuntu3)
libgle3 (3.1.0-6)
libxxf86dga-dev (2:1.0.2-1)
libxxf86misc-dev (1:1.0.1-2)
libxxf86vm-dev (1:1.0.1-2)
x11proto-xf86dga-dev (2.0.3-1)
x11proto-xf86misc-dev (0.9.2-4ubuntu1)
x11proto-xf86vidmode-dev (2.2.2-4ubuntu1)
xlibmesa-gl-dev (1:7.3+10ubuntu10)

---

