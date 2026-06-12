---
title: "DLNA/UPNP to stream of RECORDED TV  TRANSCODED and streamed to android tablet...anyon"
date: 2012-12-16
forum: Multimedia Software
---

### Post by tigerstripedcat on 2012-12-16
BASIC QUESTION: describe your setup if you have something like this working

GOAL: I'd like to take RECORDED TV shows (not live) and stream then (over wifi, from linux) to an an android tablet (tablet, not laptop, not raspberry pi, android tablet) so I can take it into the kitchen, velcro it to the cabinet while I cook.  

SO FAR:
* I have tvheadend installed and it can record and playback fine with XBMC frontend.  File is saved as matroska  container (mpeg2, AC3 audio)
* When I try and play files directly over tablet (smb, no nfs broswer that I know) they are pretty choppy, but then again it is 1080p video. (Does anyone out there have 1080p streaming to their tablets/phones? (I can do wifi to a raspberry pi, but not the tablets --too choppy).
* To counteract the high bandwidth of these 6gig+ files I'd like to transcode these files on the fly and send the downsample the videos to send off to the tablet

I'VE TRIED:

* mediatomb -- almost seemed to work but getting transcoding working right is a royal pain because the documentation is horrible
* seriivo -- again bad docs, couldn't even get any of the files to play with transcoding on or off
* universalmediaserver --  as far as I can tell this is not a dlna server proper as windows doesn't recognize it the same way it does the otehr servers
* minidlna -- no transcoding, there is a transcoding branch but the docs are nonexistent

TESTED FROM
* windows native dlna browsing
* foobar w/ plugin -- such a pain to get working so gave up
* xbmc -- could never see files on seriivo even though windows could
* android apps: Mediahouse, diceplayer, 

Any suggestions you can provide would be very helpful

Thanks!

---

