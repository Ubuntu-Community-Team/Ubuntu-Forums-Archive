---
title: "broken/freeze screen on video"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by lukk-pl on 2008-03-15
Hello, 

I've annoying think on my Ubuntu. I found out it after upgrade from 7.04 to 7.10, but it also exist on clear 7.10 install. 
In some  (random) time while I'm working on my laptop the video screen is getting broken and look like on this screenshot:
[Broken screen on video]("http://www.wrzuta.pl/obraz/nPwMNNGjTu/") . 
The problem don't depending on Video player (Totem (GS), VLC, SMPlayer) or the engine (Xine, GStreamer).
Only way to get video working is to restart X server, but sometimes it cause system not response.

I was found out in system log entry like this when it's come 
```
Mar 11 15:27:39 vault13 kernel: [55604.104000] NVRM: Xid (0001:00): 6, PE0000 0428 ffefedea 00002e38 00000000 00dababa
Mar 11 15:27:39 vault13 kernel: [55604.120000] NVRM: Xid (0001:00): 30,  L1 -> L0
```
but any solution about Xid problems do not work for me. 
I also try reconfigure xserver-xorg on different ways, but it turn only display settings to 'nv' drivers. 

One more thing - I'm using Compiz Fusion, but the problem returns also when I turn CF off. 

I've (mobile) GeForce 7600 Go (nvidia-glx-new 100.14.19+2.6.22.4-14.10).
Any idea?

PS I'm sorry for my English.

---

### Post by lukk-pl on 2008-03-20
I found one more immediate solution - switch to any tty and go back is sufficient.

---

