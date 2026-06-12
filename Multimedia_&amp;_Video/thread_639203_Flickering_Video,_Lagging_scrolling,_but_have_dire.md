---
title: "Flickering Video, Lagging scrolling, but have direct rendering"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by Criminosis on 2007-12-12
I just finished getting my ATI card (feeling that alone is what is going to be the cause) working with compiz without the XGL server backing through envy, and just got the dual screen (or head) properly running aswell.

However i've been stricken with something most unusual. 

Videos now flicker non stop during playback. Audio is fine, they just flicker. and it seems all media types are (WMV, AVI, MP4 are what i tested). Doesn't matter on either screen, they just flicker. 

Stranger yet, the videos actually flicker THROUGH other windows. For example, if i have firefox on top of totem (or mplayer) the video shows on top of firefox. Not the totem window, _just_ the video.

Scrolling through files and web pages causes visual lag.

Oddly though, i have Direct Rendering, and glxgears reports over 3 thousand, with some minor flickering (but it also shows through windows on top of it). 

UPDATE : I just turned off my Compiz and all the problems disappear. so all of this applies when compiz alone is running, any thoughts?

My card is the X1600 ATI Radeon, using the latest driver (installed by Envy), running dual screen.

---

### Post by Criminosis on 2007-12-13
bumpity

---

### Post by javidjamae on 2008-01-06
I have the same exact problems. I installed envy to get direct rendering support, but now I get minor flickering on glxgears, major flickering when movies play (DVD, MPEG, etc.), slow scrolling, and slower response on my compiz than when I installed the proprietary drivers. I have an ATI Mobility Radeon X1400 (single screen) with a resolution of 1680X1050 set to 60 Hz.

BTW: I can get video to play properly when it is running full screen, but if there are any desktop elements showing, then it runs slow.

Is this just a performance problem with the open source drivers?

---

### Post by imoatama on 2008-01-06
First off if you installed Envy and it installed drivers for you, then you aren´t using the open source video drivers, you&#341;e using the proprietary ones.

Video flicker when running Compiz is a known problem with the ATI drivers since driver version 8.42. I thought it would be fixed in (December´s release) 7.12, though it looks as though my video still flickers and I have those drivers. Hopefully ATI will fix it in the next release.

In the meantime, a workaround is to set your video output to X11 instead of Xvid. Instructions for doing so can be found here: [http://ubuntuforums.org/showpost.php?p=2892802&postcount=6]("http://ubuntuforums.org/showpost.php?p=2892802&postcount=6")

---

### Post by samosamo on 2008-01-20
Version 8.1 and the problems you report still exist for me too.

imoatama posted a great guide on getting the video to stop flickering, works great full-screen too.  Too bad scrolling is still laggy though.

See you next month for 8.2!

---

### Post by indridi on 2008-02-09
I have a dell inspiron with ati radeon HD 2600 card, and had this problem. The workaround described at [http://ubuntuforums.org/showpost.php?p=2892802&postcount=6](http://ubuntuforums.org/showpost.php?p=2892802&postcount=6) solved it

thanks

---

### Post by forrestcupp on 2008-02-09
The video workaround is great, but it doesn't solve the opengl flickering problem and the scroll lag.  There is no workaround for those things.  Until ATI fixes their drivers, I'm forced to not use Compiz.  I hope they get this worked out with this month's drivers.  I'm not getting my hopes up, though.  We've already waited this long.

---

### Post by FlashPratt on 2008-05-04
Same problem here as well (OpenGL flickering). 
Running Ubuntu 8.04 with ATI x1400 and Inspiron E1705. 

Workaround: Turning off the desktop effects (compiz?) stops the flickering.

---

### Post by RebateFX on 2008-05-10
> **FlashPratt said:**
> Same problem here as well (OpenGL flickering). 
Running Ubuntu 8.04 with ATI x1400 and Inspiron E1705. 

Workaround: Turning off the desktop effects (compiz?) stops the flickering.

Funnily enough, yes it does. Even funnier, just trying that, then switching compiz back on appeared to have fixed my flickering with gl rendering.... but only in fullscreen mode :lolflag:

---

