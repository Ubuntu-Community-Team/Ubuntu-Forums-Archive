---
title: "Port 2126 - pktcable-cops, what is this port for?"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by sandman887 on 2011-06-03
I saw this on a list of assigned and registered ports, and I was curious about it, so I googled it and looked for it on wikipedia, and all I have found are more lists with this 2126 tcp/udp port, and all they say is that it is for pktcable-cops. 

I am curious what this "service" is for. I googled packet cable, and I found a patent describing a way to filter unwanted traffic, and it showed diagrams of networks, but it didn't say what this protocol or service is. It sounds similar to a firewall, but I don't think it qualifies as one.

I am surprised there is very little information that I was able to find on the internet about this service. Surely, some people know about it. Has anybody here seen this before?

---

### Post by gmargo on 2011-06-03
I noticed probably related ports 2246 and 3918 also:
```

pktcable-cops   2126/tcp   PktCable-COPS
pc-mta-addrmap  2246/tcp   PacketCable MTA Addr Map
pktcablemmcops  3918/tcp   PacketCableMultimediaCOPS

```The latter googled me into thinking it has to do with VoIP and Multimedia delivery over cable systems.

[http://en.wikipedia.org/wiki/PacketCable](http://en.wikipedia.org/wiki/PacketCable)
[http://www.cablelabs.com/packetcable/primer/index.html](http://www.cablelabs.com/packetcable/primer/index.html)


Update: See this page and search for "port 2126":
[http://what-when-how.com/voip-protocols/the-cablelabs%C2%AE-packetcable%E2%84%A2-quality-of-service-specification-dqos-voip-protocols/](http://what-when-how.com/voip-protocols/the-cablelabs%C2%AE-packetcable%E2%84%A2-quality-of-service-specification-dqos-voip-protocols/)

---

