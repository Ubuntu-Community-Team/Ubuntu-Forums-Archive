---
title: "Closed caption issues, but only on some channels / programs"
date: 2013-06-09
forum: Mythbuntu
---

### Post by amblinn on 2013-06-09
I'm pretty much a newbie at Linux, but I'm getting really close to having my MythTV working the way I'd like it without having had to reach out for help...until now.  The system is a dedicated combined front-end/back-end System76 Meerkat Ion Nettop (2-core Atom processor, 2 GB RAM, Zotac Ion, and there are probably more important details I'm leaving out here).  Tuner is a HDHR Prime, with CableCARD.  Provider is Comcast Bay Area.  Upgraded to Ubuntu 12.04, Myth 0.25, no special patches (not like I'd know how to apply them, anyway).

I like to watch television shows with the closed captioning on (helps with mumbled dialog, not having to rewind when DH decides to run the garbage disposal, etc).  However, on some of the lower-numbered channels (FOX, NBC, CBS, etc), closed-captioning is usually either garbled or doesn't appear at all during primetime television.  Closed captioning on cable channels (e.g. SyFy, USA, TNT, FX) is fine.

I've tried all of the different video playback modes; it doesn't seem to make a difference.  Looking at the logs, it appears like there might be some sort of frame or field synchronization problem; I get a lot of "XDS: failed CRC" messages.  There also seem to be a fair number of messages about progressive and interlaced video (video stream seems to be swapping formats pretty frequently).  

Output of "mythfrontend -v playback,vbi" on a couple of problematic programs can be found at:
 [https://docs.google.com/file/d/0B7eHpEzSxHspcFFSX193R01oR1U/edit?usp=sharing](https://docs.google.com/file/d/0B7eHpEzSxHspcFFSX193R01oR1U/edit?usp=sharing)


Closed captioning is present in the programs; VLC shows the captions (CC1) without a problem.  But, just in case there could be something else in the video, video clip of one of the offending programs (93MB):
[https://docs.google.com/file/d/0B7eHpEzSxHspVVRjM3Y1T0cwYW8/edit?usp=sharing](https://docs.google.com/file/d/0B7eHpEzSxHspVVRjM3Y1T0cwYW8/edit?usp=sharing)


I'm hoping there's just some setting that I need to tweak... any help, tips, insight would be greatly appreciated (or if there's more info I can provide to help with the troubleshooting).

Thanks!
A-M

---

### Post by amblinn on 2013-06-16
OK, so I guess it's not an easy answer then :(.  It would be helpful to me if someone with a little time could download the video clip (from the second link above) to their Video folder (for me, this lives at /var/lib/mythtv/video) and try watching it through the MythTV interface with closed captioning turned on?  (press "T" on the keyboard, until it says CC1 in on).  I'm trying to figure out whether this problem is particular to my setup (maybe not enough RAM?), or may be a proper MythTV misbehavior in how video is decoded.  If you could post your results and a brief description of your setup, that would be great.

Thanks!
A-M

---

