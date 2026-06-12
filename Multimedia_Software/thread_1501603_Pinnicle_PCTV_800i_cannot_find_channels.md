---
title: "Pinnicle PCTV 800i cannot find channels"
date: 2010-06-04
forum: Multimedia Software
---

### Post by akester on 2010-06-04
I am having lots of problems installing this tuner card on this particular system.  It is a Compaq Presario 6000 that I am trying to install mythtv's backend on to act as a dvr.  It is running Ubuntu 9.04, not sure of the Mythtv version (just don't know where to find it).  The tuner card is a pinnacle PCTV 800i (more info at [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i) ]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i")).  I had this installed for about a week in my main desktop, and it worked perfect.  It is running the same version of ubuntu and mythtv.  I figured I would move it over to a dedicated machine that I had just recived becuase I dual boot my desktop.

I tried to replicate the installation on my desktop as close as I could, installing the xc5000 firmware and the v4l-dvb drivers (described in above link) just as I had done on my desktop.  That didn't work so I did some digging and found that ubuntu has its own version of the cx88 and saa7134 drivers (needed by the 800i, and should be installed with the vrl-dvb drivers).  I then removed the drivers according to this [thred post]("http://www.avsforum.com/avs-vb/showthread.php?p=13783029#post13783029").

That got the card to work...kinda.  I was able to record a show and replay it using mythweb.  The frontend never had livetv but cuold schedule recordings and watch recordings... enough for me.  I continued to test recording shows, changing some of the transcode options to be able to export them later.  Eventually the video became static on one of the recordings, so I added the dvb side of the card figuring the dvb tuner must be open and blocking the analouge tuner.  That didn't work so I still have fuzz on every channel of my tuner card.

I know this is a lot of information, but any help would be greatly appreciated.

---

