---
title: "Got D-Link DI-824 (DI824) VUP Print Server to work!"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by caseybea on 2008-12-03
(Hi- I was going to reply to an earlier thread on this, but it has apparently been "archived", and I can not respond to it any more.   How totally annoying.)

ANYWAY--  the issue was using A D-LINK router, in this case a router WITH a built-in print server-- with Ubuntu (or any other linux, presumably). Mine is a DI-824 VUP.   But D-Link has a few models out there with the same capability.  A lot of people are out there, thinking they can't print to the D-Link unit with linux.    WRONG.  

The answer is simple-- which most people have tried and failed:   Which is to use cups and create a simple LPR/LPD queue to point to the IP address of the router, and use the (here's the tricky part) correct port (queue) name (for the parallel, or usb port).

That's the trick:  Most other postings suggest using LP0, LP1, USB0, etc---  they are all good suggestions (and work on linksys boxes, etc), but of course D-Link has to be different....

The answer:   The port (queue) for the parallel port is simply "lp", and the one for the USB port is "lpUSB0" (lowercase lp, UPPERCASE USB-ZERO).

I stumbled upon the answer in a MS Vista forum, and some guy had actually gotten a correct technical answer from a d-link dude.  Amazing.

Woohoo!  Works like a charm.  :guitar:



Here's the reference just in case:
[http://blog.mcinbaby.org/2007/04/windows-vista-and-d-link-routers-di.html](http://blog.mcinbaby.org/2007/04/windows-vista-and-d-link-routers-di.html)

---

