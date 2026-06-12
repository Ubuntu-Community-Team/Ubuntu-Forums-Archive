---
title: "vlc has issues?"
date: 2009-08-22
forum: Multimedia Software
---

### Post by hwttdz on 2009-08-22
So I've installed vlc, libdvdread4, libdvdcss2 and w64codecs (I have a 64 bit machine).  And I get this:

[IMG]http://img199.imageshack.us/img199/553/screenshotnhy.png[/IMG]

I have tried various different video output types.  Additionally I have gotten the error "spudec error: overflow in SPU next command sequence".  Another funny thing is that vlc opens up two output windows, one of them does this, and the other is black.  Sound is also choppy.  Any suggestions?

Oh yes, I also ran the libdvdcss2 script and have ubuntu-restricted-extras installed.

---

### Post by hwttdz on 2009-08-22
So after much searching I found 

[http://forum.videolan.org/viewtopic.php?f=12&t=63355](http://forum.videolan.org/viewtopic.php?f=12&t=63355)

The upshot is you should try removing ~/.dvdcss

so
 
"rm -rf ~/.dvdcss"  

Hope that helps.

---

