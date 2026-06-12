---
title: "iwlagn hogs cpu and fails connection"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by mr.fudo on 2009-02-14
Hi,

I wrote almost one week ago [_here_]("http://ubuntuforums.org/showthread.php?p=6676382") about a "slowdown" problem with my laptop. I'm working with Ubuntu 8.10 Intrepid Ibex.
I have found out that the slowdown is caused by iwlagn, while it is trying to estabilish a connection. The computer works fine if the wlan (Intel 5100) is switched off or disconnected. When I try to connect to my home network usually iwlagn starts consuming all the available cpu power... and eventually fails to connect. To gain control of the laptop I can:
- physically switch off the wifi module,
- open a terminal and 'rmmod' iwlagn
- or wait for the screen requesting for a wep key (which is already set) and cancel the connection.
Any of these work, and I can then retry again (turning on the wlan switch or modprobing iwlagn) hoping for the best...which usually is not the case.

Sometimes I'm lucky and it connects immediately, but much more often I have to keep trying for a while before succeeding.
I've noticed that restarting the notebook usually works better than following this procedure: do you think there might be some hidden problem or conflict that I'm not aware of, which causes the strange iwlagn behavior? Any idea about how I could find that out? It'd be great if there was a solution for all this, but a workaround would do the trick too... it's annoying to spend so much time (almost one hour this morning) just to connect to the internet.

I've spent the last week trying to fix this, and I'm really desperate. 
Any help?

---

