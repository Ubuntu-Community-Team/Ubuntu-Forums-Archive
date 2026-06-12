---
title: "Install Codecs and MPlayer"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by zazazazaza on 2007-07-30
Hello!
I have Ubuntu 7.04
And 2 weeks ago I was download codecs, and MPlayer-1.0rc1.tar  But I don't know how is it install on my computer??!!!!
Please, speak to me, how can I install this,  or give me links on my question!!!
P.S.
Sorry for my English

---

### Post by ThrobbingBrain66 on 2007-07-30
Mplayer and all the codecs you'll need are in the repositories.  First, go to System>Administration>Software Sources and make sure you have the universe and multiverse repos enabled.  Then do a 
```
sudo apt-get update
```
```
sudo apt-get install mplayer
```

For codecs, do a search for gstreamer within synaptic and choose whichever you'd like to install.

---

### Post by linuxwizard on 2007-07-30
These are the codecs you are looking for in Synaptic.
[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)
[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats)



Then go here to install libdvdcss2 package & w32codecs
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cotcot on 2007-07-31
I got them through Automatix2.

---

### Post by aysiu on 2007-07-31
I think you should understand how software installation works. Using a .tar file should be a last resort for a beginner.

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by zazazazaza on 2007-08-01
**2 all**  Thank you
I will try!!

---

### Post by fredj on 2007-08-03
At the top of the multimedia forum there are complete instructions for installing all
the codecs you need. You may also need to install lame through the Synaptic
Package manager (for complete mp3 support).

---

