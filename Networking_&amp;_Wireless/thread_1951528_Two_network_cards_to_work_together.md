---
title: "Two network cards to work together"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by cleytondim on 2012-04-02
Hello,
I have a big problem.
I'm trying to set up a ltsp server in my ubuntu 11.10

My server have 2 network cards (one onboard, eth0,  to my dhcp server, and one offboard, eth1, to my internet connection).

The problem is: the network cards dont work together. The ltsp-server is working fine with the eth0, the clients get the system and start it. But the internet didn´t work (neither in the clients nor int he server).  The internet only work in the server if i disable the eth0 interface.

I should mention that the eth0 dont have gateway configured, so it should work fine with the two cards, since only one have the gateway. But Dont  :confused:

Do someone know why is it happening?


ps: sorry for the bad english.  i'm brazilian.

---

### Post by dandnsmith on 2012-04-03
I very much suspect that the route table doesn't have the required entries.

Could you post the output of 
*sudo route*
which could help verify this.

There are schemes for setting up the required routes or otherwise effecting your scheme - but I'm not one who knows how to do this (have a look at some of the recent threads which treat with dual ethernet interfaces).

Start with [this thread](http://ubuntuforums.org/showthread.php?t=1564081)
more from [this](http://ubuntuforums.org/showthread.php?t=1947572) and look at the link to masquerading set up article in the last posting.

---

