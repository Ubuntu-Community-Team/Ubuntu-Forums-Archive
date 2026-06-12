---
title: "wireless problems - this really should be working!"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by neill on 2006-06-04
hi

i've set up my linksys PCMCIA card in my Vaio using ndiswrapper and the netain driver for the airgo pre-n chip therein

the card is seen as OK and working in the config dialogues, wifi-radar sees my network, lights flash on the card, the WEP key is correct, and packets are passed - but i cannot get online !!

](*,) 

i'm fresh out of ideas now

where should i go form here ?

neill

---

### Post by lynxus on 2006-06-04
Check your default gateway & dns settings.

try pinging google see what responce u get.. Destination Unreachable will mean there is a routing problem ( Most likely a gateway issue ) 
if it times out then try pinging your router.. You should at least be able to ping that

If that fails then something major is up.. I would recomment wiping all tcp/ip settings and starting from scratch.

Oh and it mite be an idea to get your IP/settings via DHCP if your router can assign..that way ubuntu will be correctly configured.

---

