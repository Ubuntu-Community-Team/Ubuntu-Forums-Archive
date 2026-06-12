---
title: "Stream media over http"
date: 2013-06-18
forum: Multimedia Software
---

### Post by fnedrik on 2013-06-18
Is there a media center that can stream the videos on my media server over http? I currently use xbmc for my media box needs, but I would like something (perhaps an xbmx plugin?) that allows me to connect to the server with a browser and watch streaming media over my local network. I don't want to install mythTV clients on them or anything.

---

### Post by TheFu on 2013-06-18
HTTP is not designed as a video streaming solution. It is a cludge and barely works - just look at all the youtube and other video buffering issues.

DLNA, Samba, NFS would be the best methods to present videos to other devices that I am aware.  I've tried miniDLNA, [http://twonky.com/](http://twonky.com/), [http://www.ps3mediaserver.org/](http://www.ps3mediaserver.org/),  and a few other DLNA capable servers - all had issues.  I've ended up with both NFS and Samba as network file servers for HiDef videos.  These work great for wired connections, not so great for wifi.  WiFi does not usually present consistent bandwidth, so it suffers from the same issues that HTTP over the internet suffers.  A client that buffers will be necessary.  WIfi is fine for photos and audio, just not video.  At least in my experience.

To really be helpful, knowing the specific clients you want to view from and the types of content is needed.  Different clients have different limitations, so if all your content is 1080p h.264/mkv, you can't expect that to playback on an xbox360 or android tablet.  Divx/xvid encodes can cause issues for some clients too - WMV, MOV, and other proprietary video formats cause issues too.

---

### Post by fnedrik on 2013-06-19
Youtube quality would be just fine. It works great over our wifi too. That's what buffering is for. Ideally I would like it to work through a Chrome browser, so that it I could use a Chromebook, an Ubuntu laptop and an Android tablet as clients. I don't expect HD-content to work. At least not without the server scaling down.

---

### Post by TheFu on 2013-06-19
All my attempts to get HTTP-based video streaming have failed due to the complexities involved with the free solutions.  I'm certain you can pay Adobe/Apple (can't remember which) for a very nice solution.  Last year I tried to get their "free" solution working and found they had a streamer, but only for very specific source files. It didn't provide anything except the streamer, so file discovery, website layout were all on me.

Someone with a little time and python/perl/php/ruby skills could probably make that solution work well. I couldn't. Google found these:
* [https://www.adobe.com/products/hds-dynamic-streaming.html](https://www.adobe.com/products/hds-dynamic-streaming.html)
* [https://www.apple.com/quicktime/extending/resources.html](https://www.apple.com/quicktime/extending/resources.html)
* [http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

In the end, it was so much easier to just use NFS and SMB to stream over wired connections for my needs. A had to live with source incompatibilities across a few devices, but XBMC plays almost everything.

I hope you find something I didn't and that it works good.  Best of luck!  Please share your solution.

---

