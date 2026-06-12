---
title: "Fixing white and black levels in xv (X video extension) fur i810"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by jojo4u on 2007-03-30
I have an issue with correct black and white levels with Xubuntu/Ubuntu.
As introduction a quote from [Wikipedia]("http://en.wikipedia.org/wiki/BTB"):

Blacker-than-Black - PC RGB, 100% black starts off at 0 and 100% is at 255. Studio RGB, 100% black is at 16, and 100% white is at 235. Anything lower than 16, say from 0 - 15, that's below black, and anything higher than 235, from 236 - 255, that's above white.

I have attached I zip published by Mark Sydow [here]("http://www.avsforum.com/avs-vb/showthread.php?p=5525270&&#post5525270") which shows wether you are affected. For convinience, I attached it to this post.
Play the file VTS_01_1.VOB with your favorite media player - I'm using mplayer. Pause on the first black screen. If you own a CRT, crank up the brightness. If you own a TFT, adjust contrast so that the dim white greay are distinguishable.
If I set video output to gl or x11 and play the attached VTS_01_1.VOB everything below level 16 (reference black) is as black as the background. This happens, because the levels 16...235 are expanded to 0...255. If I set video output to xv, I can see bars all the way down to 0, making black in most movies look greyish.
The natural solution to this problem is to adjust you screen, but you can't do this with a machine which is not complety dedicated to video presentation.

Under Windows, this problem was introduced with VMR9 and there are quite a few solutions:
1. video driver update
2. forcing RGB or adjust within FFDShow
3. use AVISynth
4. use a shader for Media Player Classic
Unfortunately, none of this options are viable for Linux.

The "ATI Radeon Video Overlay" driver supplies the variable XV_COLORSPACE acessible by xvattr, the i810 does not have this option. gxine exhibits the same behaviour, vlc is wrong at all devices.
So, how to fix? Am I stuck to x11/gl? (Which are < 10% CPU load on a DIVX movie on  my Merom, so that's not too much a problem).

setup:
Xubuntu edgy
default X
default i810
default mplayer (0.99+1.0pre8-0ubuntu8)
Intel i945GM chipset
1024x768 24 bit
DRI enabled

---

