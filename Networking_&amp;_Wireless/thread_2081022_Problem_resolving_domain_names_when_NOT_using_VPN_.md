---
title: "Problem resolving domain names when NOT using VPN connection"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by JakobLu on 2012-11-05
Good evening everyone,

I have a rather strange problem with my wireless connection on my ubuntu machine(Ubuntu 12.04.1 LTS). When connecting to my wireless lan router(NETGEAR WGR614v9) I can't connect to any website(using firefox) or fetch my mail(thunderbird). The problem has first occured after a power outage at my flat while I was connected via VPN(shrewsoft client) with my university's network. When I use that connection now everything seems to be working just fine but after I disconnect the vpn client the problem reoccurs. For all the other machines in my flat the problem doesn't exist(although none of them are linux machines). My network card is a TP-Link TL-WN951N.
I'm not very experienced with linux networking but my guess is somethings wrong with my routing table? I will post you the output of 'ip route' when disconnected and when connected to the vpn:

When not connected:
```

default via 192.168.1.1 dev wlan0  proto static 
XXX.XXX.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.3  metric 2 

```

When connected:
```

default via YYY.YYY.YYY.157 dev tap0  proto static 
default via 192.168.1.1 dev wlan0  proto static 
YYY.YYY.YYY.0/24 dev tap0  proto kernel  scope link  src YYY.YYY.YYY.157 
YYY.YYY.ZZZ.ZZZ via 192.168.1.1 dev wlan0  proto static 
XXX.XXX.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.3  metric 2 

```

Not sure if it was really necessary but I hid the IP addresses(except for the local ones...). 

So if anyone has any idea on how to fix this I would be really grateful. Even if you can hint me in the right direction your comments will be much appreciated.

Thanks and good night
Jakob

---

### Post by JakobLu on 2012-11-05
I found out that i can connect to the homepage of my university even with the vpn connection disabled. I really don't understand why but it seems to be the only working address...

---

