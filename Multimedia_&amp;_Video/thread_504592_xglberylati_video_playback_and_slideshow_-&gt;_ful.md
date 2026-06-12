---
title: "xgl/beryl/ati video playback and slideshow -&gt; fullscreen question.."
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by slomodo on 2007-07-19
hi there,

i have thinkpad z61p with ati fire gl 5200 (x1600 radeon) running feisty with xgl/beryl (0.2.0)/fglrx (8.34.8) with res. 1920 x 1200,. all superstabile, smooth and fun to work with it, but when switching to fullscreen in gThumb,
f-spot, mplayer, totem, helix i get application running without any problems but only on a half-screen..VLC player works in fullscreen mode without any problems..that is a bit strange. Anyone have similar problem? ..or better put... simple solution? atm. i am out of ideas..
thanx for your answer

slomodo

---

### Post by wolfen69 on 2007-07-19
could be a driver issue. download envy and use provided driver.
```
sudo apt-get install envy
```

---

### Post by slomodo on 2007-07-19
"..could be a driver issue. download envy and use provided driver..."

ermmmm...that blew up my xgl/beryl set-up..juhuuu.. ;) .. after running "envy" i got garbled screen, but indeed a new driver and no DRI.

user@computer:fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

..looking at the "envy" looks a bit dirty underneath...and result is:


user@computer: sudo less /var/log/Xorg.0.log

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

i try to tinker a bit around with it as its pretty cool to have latest driver. worst case scenario is going back to old set up.
envy is one great idea but i guess might just work for most ppl ,not in fragile xgl/beryl set up..
thanx for a suggestion but, any other ideas?

slomodo

---

### Post by slomodo on 2007-07-19
ok here i have one nice new driver with xgl/beryl running smooth:

user@computer fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200
OpenGL version string: 2.0.6474 (8.38.7)

..but - no cigar. mplayer still does half-screen smooth video play  (gl2 video driver still crashing xgl session),  f-spot displays slideshow on half-screen - really strange effect, i guess it has to do something with resolution. i will look into Gnome settings...or xorg.conf. could be that 1920 x 1200 is somewhat high, but couldn't be. 
 however there is some improvoement "eye of gnome" displays photos in fullscreen properly - all smooth..
VLC works as usual - fullscreen. totem not. 

i also noticed that ATI catalyst center doesn't start anymore. 
eh, so much for proprietary stuff.

any help in improving fullscreen video play would be cool.

thanx for the attention.

slomodo

---

