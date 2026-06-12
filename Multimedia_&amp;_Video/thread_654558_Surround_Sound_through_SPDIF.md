---
title: "Surround Sound through S/PDIF"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by skela on 2007-12-31
Does anybody know how to get the surround sound working through the S/PDIF?
I'm only managing to get Stereo, even when playing files that I know have more than 1 audio channel.

---

### Post by karoliina on 2007-12-31
Hi,

We have managed so far to do this only with xine. There are several settings that had to be changed (under advanced options, there was some checkbox for passthrough, and then on some other page the built-in decoder had to be somehow disabled). Currently it does not work, so I can't go and check the setup. It might work also with mplayer with a command line full of parameters. To my understanding, by default, AC-3/DTS passthrough does not work on Linux like it works on other (proprietary) operating systems, but requires lots of tweaking to get it working, but it can be done. Our HTPC is running Ubuntu and it is connected to Yamaha DSP-A1 which does the decoding (usually) except currently since we haven't setted up it with the latest (re)installation working correctly. With the non-customizable players like totem etc. it might prove to be very hard thing to do, I think you might have best luck with the basic xine. Good luck.

Maybe someone else has more concrete set of parameters at hand for mplayer or some other player? The command line for mplayer would be brilliant as I am nowadays using mainly mplayer.

Best Wishes,
Karoliina

---

