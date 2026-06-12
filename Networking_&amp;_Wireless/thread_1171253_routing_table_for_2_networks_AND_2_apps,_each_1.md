---
title: "routing table for 2 networks AND 2 apps, each 1"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by berot3 on 2009-05-27
i am connected to 2 networks, 1 via eth0 and the other over wlan0. now i want to use firefox over wlan0, but use ssh over eth0...

of course i can route ALL to 1 or another network, but what command do i need to "pipe" *only* firefox, or any other programm over the networkinterface i want?


i hoped it would be something like "route add firefox eth0" :p

---

### Post by dandnsmith on 2009-05-27
I think you'll have to say more about what ranges of IP addresses you're using, to enable sensible conversation. What you're going to need is, I think, some kind of filter based on protocol types.

What you cannot do is to use the routing table and the route command - it isn't designed to handle different protocols differently, only routing by IP destination.

---

### Post by berot3 on 2009-05-27
well i googled till i didn't know what to google any more :D
[LIST]
of course "route" is not what i'm searching for. 
[/LIST]
[LIST]
do u mean by "protocol" tcp?
[/LIST]
here is what my Networkmanager gives me:
[IMG]http://g.imagehost.org/0443/Bildschirmfoto-Verbindungsinformationen-eth0.png[/IMG] [IMG]http://g.imagehost.org/0941/Bildschirmfoto-Verbindungsinformationen-wlan0.png[/IMG]
is that what u wanted?

---

### Post by dandnsmith on 2009-05-27
Having the IP addresses for the 2 interfaces in the same half of 192.168.1 makes routing difficult, and, anyway, the default gateway for both is the same (I guess a wireless router).

I'm not sure what you hope to gain by just taking a different path to the router.

---

### Post by MJBoa on 2009-05-27
Are both of those interfaces connected to the router?

---

### Post by berot3 on 2009-06-02
alright, seems i didnt make it clear enough :p

1.: this is not ONE network, i sure could connect them with a britch or some, but i dont want that
2.: one inernet-connection belongs to me, and only I use it for internet-surfing
[INDENT]this one is wired[/INDENT]
3.:the other internet-conncetion belongs to a neighbour, who shares with everybody 
[INDENT]over wlan[/INDENT]

so how can i use both of them? how can i tell an application to go over an other connection? 

lets say standart connection is my own, so every app i start or use goes over that NIC: eth0
but i want exactly ONE (with some kind of command or idk what) to go to my other NIC: wlan1

is there anything??? or anyone who understands my situation?

---

