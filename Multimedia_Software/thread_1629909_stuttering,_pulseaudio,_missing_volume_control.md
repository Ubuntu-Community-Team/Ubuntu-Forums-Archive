---
title: "stuttering, pulseaudio, missing volume control"
date: 2010-11-24
forum: Multimedia Software
---

### Post by PeterOfTheCosmos on 2010-11-24
Hi all,

Please forgive my ignorance, I'm a complete newb to Linux. I recently did a clean install of 10.10 to an old box I had so I could mess around with it and learn.  However, all audio (and videos too) would stutter and play very quickly (a 1 minute YouTube video would play in about 45 seconds).  So I followed the solution found here: [http://ubuntup.blogspot.com/2010/10/1010-maverick-audio-video-stuttering.html](http://ubuntup.blogspot.com/2010/10/1010-maverick-audio-video-stuttering.html).

This fixed the playback problems perfectly, however, I lost the volume control applet in the upper-right of the screen.  Reinstalling to volume control and then adding the "Indicator Applet" back to the panel adds a non-functional volume control icon and an additional mail icon.

I'm afraid to keep poking around to break things further, thanks in advance for your help!

-Peter
Ubuntu 10.10

---

### Post by Yellow Pasque on 2010-11-24
Either install alsamixer and use that or use this PPA: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by PeterOfTheCosmos on 2010-12-01
Thank you very much, that did the trick.

---

