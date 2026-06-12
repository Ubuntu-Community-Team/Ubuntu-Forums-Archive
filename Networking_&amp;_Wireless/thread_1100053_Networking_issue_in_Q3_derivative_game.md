---
title: "Networking issue in Q3 derivative game"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by akincer on 2009-03-18
Game: Urban Terror 4.1

I'm having an issue on 8.10 where the network seems to hang for and the game freezes for a second. There seems to be other hiccups a long the way. Here's a picture of my netgraph in the game:

[IMG]http://www.urtalphaclan.com/netgraph.jpg[/IMG]

Note the hole in the green graph on the right. That's when the freeze occurs.

This problem did not exist in 8.04 on identical hardware. Any ideas?

SOLVED:

I did some research and it appears the problem is with Pulse Audio. By disabling Pulse Audio, the major lag issues went away. There are still some issues with it lagging, but the issue described here is resolved by killing Pulse Audio.

---

### Post by akincer on 2009-03-30
I have heard from a friend he experiences the same thing on the latest 9.04 beta. I'm going to test and validate to make sure, but it sounds like whatever the issue is has not been magically fixed in the latest iteration.

Any ideas?

---

