---
title: "Deluge killing network connections?"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by OliW on 2010-10-07
I've noticed that if I leave deluge-torrent running for more than a few minutes, it starts to nuke the network connection. IRC goes into fits and some pages don't load first time.

The only common factor is that deluge is running when this happens. As soon as I exit it, everything else springs into action.

I'm on a 64bit upgrade.

Anybody else getting similar behaviour?

---

### Post by MishaAct on 2010-10-07
It can be a router problem (It must be a router problem IMO).

---

### Post by xircon on 2010-10-07
Bet you ISP is "traffic shaping" mine does, run a torrent and everything else crawls.  Does everything come back to normal if you stop the torrent?  That is a sure sign!

---

### Post by e79 on 2010-10-07
> **MishaAct said:**
> It can be a router problem (It must be a router problem IMO).
 
+1
I had similar problems using a Linsksys BEFSR41, everytime I would start downloading some torrents, I had network connection problems, it would drop, reconnect, drop again and so on until I change my router; I now have an old PC that I turned into a Linux firewall and since, everything works like a charm !

---

### Post by OliW on 2010-10-07
Well I connected to IRC on my phone and that's been diconnecting too (suggesting it's something at network level).

I switched out to Transmission to make sure Deluge isn't flooding the network with silly traffic and it's having a negative effect on IRC still.

The strange thing is this is quite recent (suspiciously close to when I upgraded to Maverick) and nothing in the network has changed.

I've asked the ISP and they say their p2p shaping hasn't changed in months. I'm inclined to believe them and I also don't see how their shaping would (or should) affect IRC.

I'll try swapping the router out for an old spare when I can remember where I put it.

---

### Post by whoop on 2010-10-07
I had that same problem with a crappy router...

Try disabling dht as an experiment...

---

### Post by SeijiSensei on 2010-10-07
Try reducing the number of simultaneous connections your torrent client is making.  Note this isn't about bandwidth limits but the number of connections.  Your router has to maintain an entry in its "NAT" tables for each and every peer to which you're connected.  Most consumer routers don't have very big NAT tables and fall over when they have to deal with a large number of peers.

Gaming routers appear to be better at this than normal consumer-grade routers.

---

### Post by cuby on 2010-10-09
Hello.
Two days ago I installed Maverick RC amd64. Before that, with ubuntu 10.04 32bits, deluge worked flawlessly.

With the exact same configuration, first it used 100% CPU, after some tweaks (ports and encryption) it started to work well, but my router freezes frequently (never happened before). Now, I did some stupid thing and I'm unable to get incoming connections. Changed router and everything.

I think the app is broken and I'm considering to file a bug report.

---

