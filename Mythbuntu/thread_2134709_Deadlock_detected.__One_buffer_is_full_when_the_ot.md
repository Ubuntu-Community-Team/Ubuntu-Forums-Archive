---
title: "Deadlock detected.  One buffer is full when the other is empty!  Aborting"
date: 2013-04-12
forum: Mythbuntu
---

### Post by davekoenig on 2013-04-12
I simply want to delete the Commercials from my videos, I look at them on Mythweb, it shows commercials flagged, I go into Frontend and shows cutlist, but after figuring out how to get transcode to work, no commercials are GONE!


I am using MythTV 0.26, this is very frustrating because out of the box the program does not Transcode!!!!   You need to set option from default to MPEG4, it then creates a NUV file!  What the hell is a NUV File????  When I change to lossless I get:

Deadlock detected.  One buffer is full when the other is empty!  Aborting

how does this stuff ever work!!!

---

### Post by klc5555 on 2013-04-12
This has been an occasional issue in mythtranscode for a long time. The bugtrack for it has been open since about 2007.

However, in mythtv 0.26, it seems to have ceased being an occasional issue and appears to happen with almost all lossless transcoding of DVB. There is no good solution --the devs over at the mythtv list seem suffiently frustrated by it as to be as likely to rip mythtranscode out of mythtv entirely as to solve the issue.

From a practical standpoint, there are a limited number of workarounds. First is to use mythtranscode from 0.25, in which version the deadlock problem remains an occasional issue. Folks have done this either by simply running mythtv 0.25, or some intrepid souls have taken the source code for mythtranscode 0.25, recompiled it for mythtv 0.26 and installed it over the top of  mythtranscode 0.26, which has sometimes been successful. "mythtranscode" and "deadlock" can be searched over at the mythtv list on gossamer threads, and will yield a vast number of hits, but one representative exchange is here: [http://www.gossamer-threads.com/lists/mythtv/users/539608?search_string=mythtranscode%20deadlock;#539608](http://www.gossamer-threads.com/lists/mythtv/users/539608?search_string=mythtranscode%20deadlock;#539608)

When you have a recording where mythtranscode bombs with the deadlock error, about the only reliable way to handle it is to cut and save the recording manually with an external video editor of some sort. The one procedure almost guaranteed **not** to work is the remuxing procedure described in the mythtranscode wiki page: [http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode) 

On 0.24 and 0.25, I tend to have about 1 lossless transcode of DVB out of every 10 fail with the deadlock error. For these recordings, I use avidemux as my external editor to cut and save the recordings (as .ps files).  It appears that avidemux 2.5.x does not cut and save HD recordings properly, but versions 2.6.1 and above seem to do a very good job with all recordings. But that's my preference --you and others may have other video editors you prefer to use in situations of this sort.

---

### Post by BicyclerBoy on 2013-04-16
Recent posts on mythtv mailing lists strongly suggest this has been fixed & by a disgruntled user. There was a hiccup with a recent ffmpeg resync.

[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=214298;page=2;sb=post_latest_reply;so=ASC;mh=25;list=mythtv](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=214298;page=2;sb=post_latest_reply;so=ASC;mh=25;list=mythtv)

One of the mythbuntu devs has setup a ppa
[https://launchpad.net/~dekarl/+archive/mythtv-transcode-ac3](https://launchpad.net/~dekarl/+archive/mythtv-transcode-ac3)

note that mythtranscode only supports lossless H264 via pipe to external program like ffmpeg.

There are a couple of cutting scripts around.
One is as fast as file copy & uses myth cutlist editor/seektable, frame accurate & can cut any file.
Not tested it with commflagged recordings.

---

### Post by splg on 2013-05-24
Sorry to dig up an old post but I'm having a problem with mythtranscode on .26 too. I thought I had the fix by following [http://www.gossamer-threads.com/lists/mythtv/users/539697#539697](http://www.gossamer-threads.com/lists/mythtv/users/539697#539697). I copied the precise-update libs and binary to /usr/lib and /usr/bin however mythtranscode still fails when I try to run it via mythweb. 

```
May 24 07:29:27 localhost mythlogserver: mythbackend[1662]: C ProcessRequest mainserver.cpp:1294 (HandleVersion) MainServer::HandleVersion - Client speaks protocol version 72 but we speak 75!
May 24 07:29:27 localhost mythlogserver: mythbackend[1662]: W ProcessRequest mainserver.cpp:5841 (connectionClosed) MainServer: Unknown socket closing MythSocket

```

The above error repeats a few times and then the job fails. I'm sorry if I missed something above but is there something I missed when moving this over? I checked with ldd /usr/bin/mythtranscode and there is nothing that shows "not found".

Thanks

---

