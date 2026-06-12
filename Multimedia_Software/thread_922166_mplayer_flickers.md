---
title: "mplayer flickers"
date: 2008-09-17
forum: Multimedia Software
---

### Post by heiNey on 2008-09-17
hi, im having a problem with mplayer.  im trying to watch videos and it flickers a lot...i tried changing the available drivers in the preferences to gl and gl2, and they all flicker.  changing it to x11 gets rid of the flicker, but then i cant watch videos fullscreen (hitting the fullscreen button makes the video play in a little area in the center, and the rest of the screen is just black)

ive tried vlc, but it lags and the picture looks blocky.

video was working perfectly fine when i was running gutsy, upgraded to hardy this week and now the video is doing this.  i also have compiz turned on now in hardy and i didnt have it on before in gutsy.

system specs:

Intel Core2Duo T7200 2.0Ghz
2 Gigs RAM
Video Card: ATI Radeon X1400

---

### Post by heiNey on 2008-09-17
well, i removed compiz and it seems to be working fine now.  ill sacrifice compiz for good video quality i guess.

---

### Post by aeiah on 2008-09-17
make sure you tried all the video output options. i cant remember which one works for me, probably one you've already tried to be honest, but mplayer should play nice with compiz on ati stuff i think (i have nvidia, however).

perhaps you should give xine a shot. apart from HD content, i find it just as good as mplayer

---

### Post by stephanvaningen on 2008-10-19
Can you try this, and compiz should work while still having non-flickering video:
 sudo gedit /etc/X11/xorg.conf
In the "Device" section, add:
 Option   "TexturedVideo"   "Off"
(source: [http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5](http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5))

Remark: On my machine this change [caused this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/281433"), but that's another thing...

---

### Post by lubo777 on 2008-11-04
thanks, that solved the problem with compiz-fusion and mplayer flicker :)

---

### Post by pyr0man24 on 2009-02-26
Solved!!!

I found that by running mplayer with the following arguments (highlighted in red), there is no flicker.  The picture quality is finally up to par with Window$.

mplayer -fs -x 1024 -y 576 [COLOR="Red"]-vsync -vo gl[/COLOR] %MoviePath

That's all there is to it. :D

Shame it took me 2 weeks to figure these settings out. 

AMD AM2 2.5Ghz
2 Gb RAM
ATI HD 3200

---

