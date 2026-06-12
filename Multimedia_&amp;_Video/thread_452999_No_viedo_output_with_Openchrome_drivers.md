---
title: "No viedo output with Openchrome drivers"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by lsalminen on 2007-05-23
I have installed everything necessary to enable Ubuntu 7.04 to be able to play VCDs and DVDs:

MPlayer
VLC media player
"Ubuntu restricted extras"
libdvdcss2
w32 codecs

I get a sound output, but no video/picture.

I tracked the problem to this: 
[http://www.openchrome.org/trac/ticket/40]("http://www.openchrome.org/trac/ticket/40")
But, there is no answer there.

Any ideas?

Thanks in Advance.

lee

---

### Post by lsalminen on 2007-05-23
Problem solved.

In VLC, you have to go to Preferences, and change video output to X11... That solved my problem in case anyone else needed to know.

-Lee

---

