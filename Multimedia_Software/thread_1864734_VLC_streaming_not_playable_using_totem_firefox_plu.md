---
title: "VLC streaming not playable using totem firefox plug-in"
date: 2011-10-19
forum: Multimedia Software
---

### Post by the_X_files on 2011-10-19
I'm trying to re-stream video from an ip cam and make it playable on Windows (Media Player Plug-in) and on Linux (Totem Plug-in) using cvlc without any luck. I tried all the available muxers and supported codecs. 
My best result is using 
```
cvlc -Idummy http://link/videostream.cgi :sout="#transcode{vcodec=DIV3,vb=250,fps=1,width=640,height=480,acodec=none}:std{access=mmsh,mux=asfh,dst=0.0.0.0:8081}" :no-sout-rtp-sap
```
and it works great on Windows but doesn't work at all on Linux (I guess that it's because of the mms protocol)

It is possible at all to do that using vlc..? Maybe I need some extra codecs?
I'm using Ubuntu Server 11.10 64 bit version.

---

