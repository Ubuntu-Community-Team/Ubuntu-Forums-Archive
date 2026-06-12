---
title: "rhythmbox as DAAP client : does not close connections"
date: 2010-02-09
forum: Multimedia Software
---

### Post by raghu1111 on 2010-02-09
This is more of a question for developers of rhythmbox DAAP support.

I am using rhythmbox to remotely access music exported by mt-daapd server. It works fine.

But it does not seem to close connections properly. This problem is very severe when you press "prev" button a few times. 

How to reproduce (this just one way):
=====================================

1) Start playing a few songs (playlist or an album). 
2) press "next" button a few times
3) then press "prev" a few times.

The playback might even pause for many seconds if you are not a LAN.

Now check connections opened by Rhythmbox.. (netstat -n | grep 3689 on client). You will notice a lot of connections, and they stay for a very long time.. multiple hours.

Let me know if anyone needs more info.

Any insight into daap implementation would be useful.. for. e.g. this could be common problem for all streaming.

---

### Post by maedox on 2010-04-15
I'm not sure this is the correct place for this. No one will read it, but I can get rid of some steam at least. :P

I am also having major issues with Rhythmbox. Why must everything with a GUI be so half-assed in the OSS world? I tend to think RB is so badly done that putting it in Ubuntu is insane, but that's another story I guess. (Yes I know it's Gnome software.)

The issue:
When I try to stream from di.fm premium it may or may not work. If the stream stops, there is no way to get it going again. The reason is that Rhythmbox somehow manages to make more than one connection to the di.fm server and therefore is disconnected. There is only one connection allowed from one account. When I hit play again after it stops it keeps going for max one minute before it is disconnected. Then, at random, it does not start playing at all.

I have completely stopped using Rhythmbox for streaming because of this. Totem works like expected so I'll use that instead.


It just hit me that I didn't include any system specs. I'm using Ubuntu 9.10 and have tried the default Rhythmbox (version 0.12.5) and also built 0.12.8 from git source. 0.12.8 is not even marginally better at streaming.

---

