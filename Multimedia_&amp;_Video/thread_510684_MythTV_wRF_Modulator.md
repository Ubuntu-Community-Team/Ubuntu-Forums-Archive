---
title: "MythTV w/RF Modulator"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by KoRnholio on 2007-07-26
Hi, I"ve installed MythTV to use my Hauppauge HVR 950.  I'm using it to capture video from a Playstation 2, so I'm using an RF modulator to feed into the Coaxial input on the 950.  This setup works somewhat, at least on xawtv (tvtime won't even start, because I have an ATI card).  But the problem is, I'm trying to use it with MythTV - xawtv's interface is terrible, and it can't even record video right.

MythTV installs fine from the repos, and it detects my card.  I set it up as follows:

Capture Cards: Just as described in the oft-linked [http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html) guide (as a DVB DTV capture card). I left everything else in there as the default.

Video Sources:  I just created a new video source with no listings grabber.  Set to us-bcast (that's the setting that works in xawtv).

Input Connections:  I set the DVB input to that video source I created, and defaulting to channel 3.  It also created a V4L listing, and I set the televison one to default to channel 3 as well.

Channel Editor:  My RF modulator outputs on channel 3, so I've added a channel 3 to the backend.  I assigned it to the video source I created.

But, I get no output.  Attached is the output of both the mythfrontend and backend processes.

I'm using a Radeon 9550, with the fglrx drivers, if that means anything.  They've been working beautifully.  I'm using Feisty, by the way.  I'm also trying out Mythbuntu to see if that works any better, but I'm hoping to get this to work on my regular Feisty install.

---

