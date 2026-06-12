---
title: "No longer connects to OpenArena servers"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by qbee42 on 2009-02-20
Ubuntu 8.10
wired ethernet connection
Firestarter firewall
Open Arena 0.8.0-2 (started with 0.8.0, upgraded while testing)

I appear to have something fishy going on with my network. I can no longer connect to Open Arena servers, whether on our local LAN or on the Internet. The servers list okay, but when I attempt to connect it waits indefinitely for the server state. This is true whether using port 27960 or one of the alternate ports commonly found on the Internet servers.

Doing a packet sniff on the network shows that the Quake3 user datagrams from my computer to the server all have bad checksums.

Other network activity seems to work okay, both inside our local network and out to the Internet.

Open Arena connects properly from other Ubuntu and Windows boxes on our network.

Firestarter is set for open outbound connections.

I'm really puzzled by this. At first blush I would suspect that my network stack is hacked, or some sort of blocking is in place, but I am not sure what to test or how to do a clean install of the stack.

Any suggestions of what to try?

Thanks,
Tom

---

