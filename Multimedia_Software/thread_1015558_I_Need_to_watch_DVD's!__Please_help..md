---
title: "I Need to watch DVD's!  Please help."
date: 2008-12-18
forum: Multimedia Software
---

### Post by iNeeed on 2008-12-18
Maybe someday I can rename myself iHelp.  In the meantime. . .

I can't play dvd's and its driving me crazy.

I've tried Totem and VLC.

So far I have done this sudo 

wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

and 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

and 

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

Mind you I have no idea what I'm doing.  Just copying and pasting from another thread.  Any help is GREATLY appreciated!

---

### Post by jrusso2 on 2008-12-18
You need libdvdcss2 all the other stuff you got has nothing to do with DVD.

---

### Post by iNeeed on 2008-12-19
> **jrusso2 said:**
> You need libdvdcss2 all the other stuff you got has nothing to do with DVD.

Thanks.  I'll look into that.

---

### Post by iNeeed on 2008-12-19
Progress.  Totem and VCL are now playing the DVDs.
The audio is fine.  The video is blinking rapidly and sporadically.
Any suggestions?

---

### Post by iNeeed on 2008-12-19
Working now.  Found solution somewhere.  Can't trace my steps. . in internet frenzy

In VCL 
Went into "tools" then 'preferneces"
Then changed the video output to X11 video output.  

Its working great now!

Thanks for the tip.

---

