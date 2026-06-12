---
title: "h264 hardware decoding"
date: 2010-11-16
forum: Multimedia Software
---

### Post by KillerSponge on 2010-11-16
Hello all,

I currently have a nice media center with XBMC and an onboard ATi graphics chip. Most of the times this works fine, but since the graphics card doesn't give me hardware decoding of h264, the CPU (a meager AMD Sempron) has to bear the full weight of the decoding, and sometimes it buckles, which leads to choppy framerates and lag.

So now I am looking for a way to get the video to play smoothly. I think a cheap dedicated graphics card will do, but will this work with Ubuntu and XBMC? And do you guys have any recommendations as to the brand or model that is most suitable for this?

Thanks in advance!

---

### Post by no2498 on 2010-11-16
this helps me open a terminal type smplayer click enter
it tells you how to install it
it loads some more 264 codes for ff


hope it helps you too

---

### Post by KillerSponge on 2010-11-16
Thanks for the reply, but I tried it and it didn't really change anything, framerates are still very choppy with some files. And I really would like some hardware decoding, so my CPU can do other stuff :)

---

### Post by cchhrriiss121212 on 2010-11-16
Nvidia gt210, which has full vdpau (i.e. GPU decoding) support. Video playback with vdpau will only take up a maximum of 10% cpu usage.

---

### Post by Yellow Pasque on 2010-11-16
If your XBMC is current enough (i.e. includes this commit made on 4/6/10: [http://trac.xbmc.org/changeset/29053](http://trac.xbmc.org/changeset/29053)), then you can use VA-API from: [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)
You'll need the libva(-dev) and xvba-video packages. 

You'll also need Catalyst 10.10: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)
On top of all that, you may have to build XBMC from source to include the ATI support found in libva-dev from the link above. :\

---

