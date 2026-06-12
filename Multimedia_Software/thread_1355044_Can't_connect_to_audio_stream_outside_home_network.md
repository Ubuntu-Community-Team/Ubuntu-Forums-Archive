---
title: "Can't connect to audio stream outside home network"
date: 2009-12-14
forum: Multimedia Software
---

### Post by InkyDinky on 2009-12-14
I have mpd setup on a computer at home. Mpd uses port 6600 and httpd uses 6660. I can connect to the http stream on my local network using vlc to connect to  [http://192.168.0.3:6660](http://192.168.0.3:6660).  VLC picks up the stream, buffers, and begins playing. However whenever I try to use my static ip provided via dyndns.org and connect to the mpd http stream, VLC just sits there.  I have both the mpd and httpd ports forwarded on my router.  I can connect and manipulate mpd by using the Music Player Minion plugin for firefox. However I get nothing when I try to connect to the http stream. Am I missing something?  Is there further configuration for the http daemon that needs to be done? port forwarding?

---

