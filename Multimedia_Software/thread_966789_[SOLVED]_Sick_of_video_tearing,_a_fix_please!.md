---
title: "[SOLVED] Sick of video tearing, a fix please!?"
date: 2008-11-01
forum: Multimedia Software
---

### Post by theduffman on 2008-11-01
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9800
OpenGL version string: 2.1.8087 Release

Intrepid, fresh install all updated, graphics are fine i can use compiz but choose not to.  btw: Mplayer wont work anymore with "xv" (the default) and with "x11" set i cant get it to go fullscreen, so im using VLC which works nice, except for tearing and im now fed up of it, so much so i may just go back to bill. I`d rather not so can anyone tell me how to get vsync enabled with my setup.  It also might fix the UT2004 vsync issue ive had forever and why i play it in XP still.  Ive set vsync in the config files but it has side effects, like movement is stuttery, whereas its fine without vsync but gives me tearing.

Cheers all

---

### Post by theduffman on 2008-11-12
Ive fixed the tearing in videos at least by running ati control centre (applications/accessories) setting Vertical Sync to `always on' and choosing OpenGL and the output in VLC.

---

### Post by michande03 on 2008-11-17
tested to use vertical refresh always on, but still not able to watch movies in full screen on either mplayer or vlc, but works if using in small player mode without flickering if using X11 output, without compiz running it works just fine with xv output and full screen.

Another setback is some 3D games not working, with or without compiz running, for example Torcs becomes like watching the other racers drive around and a small window at top showing only sky and horizon, so hadr to see where to steer :).

Also when doing fgl_fglrxgears lots of flickering in gearbox with compiz activated, no flickering when compiz off.

Am using latest fglrx prop drivers on ati radeon 9800 pro 256mb

OMG works like a charm without compiz, but with compiz it really suxx with playing video on mediaplayers, tested a lot of things, well seems like it is to wait for new fglrx drivers and plan video viewing and kill compiz during videoplay :(

---

### Post by anxean on 2008-11-18
I have the ati 4850 running and I cant get any vsync with compiz from the ati control center or by the "sync to vblank" option in the compiz control.  any suggestions

dro@dro:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release

Edit: im running intrepid

---

### Post by vhozard on 2009-11-10
[http://ubuntuforums.org/showthread.php?t=1320484]("http://ubuntuforums.org/showthread.php?t=1320484") fixed it for me.

---

