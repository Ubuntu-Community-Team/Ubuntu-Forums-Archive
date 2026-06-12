---
title: "Recording a stream"
date: 2011-04-21
forum: Multimedia Software
---

### Post by primetime34 on 2011-04-21
There is a stream that plays on this link
[http://www.seeon.tv/view/11073/](http://www.seeon.tv/view/11073/)
that I would like to set a schedule to record it at a certain time everyday.  I know how to use cron, but I have no idea what the stream address or how to write the script.  Any help?  Thanks.

---

### Post by primetime34 on 2011-04-22
Any help?

---

### Post by primetime34 on 2011-04-24
Maybe the 3rd time is the charm. :D

---

### Post by primetime34 on 2011-04-29
Okay I think I can figure out what the stream address is...anybody willing to help with this though, as far as creating a script that will record it on a scheduled basis?

---

### Post by primetime34 on 2011-05-04
Any help with this?

---

### Post by primetime34 on 2011-05-05
This is the stream address:

rtmp://live0.seeon.tv/edge/nvcrd4lz4zs0w34

Any help on writing some script that can record this stream?  Thanks.

---

### Post by ron999 on 2011-05-05
Hi

I can download that stream on a Windows machine using "**StreamTransport**".
See attachment.


With Linux, I've tried to download it with rtmpsrv and **RTMPDump**.

But it gives me an error:-

```
ERROR: rtmp server sent error

ERROR: rtmp server requested close
```

Perhaps these people at the other forum will help you find a suitable command for RTMPDump.
Here:- [http://stream-recorder.com/forum/rtmpdump-f54.html]("http://stream-recorder.com/forum/rtmpdump-f54.html")

---

### Post by primetime34 on 2011-05-06
Here is the command needed to record this stream, but I still don't know how to write a script that I can have run everyday at a certain time.  If I had the script, I know how to use cron:

rtmpdump -r "rtmp://live1.seeon.tv/edge/nvcrd4lz4zs0w34" -p "http://www.seeon.tv/view/11073" -W "http://www.seeon.tv/jwplayer/player.swf" --stop 60 --live -o ~Test.flv

I'd like the file name to be saved in my Videos folder and have a dynamic filename based on the day it was recorded.  Any help will be greatly appreciated!

---

### Post by primetime34 on 2011-05-07
FWIW, this is the script I came up with (with help from another forum)

> #! /bin/bash
FileName=$(date +"RedEye-%0m-%0d-%0y-%0k-%0M-%0S.flv")
rtmpdump -r rtmp://live1.seeon.tv/edge/nvcrd4lz4zs0w34 -p [http://www.seeon.tv/view/11073](http://www.seeon.tv/view/11073) -W [http://www.seeon.tv/jwplayer/player.swf](http://www.seeon.tv/jwplayer/player.swf) --stop 3600 --live -o $FileName 

seems to work fine. :D

---

