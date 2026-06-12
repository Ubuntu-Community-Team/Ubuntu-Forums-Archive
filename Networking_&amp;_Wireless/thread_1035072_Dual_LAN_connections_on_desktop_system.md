---
title: "Dual LAN connections on desktop system"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by fhsm on 2009-01-09
I'm working on building an intranet for a department at my school. Those who will use my system currently connect to the internet over a wired LAN. We have no control over that system what-so-ever. It uses DHCP to auto assign everything (ip, gateway, dns etc).

Everyone already has a wireless card so I though an easy solution might be to run our system over wi-fi (over which we'd have full control). 

It would be very annoying having to enable and disable an adapter to swap between internet and intranet. Thus I need to have two live connections and a way to route traffic to the correct interface by destination. Is this even possible in theory? Does anyone have any tips on how to actually do it?

Ideally I don't want to require a lot of complex config on the client side for end users to fight.  Simple is clearly best here. If someone can think of an neat router trick that would be amazing.  

(oh, and no we can't just turn the a wired internet connection into a shared wifi connection to everything, that would get us in hot water with ITS).

---

### Post by Archmage on 2009-01-09
That is very possible. You only need to specifce the routing tables and than you can go.

E.g. I have 192.168.10.255 for my LAN and the remaning ones are the internet.

---

### Post by fhsm on 2009-01-10
> **Archmage said:**
> That is very possible. You only need to specifce the routing tables and than you can go.

E.g. I have 192.168.10.255 for my LAN and the remaning ones are the internet.

Sorry but I don't quite follow could you explain a bit more?

---

