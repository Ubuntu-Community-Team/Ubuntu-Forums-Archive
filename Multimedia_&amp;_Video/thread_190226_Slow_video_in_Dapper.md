---
title: "Slow video in Dapper"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Zariski on 2006-06-06
Hello,

Since installing Dapper (fresh install) my video playback has become terrible. It worked fine in Breezy and earlier versions. Full screen playback is horrible, and even in small size video and sound don't fit together. The problems also come up in flash players like YouTube and Google Video.

I noticed that when installing I had to choose "safe graphics mode". Does anybody have an idea how to speed up things?

Thanks!

-- 
Zariski

---

### Post by djchuang on 2006-06-07
Brand new user to Ubuntu 6.06, less than a day using it, and noticed the same symptoms -- there's an annoying time lag in the audio on many (most? all?) YouTube videos. 

I'm using a Dell Inspiron 600m, with a partitioned default Ubuntu install, new Macromedia Flash install. No changes to drivers or settings (yet). Hope to find some help here! :)

---

### Post by giorg on 2006-07-08
Hi,

experiencing same problem here. On breezy everything was fine, with dapper video (fulls screen) absolutely slow. Any solution? By the way, codecs (and not only) installed through automatix this time, did not do in breezy... maybe is related to this?

Andrea

---

### Post by onlysolution on 2006-07-08
Try installing Mplayer and/or VLC, see if those work better. In both of those you can change the video-playing drivers (xv, gl, etc) in the prefences/settings window. Try ou the different ones and see if that improves anything.  Search these forums about the Flash sound lag (there is at least one HowTo on the subject,) that is a known issue and a fairly easy fix.

---

### Post by giorg on 2006-07-09
> **onlysolution said:**
> Try installing Mplayer and/or VLC, see if those work better. 

Hi,

actually I had everything already installed but did not play with options (never needed before....). But hanks to you I did, and with MPlayer the only working video output codec is gl2. I still think something is wrong, but at least I can use it now...

Thanks

Andrea

---

### Post by tospig on 2006-07-09
I had the same problem, but thanks to this thread I played around with the codecs, and now everything is working fine.

(X11 is the codec that works for me)

---

### Post by mattalves on 2006-09-27
From another forum post (by disturbed1):

In a terminal, type

sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc

And then change FIREFOX_DSP="none" to FIREFOX_DSP="aoss" in the file.

Save it and restart Firefox, your YouTube issues should be fixed.

Cheers.

---

