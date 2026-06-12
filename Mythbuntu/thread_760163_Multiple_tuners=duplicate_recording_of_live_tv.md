---
title: "Multiple tuners=duplicate recording of live tv"
date: 2008-04-19
forum: Mythbuntu
---

### Post by Afkpuz on 2008-04-19
Ok, so I've installed 2 PChdTV 5500s in my mythbox and they work great.  I can record 2 different shows at a time.  Here's the problem though: when I watch live tv and nothing is recording, both tuners record the live tv.  So, I'm getting alot of duplicates in my recordings section.  How can I stop this?

Oh and I'm running mythtv 20.2.

Somehow though, if I tell it to record that live show, I can press escape, re-enter live tv using the other tuner and change channels normally.  Please help save my hard drive space!

---

### Post by oscarsfriend on 2008-04-20
Are you **sure** the extra recording is a duplicate?  [EDIT: And are you sure it doesn't expire after a short while?]  I've seen reports of this before in mythtv 20.2, where when viewing live tv it makes a recording and also creates an empty entry with the same name, time, etc. as the actual recording, but it won't play.  I don't think this has anything to do with multiple tuners.  I get the same problem, but I almost never watch live tv so it doesn't bother me.  I'm not aware of any fix for this (short of upgrading to 0.21, and I don't know for sure that this would fix it).

EDIT: I just watched a few seconds of live tv, and it created the following files:

```

-rw-r--r-- 1 mythtv mythtv    0 2008-04-20 10:51 /mythtv/recordings/1013_20080420105152.mpg
-rw-r--r-- 1 mythtv mythtv 4.4M 2008-04-20 10:52 /mythtv/recordings/1013_20080420105153.mpg

```

EDIT#2: OK, so I just tried the same thing, this time I watched live tv for about five minutes.  I only get one entry listed under watched recordings, as it appears the duplicate was expired after a short while.  Here are my log entries:
```

$ tail /var/log/mythtv/mythbackend.log
2008-04-20 11:03:19.099 MainServer::HandleAnnounce Playback
2008-04-20 11:03:19.100 adding: plato as a client (events: 0)
2008-04-20 11:03:19.105 TVRec(6): Changing from None to WatchingLiveTV
2008-04-20 11:03:19.110 TVRec(6): HW Tuner: 6->6
2008-04-20 11:03:21.215 Finished recording T4:Hollyoaks Omnibus: channel 1013
2008-04-20 11:03:21.287 Finished recording T4:Hollyoaks Omnibus: channel 1013
2008-04-20 11:03:21.304 Preview Error: Previewer file '/var/lib/mythtv/recordings/1013_20080420110319.mpg' is not valid.
2008-04-20 11:04:00.037 [COLOR="Red"]Expiring T4:Hollyoaks Omnibus from Sun Apr 20 10:25:00 2008, 0 MBytes, forced expire (LiveTV recording)[/COLOR]
2008-04-20 11:08:00.340 TVRec(6): Changing from WatchingLiveTV to None
2008-04-20 11:08:00.679 Finished recording T4:Hollyoaks Omnibus: channel 1013

```

---

### Post by Afkpuz on 2008-04-20
Interesting.  The times that I noticed this were when I watched only a few seconds of live tv.  Either way, I'll be upgrading my media center to hardy when it officially gets released, which means new version of mythtv!  thanks for the input.

---

