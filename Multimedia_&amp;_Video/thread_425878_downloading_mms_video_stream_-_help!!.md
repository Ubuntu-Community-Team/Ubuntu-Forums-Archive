---
title: "downloading mms: video stream - help!!"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by spykecub on 2007-04-28
I've been trying to download a video from dr.dk

On this page: [http://www.dr.dk/Melodigrandprix/forside.htm](http://www.dr.dk/Melodigrandprix/forside.htm)
The link called: "Før melodi grand prix - 2. del (58:03)" (it's a javascript, which is why I'm not posting a direct link...)

First of all I should mention that I can't even get the thing to PLAY in my kubuntu feisty installation (I've tried it on windoze, works fine). I've tried mplayer, kaffeine, vlc... anything that can play video

In any case, I'd like to download the stream. Found the link to be ```
mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR1/2007/04/fefe709e-c29a-432a-8622-46990decc7b3/F%c3%b8r%20melodi%20grand%20prix20070420.wmv
```

I first tried mplayer dumpstream. That gave me:
M```
Player 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 3000+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR1/2007/04/fefe709e-c29a-432a-8622-46990decc7b3/F%c3%b8r%20melodi%20grand%20prix20070420.wmv.
STREAM_ASF, URL: mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR1/2007/04/fefe709e-c29a-432a-8622-46990decc7b3/F%c3%b8r%20melodi%20grand%20prix20070420.wmv
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Cache size set to 320 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
```

mimms gives memimms ```
mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR1/2007/04/fefe709e-c29a-432a-8622-46990decc7b3/F%c3%b8r%20melodi%20grand%20prix20070420.wmv
<mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR1/2007/04/fefe709e-c29a-432a-8622-46990decc7b3/F%c3%b8r%20melodi%20grand%20prix20070420.wmv>  =>  'F%c3%b8r%20melodi%20grand%20prix20070420.wmv'
Connecting...Could not read packet header: Success
libmms connection error
```

and I'm about to begin pulling my hair out trying to get this stream.


Anyone wanna help me out? :)

---

### Post by musicinmybrain on 2007-04-28
Did you see this? ```
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Server returned 404:Not Found
```
I'm not sure that URL is right after all.

Edit: Hmm, I got the same URL from the site. Puzzling. And it works on Windows.

---

### Post by spykecub on 2007-04-28
> **musicinmybrain said:**
> 
Edit: Hmm, I got the same URL from the site. Puzzling. And it works on Windows.

told ya ;)

---

