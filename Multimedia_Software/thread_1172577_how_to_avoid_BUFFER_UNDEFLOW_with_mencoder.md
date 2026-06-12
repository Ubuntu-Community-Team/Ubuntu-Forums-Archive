---
title: "how to avoid BUFFER UNDEFLOW with mencoder"
date: 2009-05-28
forum: Multimedia Software
---

### Post by marco.pallotta on 2009-05-28
I use Acidrip to rip my dvd into mpeg format. The command that acidrip uses is to do this is:
AcidRip message - Running mencoder dvd://2 -dvd-device /dev/dvd -chapter 10-10 -alang English -info srcform="DVD ripped by acidrip.sf.net" -oac copy -ovc lavc -lavcopts vcodec=mpeg1video:vbitrate=5000:vpass=1 -vf pp=de -of mpeg -o "/dev/null"

The problem is that in the debug window I can see a lot of these messages:
ERROR: scr 0.959, dts 0.000, pts 0.624
BUFFER UNDEFLOW at stream 1, raising muxrate to 3858 kb/s, delta_scr: 114649

At the end some movies are ok but some others not.

Have somebody any idea to correct this?

---

