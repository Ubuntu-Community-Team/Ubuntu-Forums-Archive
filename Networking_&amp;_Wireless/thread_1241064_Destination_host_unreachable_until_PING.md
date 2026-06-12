---
title: "Destination host unreachable until PING"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by cristian.vrabie on 2009-08-15
Hi guys! I noticed a weird behavior in networking. Maybe you know which might be the cause. I'm not sure if is because the OS or wireless card or router, but in case you know, please share.

So both me and my wife have our laptops connected to our home WiFi router. I have an IP like 192.168.1.100 and my wife 192.168.1.101. If she tries to ping me she gets "Destination Host Unreachable". However if I do ping her it works. The first ping takes about 3000ms then the following ones only take about 1ms. After this she can ping me normally until my laptop enters screen saver when the problem reapers. 

Because of the long time it takes me to do the first ping I would say that some sort of connection is established, but why and how, I can't tell.

Got any ideas?

Btw. I have: Ubuntu 9.04 and she has Mint 7

---

### Post by harry2006 on 2009-08-15
sounds weird...i've never come across something like this :-)

---

### Post by xover on 2010-01-06
I have the exact same issue, did you overcome it? I have checked with tcpdump and the packet it not being received, yet as soon as I ping the host it immediately starts to respond, its almost like the NIC is asleep.

---

### Post by cristian.vrabie on 2010-01-06
Never found what it was but was solved after installing a fresh copy of Ubuntu 9.10

---

### Post by xover on 2010-01-07
One observation that I made was when changing network managers to wicd - which I don't advise, the interface appeared to flap, although the ping responses were constant with no loss.

It appears as though the NIC has developed a code of conduct, wireless rules of engagement, 'do not ping unless pinged upon'.

I would love to know how to diagnose the problem further, tcpdump is just showing that no packets are received, which makes sense. What I need is a  layer 2 data capture facility so that I can tell why the broadcast frame isn't replied to?

---

