---
title: "Apache: Throttle Upload *and* Download Speeds?"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by pneumatic on 2011-08-09
Hi - I have installed libapache2-mod-bw and it works great to throttle download speeds to the clients (i.e. - the bandwidth out of the server can be controlled just peachy).

However, I need to limit the bandwidth *into* the server from specific networks because my WAN links are tiny and do not have QoS or shaping of any sort (I know, I know - contracts in place - will be fixed in November - not my design).

Is this possible?

I know that there are ways to throttle this at the interface level (e.g. - wondershaper) but I'd like to allow full bandwidth to the clients that are connected locally.  The server in question is for web file transfers (under apache2 on 443) and expected file sizes are up to 2GB so a per-network limit would prove helpful.

---

### Post by jmoorse on 2011-08-12
Short answer, no.  You cannot truly control what upload traffic (from your perspective) the service provider sends you.  From your firewall you can control what leeches into your LAN, but that will not stop pointless ingress utilization of your WAN link.

Some service providers provide firewalling, shaping, etc at customer request.  If you have a particular VIP assigned to your www, you may be able to get them to shape it for you in their cloud.  You mentioned this in your question, but that is what came to mind first too. 

Does that answer your question?

---

### Post by pneumatic on 2011-08-12
I was able to get this done with FreeBSD.  It appears that Linux can only shape traffic at the interface level while the BSDs can shape down to the source level.

This allows me to set certain networks to 1Mbps uploads while others can upload at full speed.

Wondershaper works for limiting upload speeds with Linux - but only at the interface level (e.g - eth0).  I suppose that I could have accomplished the same thing with multiple NICs but it was easier to go with FreeBSD.

---

