---
title: "I can't install MPlayer 1.0rc2"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by tachibana on 2007-12-01
Hello everyone,
I am trying to install mplayer rc2 since i installed ubuntu 7.10 but i couldn't do that. I am always getting an error like "The GUI requires libavcodec with PNG support (needs zlib).". What do i have to do for that?

Thank you.

---

### Post by mattydee on 2008-02-15
You need to install  libavcodec-dev using apt-get or synaptic which will install zlib also.

You also need xorg-dev if you want to build the gui, as well as libgtk2.0-dev.

---

### Post by andrew.46 on 2008-02-20
Hi,

 As has been pointed out you need a few dev files:

> **tachibana said:**
> Hello everyone,
I am trying to install mplayer rc2 since i installed ubuntu 7.10 but i couldn't do that. I am always getting an error like "The GUI requires libavcodec with PNG support (needs zlib).". What do i have to do for that?

Thank you.

Perhaps you could have a look at the svn mplayer page on the forums, just leave out the svn pieces and use the skins, dev files, OSD fonts info and configure options:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

     Andrew

---

