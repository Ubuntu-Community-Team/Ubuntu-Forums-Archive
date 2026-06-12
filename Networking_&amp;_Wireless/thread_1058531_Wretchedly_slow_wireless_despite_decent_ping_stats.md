---
title: "Wretchedly slow wireless despite decent ping stats"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by neanderslob on 2009-02-02
Howdy all,

I'm running 8.04 w/ kde.  I've recently started using nm-applet (the gnome wireless manager) with kde because I rarely get connectivity with Knetwork manager.  Anyway, for some reason my Internet connection is so slow on this machine that I can't even listen to Pandora or watch youtube videos.  I decided to see (quantitatively) just how slow my connection was and my ping summary yielded surprisingly reasonable results (given below).  My processor is fine and all internal processes are quite speedy.  Any ideas as to what else I should check in order to diagnose it?  If it's significant, there was mild damage done to my wireless card (sort of bent it while I was moving) but since the ping stats are reasonable I figured this doesn't have any sort of bearing.  Also, connection is equally slow in Gnome.

--- 192.168.1.2 ping statistics ---
29 packets transmitted, 29 received, 0% packet loss, time 27996ms
rtt min/avg/max/mdev = 0.028/0.034/0.042/0.006 ms

Any and all help is of course, much appreciated.

---

### Post by Crafty Kisses on 2009-02-02
What are the results of these commands?
```
lshw -C network
iwconfig
```

---

### Post by neanderslob on 2009-02-03
Never mind.  I changed the wireless card and it's flying now.  Upon inspection of the old card there was a bend in the connection of the antenna plug to the board.  My guess is that this partially severed the connection which created a bottleneck in the wireless card.  This bottleneck wasn't enough however to encumber the trivial amount of data that is sent and received in a ping.

---

