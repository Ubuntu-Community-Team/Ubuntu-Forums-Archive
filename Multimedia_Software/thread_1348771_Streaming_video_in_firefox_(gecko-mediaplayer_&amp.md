---
title: "Streaming video in firefox (gecko-mediaplayer &amp; mplayer)"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Slanter2010 on 2009-12-07
I'm trying to watch some streaming video (found [here]("http://www1.cop15.meta-fusion.com/kongresse/cop15/templ/play.php?id_kongressmain=1&theme=cop15&id_kongresssession=2281")) but have been unable to get it to play. The mplayer embedded ui shows up, but it won't play the video (screen remains black). MIME type is application/x-ms-wmp if that helps. I'm using the gecko-mediaplayer plugin, firefox 3.5 and Ubuntu 9.10.

If there is a better app for streaming windows media I'd be more than willing to try that too. 

Thanks for your time!

---

### Post by xc3RnbFO8P on 2009-12-07
Try to open this in Vlc:
[mms://a1737.v2879c.c2879.g.vm.akamaistream.net/7/1737/2879/001/gff.download.akamai.com/2879/meta/091207_1000_cop15_p1_enc09_floor.wmv?obj=001&WMStartupProfile=0]("mms://a1737.v2879c.c2879.g.vm.akamaistream.net/7/1737/2879/001/gff.download.akamai.com/2879/meta/091207_1000_cop15_p1_enc09_floor.wmv?obj=001&WMStartupProfile=0")
I am having problem playing it in Firefox, works fine in Vlc.

---

### Post by Slanter2010 on 2009-12-07
That works great, I'm just having one problem - when I try to get the url from other streams they're all missing the "mms://a1737" (or whatever that feed is) and I just end up with the rest of it. Any idea why that might be? I'm getting the url via right click -> copy location.

EDIT: Now I can't seem to even get that much... is there another way of grabbing that url? (Couldn't find it or anything similar in source :()

---

### Post by xc3RnbFO8P on 2009-12-07
> when I try to get the url from other streams they're all missing the "mms://a1737" (or whatever that feed is) and I just end up with the rest of it
I need a link.

---

### Post by Slanter2010 on 2009-12-07
All of the streams I'm looking at are on the COP15 website, but I'm unable to view any of them in VLC because I can't retrieve a complete url from the feeds (the one with the mms protocol). I just need a way to grab the stream urls so that I can open them in VLC.

---

