---
title: "Ubuntu 10:04: mplayer stopped working with RTSP stream"
date: 2010-05-17
forum: Multimedia Software
---

### Post by edantes on 2010-05-17
I just upgraded from Ubuntu 9.10->10.04.  In the new system, mplayer stopped working with some RTSP streams which worked perfectly in my Ubuntu 9.10.  Am I  missing some codec o plugin I used to have? (10.04 was a clean install).  
----
Here is a typical output:

> 
 STREAM_LIVE555, URL: rtsp://a988.v101995.c10199.e.vm.akamaistream.net/7/988/10199/3f97c7e6/ftvigrp.download.akamai.com/10199/cappuccino/production/publication/France_2/Autre/2010/S20/125780_HD_13h_20100517.wmv
Stream not seekable!
 file format detected.
Failed to initiate "audio/X-ASF-PF" RTP subsession: RTP payload format unknown 
or not supported
Failed to initiate "video/X-ASF-PF" RTP subsession: RTP payload format unknown 
or not supported
Failed to initiate "video/X-ASF-PF" RTP subsession: RTP payload format unknown 
or not supported


---

### Post by andrew.46 on 2010-05-17
Hi edantes,

I saw the answer from [MPlayer-users]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-May/080014.html").... what I will admit baffles me a little is that the stream plays with vlc... BTW if you supply 'complete uncut output' to mplayer-users they will expect to see the most recent svn MPlayer compiled against recent Live555 libraries.

Andrew

---

### Post by edantes on 2010-05-18
It turns out the answer from MPlayer-users was correct in the sense that that url (rtsp:) did not run in my old setup either.  What I was doing on a regular base was to record the broadcast stream using an url copied from Firefox.   It was an mms://  from the Mplayer plugin.  

When I switched to Lucid, After the url  was coming from the Movie Player plugin which uses rtsp which mplayer does not support along the ASF content.  

The rtsp url is supported by both vcl and Movie player, but not reliably. At least in my sluggish connection it always get interrupted.

The request from the mplayer folk for the most recent svn seems a bit unrealistic in a users list.  Anyway, I was not expecting the message to be seen as a bug report.  From the reply, it is obvious they are not shooting for a miss congeniality sash, but in all fairness, the reply solved my problem.

---

### Post by mc4man on 2010-05-18
> The rtsp url is supported by both vcl and Movie player, but not reliably..

That's what i see - for the most part I find rtsp to be 50-50 as to if it plays and even then can be pretty crappy.

The biggest diff. here ( with your url and similar ones) is when there are multiple video streams vlc picks the best one, mplayer seems to usually pick the worst one by default.

Ex. 
changing your url to mms both mplayer and vlc play

mplayer
> ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
[asfheader] Video stream found, -vid 3
VIDEO:  [WMV3]  384x216  24bpp  1000.000 fps [COLOR="Blue"] 177.0 kbps[/COLOR] (21.6 kbyte/s)

vlc
> VLC media player 1.0.6 Goldeneye
[0x9ed2d58] access_mms access: selecting stream[0x1] audio (65 kb/s)
[0x9ed2d58] access_mms access: selecting stream[0x2] video ([COLOR="Blue"]381 kb/s)[/COLOR]
[0x9ed2d58] access_mms access: ignoring stream[0x3] video (185 kb/s)


(you can tell mplayer to use the better stream  (-vid 2 ), though have always found it odd about how it picks in the first place

---

