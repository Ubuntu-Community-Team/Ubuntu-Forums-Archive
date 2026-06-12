---
title: "TCP socket issue with libevent"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Anoop.kulkarni on 2010-02-09
Hi,

I have server-client program that initializes TCP socket for communication and uses libevent 1.4 calls event_set and event_add followed by event_dispatch for scheduing the socket read and write through a socketeventcallback function.

I am trying to get this program started at bootup time in Ubuntu 9.10 and am unsuccessful. When I traced through the execution sequence, have realised that it exits with an error on "recv" function (part of the socketeventcallback function). It is not able to read from the socket, although the socket is properly established and listening.

Is there something about libevent at bootup time in Ubuntu that I need to watch for? Has anyone seen/know of such behaviour?

If I start the program later from a terminal, it works just fine.

Thanks for your comments.
~anoop
-- 
Anoop Kulkarni, PhD

---

