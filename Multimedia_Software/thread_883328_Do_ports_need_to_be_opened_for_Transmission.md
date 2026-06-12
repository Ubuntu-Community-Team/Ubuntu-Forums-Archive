---
title: "Do ports need to be opened for Transmission?"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Beyla on 2008-08-07
I started using Transmission today but noticed that my download rates jump around considerably between my three downloads I have going right now (it'll be at like 800 kb/s then drop to 1 or 2 kb/s and repeat within the three downloads). 

In preferences it said that the port it was using was closed, and I read that Ubuntu comes default with closed ports...is this the problem and if so how do I open ports? Or is this no problem at all? (I'm new to linux/transmission and on the utorrent I used on windows it was a steady stream for the most part).

Thanks for the help

---

### Post by tuxxy on 2008-08-07
It should rune fine without you having to open ports.

You could try another client like Deluge to see if its transmissions problem

> sudo apt-get install deluge

---

### Post by Orfintain on 2008-08-11
I'm getting slower than expected transfer rates with transmission
and it is saying port is closed as well.

deluge installation didn't work..

user@:~$ sudo apt-get install deluge 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge


What does automatically map port mean?

I'm connected to dsl modem

---

### Post by redonwhite on 2008-08-11
my transmission is acting funny too.  my Download speeds are in the B/s.  And nothing will upload.

---

### Post by cozmicharlie on 2008-08-11
You need to forward a port in your router - this will show you how [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by Orfintain on 2008-08-11
Interesting, Problem is that It's not my router it's installed by the ISP ... what the protocol , can I reset the user/pass with out stopping the DSL (legal)?

Can I call my ISP and get the user/pass to rented router

Is there a work around?

---

### Post by cozmicharlie on 2008-08-11
> **Orfintain said:**
> Interesting, Problem is that It's not my router it's installed by the ISP ... what the protocol , can I reset the user/pass with out stopping the DSL (legal)?

Can I call my ISP and get the user/pass to rented router

Is there a work around?

I'm not sure what your set up is.  Do you connect right to the dsl without going through a router?  Are you on a work or school network?  If so most don't like bittorrent.  You could use Opera - it has a built in bittorrent client that works through the browser.

---

### Post by Orfintain on 2008-08-11
I'm in a private house, the phone line for DSL goes into the router that came from the ISP which has three computers plugged in via ethernet cables (which is actually legal I'm pretty sure)

what makes this interesting/problematic is the guy that is paying for the service (same house) is the kind of guy that falls for phishing scam's so i get to talk to his friend/tech guy in few days

I'll try opera thanks

Note: Bit tornado is working much better than bit transmission though I doubt it's what it should be with port's forwarded

---

### Post by Orfintain on 2008-08-12
Opera uses bit torrent which still requires ports

---

