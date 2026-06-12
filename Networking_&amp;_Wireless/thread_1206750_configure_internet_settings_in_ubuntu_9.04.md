---
title: "configure internet settings in ubuntu 9.04?"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by L0v3Rd0 on 2009-07-07
Hi all !

sorry for my bad english

  i cant connect to the internet !

i have a zte zxdsl 831 series adsl router

I Using connect to the internet : sudo pppoeconf

But there is a  problem


if i connect with proxy no problem :

[IMG]http://img89.imageshack.us/img89/2790/18163004.png[/IMG]

but how to connect by no proxy 

if i delete proxy no connection !!

[IMG]http://img246.imageshack.us/img246/6165/55446429.png[/IMG]



how to connect !!!!!!



please help me !

---

### Post by L0v3Rd0 on 2009-07-07
upup
please please help me

---

### Post by superprash2003 on 2009-07-08
post output of ifconfig from the terminal.. also output of cat /etc/resolv.conf .. you cant access ANY site at all without proxy?

---

### Post by martinbaselier on 2009-07-21
You have a proxy at work, so normally you would not be allowed to connect to the internet at your work, without using their proxy server. 

As you statet in your first post, it works fine when using the proxy. 

Why would you want to disable that?

---

### Post by DJonsson2008 on 2009-07-29
i had a similar problem, 
could ping gateway router
could open gateway router admin page in browser

lan seemed to be working

but could not see internet.

this seems like a similar problem i had with 
can't see internet
no internet but can see lan on 8.4

the problem was in /etc/resolv.conf

ifconfig looked ok and showing
the network card was working...

route 
showed either no gateway or wrong gateway

the solution was incredibly simple.

adding the following line
with number of gateway router
solved the problem instantly closed
and reopened browser and it worked.

nameserver XXX.XXX.XXX.XXX 

i also note in the sample resolv.conf 
a line called 

search com

not sure what that is but i added it for good luck.
not sure if it helped but i can now see the internet

---

