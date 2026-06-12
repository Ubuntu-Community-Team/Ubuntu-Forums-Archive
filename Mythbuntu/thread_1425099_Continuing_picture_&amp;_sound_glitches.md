---
title: "Continuing picture &amp; sound glitches"
date: 2010-03-08
forum: Mythbuntu
---

### Post by tonycollinet on 2010-03-08
EDIT:
Mythbuntu 9.10
Haupauge Nova TD 500
3GHz processor 
2GB ram

Recordings are continuing to have frequent picture glitches, and in the worst case, sound glitches.

It seems to be fragmentation related (or at least free space related, since if I delete a load of stuff the symptoms reduce). I have set minimum free space to about 20GB, and as the free space reduces, the glitching gets worse. I have also set a cron job to defragment files overnight - but I suspect the problem is (at least partly) fragmentation of the free space - which cannot be defragmented.

I've now just upped the min free space to 100GB which should help.

Does anyone have any suggestions on how to properly cure this? Someone else I know has suggested it should be possible to increase the size of a memory based buffer to hold the stream prior to writing to disk - but I can't find any way of doing this.

Cheers.

---

### Post by tonycollinet on 2010-03-08
Here is some mythbackend log (simultaneous playback and recording going on)


> 2010-03-08 21:15:39.245 [mpeg2video @ 0x65e86c0]ac-tex damaged at 0 10
2010-03-08 21:15:43.031 [mpeg2video @ 0x65e86c0]mb incr damaged
2010-03-08 21:15:48.514 [mpeg2video @ 0x65e86c0]00 motion_type at 34 22
2010-03-08 21:15:59.364 [mpeg2video @ 0x65e86c0]ac-tex damaged at 14 10
2010-03-08 21:16:00.770 [mpeg2video @ 0x65e86c0]00 motion_type at 8 30
2010-03-08 21:16:02.314 [mpeg2video @ 0x65e86c0]ac-tex damaged at 10 28
2010-03-08 21:17:05.530 MainServer::ANN Monitor
2010-03-08 21:17:05.536 adding: myth as a client (events: 0)
2010-03-08 21:17:22.365 [mpeg2video @ 0x65e86c0]invalid mb type in B Frame at 32 33
2010-03-08 21:18:51.160 AutoExpire: CalcParams(): Max required Free Space: 102.0 GB w/freq: 5 min
2010-03-08 21:20:08.423 [mpeg2video @ 0x65e86c0]00 motion_type at 29 16
2010-03-08 21:20:59.737 [mpeg2video @ 0x65e86c0]slice mismatch
2010-03-08 21:21:05.108 Reschedule requested for id -1.
2010-03-08 21:21:11.098 Scheduled 134 items in 5.9 = 0.90 match + 5.01 place
2010-03-08 21:22:05.911 [mpeg2video @ 0x65e86c0]invalid cbp at 43 15
2010-03-08 21:22:32.457 [mpeg2video @ 0x65e86c0]00 motion_type at 35 25
2010-03-08 21:22:44.339 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-03-08 21:22:44.346 UPnpMedia: BuildMediaMap Done. Found 1 objects
2010-03-08 21:22:45.127 [mpeg2video @ 0x65e86c0]ac-tex damaged at 38 18
2010-03-08 21:22:56.567 [mpeg2video @ 0x65e86c0]ac-tex damaged at 18 19
2010-03-08 21:23:42.333 [mpeg2video @ 0x65e86c0]00 motion_type at 33 23
2010-03-08 21:23:51.310 AutoExpire: CalcParams(): Max required Free Space: 102.0 GB w/freq: 5 min
2010-03-08 21:24:06.188 [mpeg2video @ 0x65e86c0]ac-tex damaged at 2 13
2010-03-08 21:24:16.052 [mpeg2video @ 0x65e86c0]ac-tex damaged at 31 26
2010-03-08 21:24:35.651 [mpeg2video @ 0x65e86c0]ac-tex damaged at 1 0
2010-03-08 21:24:38.588 [mpeg2video @ 0x65e86c0]ac-tex damaged at 28 5
2010-03-08 21:24:45.708 [mpeg2video @ 0x65e86c0]slice mismatch
2010-03-08 21:24:50.328 [mpeg2video @ 0x65e86c0]mb incr damaged
2010-03-08 21:25:08.381 [mpeg2video @ 0x65e86c0]slice mismatch
2010-03-08 21:25:18.012 [mpeg2video @ 0x65e86c0]slice mismatch
2010-03-08 21:25:37.727 [mpeg2video @ 0x65e86c0]ac-tex damaged at 21 29
2010-03-08 21:25:51.648 [mpeg2video @ 0x65e86c0]00 motion_type at 21 29


---

### Post by tonycollinet on 2010-03-08
OK

It seems to be nothing to do with disk access, fragmenetation or anything else, and everything to do with signal strength on just one of the two tuners.

Ho hum. Now to check all the aerial wiring.

---

### Post by My Name on 2010-03-09
There is an option/switch on the nova-t card which is called LNA (low noise amplifier). it is a software switch that requires you build an options file.
this link is not directly about the switch but may help you.

[http://ubuntuforums.org/showthread.php?t=1311795]("http://ubuntuforums.org/showthread.php?t=1311795")

---

### Post by Chris Musampa on 2010-03-09
> **tonycollinet said:**
> OK

It seems to be nothing to do with disk access, fragmenetation or anything else, and everything to do with signal strength on just one of the two tuners.

Ho hum. Now to check all the aerial wiring.

Are these glitches a picture disturbance accomnpanied by a breif high pitched squeak (bloody annoying!) by any chance?  I get them sometimes if the whether is bad, it sometimes gets worse if both tuners happen to be tuned to the same multiplex.

@My Name - I did some testing a while back and am pretty sure the LNA option has no effect on the TD500.

---

