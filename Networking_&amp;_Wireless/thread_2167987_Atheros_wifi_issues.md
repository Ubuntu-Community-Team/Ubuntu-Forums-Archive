---
title: "Atheros wifi issues"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by Rd7Tw4T on 2013-08-15
Hi everyone.  A bit of a noob here, well sort of.  I have been casually playing with lnux for about 6 years and have been running a home server using Zentyal for about 2 years.  There is still a lot I am trying to figure out and get used to.

In the past I have always been able to make things work, with a little help from browsing the forums.  The past few days I have been trying to set up a computer in my office across the street from where my internet is.  I am currently using a windows 7 laptop which connects to the wifi without any problems.  Here's the problem, neither wifi card that I have available will connect in Ubuntu.  Here are the two cards and the problems:

First card: Compex WLE300NX Atheros AR9390 XB114: This card was originally purchased to coincide with my server, but I moved shortly after purchasing it and it was no longer needed.  From my understanding it is a very powerful card and is supposedly compatible with ath9k.  It is capable of Tx Power at 27 dBm and 200 mW.  I have had great difficulty getting it to work.  At one point, it logged in while 15 feet from the router, but on the next reboot it would not connect.  I have not been successful in getting a connection since then.  As this is the more powerful card I would prefer to use it if anyone knows what needs to be done to make it work.

Second card: Tp-link Tl-wdn4800:  I do have this card up and running at the house (where the router is), but not in the office.  I have noticed that if I disable WPA2 (personal) in the router that I am able to connect, though only at 2mbps.  Oddly, this card is more powerful than the one in my laptop which will connect, under both Windows 7 and Ubuntu, and at a much faster speed.  I have tried adjusting the Tx Power, but the default is already the maximum.  The signal strength is at 75, which I realize is on the low side.  But like I said, the lesser card in the laptop connects just fine.

Any thoughts on how I might be able to get things working?

---

### Post by chadk5utc on 2013-08-17
Some of these cards can be frustrating to setup but most Atheros cards will work to some degree. This link should help get you going.
[http://wireless.kernel.org/en/users](http://wireless.kernel.org/en/users)

---

