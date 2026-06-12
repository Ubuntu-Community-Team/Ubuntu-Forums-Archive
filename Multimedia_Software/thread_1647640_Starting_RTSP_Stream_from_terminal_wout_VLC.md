---
title: "Starting RTSP Stream from terminal w/out VLC"
date: 2010-12-17
forum: Multimedia Software
---

### Post by b0ot on 2010-12-17
I have been doing a lot of video streaming lately, and I have had a lot of issues with lag when using vlc. Basically I take in an RTSP video stream from a axis encoder and restream it out across my network using rtp. This ends up resulting in about a 4 second lag from my live video to my remote end viewing.

What I would like to do now is initiate an RTSP request to a *specific* port than at the ip level redirect the video traffic out to specific ip(s)/port(s). I have been able to redirect the video stream of an rtp video stream from vlc but not an rtsp stream... it seems to crash vlc.


(All without VLC)
Is there a way to request an rtsp stream from terminal (so I could use it in a bash script)?

---

