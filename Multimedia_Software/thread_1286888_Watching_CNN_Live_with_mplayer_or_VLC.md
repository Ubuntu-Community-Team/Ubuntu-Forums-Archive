---
title: "Watching CNN Live with mplayer or VLC"
date: 2009-10-09
forum: Multimedia Software
---

### Post by arslano on 2009-10-09
Hello,

I've searched the web about watching the CNN Live stream by using mplayer or VLC, but I couldn't solve my problem.

**I use Ubuntu 9.04 AMD-64**

-When I try this link with VLC (Media>Open Network):

[http://www](http://www).*cnn*.com/video/*live*/cnnlive_1.asx

VLC returns me this error:

[COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary'. Check the log for details.[/COLOR]


-When I try mplayer on terminal:


*mplayer* -playlist [http://www](http://www).*cnn*.com/video/*live*/cnnlive_1.asx


The codes on the Terminal are:


[COLOR=#000000]MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET6...
Couldn't resolve name for AF_INET6: [www.cnn.com]("http://www.cnn.com")
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET...
Connecting to server [www.cnn.com]("http://www.cnn.com")[157.166.224.25]: 80...
STREAM_ASF, URL: [http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET6...
Couldn't resolve name for AF_INET6: [www.cnn.com]("http://www.cnn.com")
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET...
Connecting to server [www.cnn.com]("http://www.cnn.com")[157.166.255.18]: 80...
size_confirm mismatch!: 30835 28271
Error while parsing chunk header
Failed, exiting.
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET6...
Couldn't resolve name for AF_INET6: [www.cnn.com]("http://www.cnn.com")
Resolving [www.cnn.com]("http://www.cnn.com") for AF_INET...
Connecting to server [www.cnn.com]("http://www.cnn.com")[157.166.226.26]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364.
STREAM_ASF, URL: mms://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.94]: 1755...
Connected
read error:: Resource temporarily unavailable
pre-header read failed
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.94]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.102]: 80...
Cache size set to 320 KBytes
Cache fill:  0.06% (196 bytes)   


Playing [http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364](http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364).
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.102]: 80...
STREAM_ASF, URL: [http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364](http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364)
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.102]: 80...
read: Resource temporarily unavailable
Failed, exiting.
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a466.l3760651364.c37606.g.lm.akamaistream.net
Resolving a466.l3760651364.c37606.g.lm.akamaistream.net for AF_INET...
Connecting to server a466.l3760651364.c37606.g.lm.akamaistream.net[209.18.41.94]: 80...
Cache size set to 320 KBytes
Cache fill:  0.06% (195 bytes)   


Playing [http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary](http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary).
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: cnn-cnnlive-1-primary.wm.llnwd.net
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET...
Couldn't resolve name for AF_INET: cnn-cnnlive-1-primary.wm.llnwd.net
STREAM_ASF, URL: [http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary](http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary)
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: cnn-cnnlive-1-primary.wm.llnwd.net
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET...
Couldn't resolve name for AF_INET: cnn-cnnlive-1-primary.wm.llnwd.net
Failed, exiting.
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: cnn-cnnlive-1-primary.wm.llnwd.net
Resolving cnn-cnnlive-1-primary.wm.llnwd.net for AF_INET...
Couldn't resolve name for AF_INET: cnn-cnnlive-1-primary.wm.llnwd.net
No stream found to handle url [http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary](http://cnn-cnnlive-1-primary.wm.llnwd.net/cnn_cnnlive_1_primary)


Exiting... (End of file)
[/COLOR]


[COLOR=#000000]So what's the problem? Can you please assist me?[/COLOR]


[COLOR=#000000]Thanks[/COLOR]


[COLOR=#000000]Onur
[/COLOR]

---

### Post by arslano on 2009-10-09
any suggestions?

---

