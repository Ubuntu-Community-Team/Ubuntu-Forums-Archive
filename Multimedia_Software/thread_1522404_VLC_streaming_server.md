---
title: "VLC streaming server"
date: 2010-07-02
forum: Multimedia Software
---

### Post by asai on 2010-07-02
Hi,
I have a 8.04 server which I like to use as a streaming server for my Dreambox TV tuner.
Wrote this script:
```
#!/bin/bash

/usr/bin/vlc '/usr/bin/lynx -dump http://root:dreambox@10.10.160.8/video.m3u' :sout='#transcode{acodec=MP3,vcodec=DIV3,ab=32,vb= 128,width=320,height=240,deinterlace,fps=15,channels=2}:std{access=mmsh,mux=asfh,url=:8154}' vlc:quit

```
This script will transcode the stream from the tuner and I should then be able to connect to the stream from Internet or mobile phone.
However, the script stops with this error:
```
[00000293] main input error: no suitable access module for `/usr/bin/lynx -dump http://root:dreambox@10.10.160.8/video.m3u'
status change: ( stop state: 0 )
```
Any suggestions on this error?

---

### Post by asai on 2010-07-07
I have changed the script:
```
vlc -vvv http://root:dreambox@10.10.160.8/video.m3u --sout '#transcode{vcodec=DIV3,vb=128,scale=1,acodec=mp3,ab=32,channels=2}:std{access=mmsh,mux=asfh,dst=:8080}'
```

Edit: It works! But it laggs.
Any suggestions?

---

### Post by asai on 2010-07-07
Changed it again, and tried it on a more powerful machine with Karmic...
Heres the script:
```
#!/bin/sh

cvlc -vvv http://root:dreambox@10.10.160.8/video.m3u --sout "#transcode{vcodec=h264,acodec=mp3,venc=x264{profile=baseline},width=320,vb=256,ab=96}:std{access=mmsh,mux=asfh,dst=:8080}"
```
Picture is fine, but I have no sound.
Any suggestions?

---

### Post by asai on 2010-07-16
An update on this issue:
I have upgraded my server to Lucid and VLC to the newest version, but still have som trouble.
Most of the errors are gone, but I still have som trouble.
I suspect that the server have to slow hardware...

This is the error (warning):
```
[0x8b70e3c] main mux warning: late buffer for mux input (222795958)
[0x8b8e084] stream_out_transcode stream out debug: late picture skipped (5718316)
```
Any suggestions?

---

