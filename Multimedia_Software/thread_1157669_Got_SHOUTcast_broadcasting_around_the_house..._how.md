---
title: "Got SHOUTcast broadcasting around the house... how can i get it on the net?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by higashi on 2009-05-12
Title says it all. I have SHOUTcast up and running, have a server, i can listen to it from other computers around my house.
Now... how can i get it to the internet?
(for free pleez... dont care if it has to have some weird URL.. just.. i have no money to spend lolol )
T I A

---

### Post by bobince on 2009-05-13
> **higashi said:**
> how can i get it to the internet?

If you're using a router, you'll need to forward the incoming port that SHOUTcast is serving on (default 8000) to your computer. Then people can make incoming requests to http&#8203;://your.public.ip.address:8000/ to get the radio. (You may not be able to access yourself through the public IP address from inside your private network.)

You could then use a dynamic DNS service (dyndns.org etc.) to get a prettier hostname if you wanted.

If you also want to allow other DJs to connect to your radio server as sources, you'd also have to forward the source-port, which is always the listeners-port plus 1 (8001 by default).

Caveat: unless you've got a very fast internet connection, you'll run out of upload bandwidth quickly with only a few listeners. SHOUTcast servers are typically located in datacentres because home internet connections usually have quite poor upload speeds.

---

### Post by higashi on 2009-05-13
Thanks, but can you explain that in simpler terms? I don't understand especially the first part.

Also, all i really want to do is just be able to send a link to a couple of friends. i dont want ppl i dont kno listening to my station.

i already have a server up and everything,  i just need to figure out how to get my friends to listen.

EDIT: when i am running my shourcast server, it says in the terminal
> yp.shoutcast.com gave extended error (Cannot see your station/computer (IP: 96.20.133.112:8002) from the Internet, disable Internet Sharing/NAT/firewall/ISP cache (Connection timed out).)


... what do i do? :\

---

### Post by higashi on 2009-05-13
Nevermind, turns out its cuz i have a dynamic ip. i'll get that fixed later

---

### Post by bobince on 2009-05-13
> **higashi said:**
> I don't understand especially the first part.

[Port forwarding](http://en.wikipedia.org/wiki/Port_forwarding). If you use a router, you need to tell your router than anyone trying to connect to your public internet IP address on a particular port should be allowed through and directed to the same port on your computer itself. Exactly what the interface to this feature looks like depends on what router you are using.

If you use a firewall, you similarly need to tell it that incoming connections on the SHOUTcast port are okay. Exactly what the interface to this feature looks like depends on what firewall you are using.

---

