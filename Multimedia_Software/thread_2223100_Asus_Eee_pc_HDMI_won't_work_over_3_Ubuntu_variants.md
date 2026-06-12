---
title: "Asus Eee pc HDMI won't work over 3 Ubuntu variants"
date: 2014-05-09
forum: Multimedia Software
---

### Post by AlbertaJeff on 2014-05-09
Hello, I have an Asus eee pc x101ch (with maximum 1 gb RAM).  This netbook couldn't run windows 7 starter so I Installed Ubuntu 14.  It couldn't handle the regular desktop it so I enjoyed the results of booting to the Metacity desktop where everything ran well.  Except for video playback.  It won't play on the desktop very well, but more importantly, the HDMI port is without audio and flickers with bad aspect ratio and poor video quality; the main reason I have this netbook is hdmi (which worked very well on win 7 starter).

 For the past 2 weeks I've Installed Ubuntu 12 (no good, video drivers are recognized but will not install - "error"), now i'm onto ubuntu 13 but it still won't run well, So, my question is:

Should I go back to ubuntu 14 metacity and try to install (an old kernel? - 3.2??) and then try to install the Intel Atom's cedarview drivers?  Is this possible?

I've been scanning these forums for an answer an there doesn't seem to be a way to get ubuntu 14 to work with my x101ch.

Thanks,

---

### Post by mörgæs on 2014-05-09
Hi, welcome to the fora.

Lubuntu 14.04 is a better choice.

---

### Post by trag on 2014-05-12
Try a distro meant for eepc's  give this a try [http://www.leeenux-linux.com/](http://www.leeenux-linux.com/)
good luck
trag

---

### Post by AlbertaJeff on 2014-05-15
Yeah, the Lubuntu is a great option for speed; alas the same issues with Intel's cedarview Atom and the HDMI still not working.

Trag, I wasn't aware of the Leeenux distro!  I'm trying this tonight, thanks!

---

### Post by AlbertaJeff on 2014-05-21
So the Asus Cedarview problem is (mostly) solved.  In order for the HDMI to work properly I had to go to Linux Mint (mate) which would allow the recognition of and installation of the cedarview graphics package through the software manager.  I then had to install the ALSA sound package so then I could switch the sound output from analog to hdmi.

I say (mostly) solved because when I'm not using the tv connected through hdmi, I can't get the netbook display beyond 800x600.

---

