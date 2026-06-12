---
title: "VLC install problem"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by dutch1918 on 2007-06-13
I am trying to install VLC and the other required files but I get the following:

Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb](http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb](http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb)  404 Not Found

How can I resolve this?

---

### Post by stchman on 2007-06-13
> **dutch1918 said:**
> I am trying to install VLC and the other required files but I get the following:

Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb](http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb](http://medibuntu.sos-sts.com/repo/pool/free/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu4+medibuntu2_i386.deb)  404 Not Found

How can I resolve this?

VLC is not in the Medibuntu repositories.

Try this:

sudo apt-get install vlc mozilla-plugin-vlc

That should do it.

---

### Post by dutch1918 on 2007-06-13
I am using apt-get... here is the full err message

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free libavcodec0d 3:0.cvs20060823-3.1ubuntu4+medibuntu2
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free libavformat0d 3:0.cvs20060823-3.1ubuntu4+medibuntu2
  404 Not Found

---

### Post by dutch1918 on 2007-06-14
Resolved the problem. Found out that they changed from .com to .org so you will need to update your repositories. Goto [http://medibuntu.org](http://medibuntu.org) for further info/help

---

