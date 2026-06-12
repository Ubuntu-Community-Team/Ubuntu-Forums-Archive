---
title: "All forwarded inbound connections through my secondary gateway are ignored"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by dsjstc on 2010-03-26
I've got a couple of services forwarded through my primary gateway (192.168.0.1) to my linux server (192.168.0.2).  Everything works great.  Awesome.  I have a secondary ISP with a secondary gateway (192.168.0.3).  If I specify that as my gateway, everything works fine, which is very nice when the primary ISP goes down.

I've forwarded some ports (notably 22 for ssh) on the secondary gateway, just like I've done on the primary gateway.  That's so I have a back door into the network if the primary ISP goes down.  Makes sense, right?

However, the server totally ignores all connections (on any port) which came through the secondary gateway.  It's probably not routing; outbound connections work just fine if I specify the secondary as the gateway.  It's probably not firewalling; the iptables list is completely empty.  It's probably not the router configuration; a windows machine on the same network (192.168.0.10) accepts forwarded connections just fine.

Can anybody suggest anything easy to check before I start trying to learn how to use packet sniffers?

---

### Post by Iowan on 2010-03-26
Do those connections come in through different interfaces? Having them both in the same subnet *might* be problematic.

---

### Post by dsjstc on 2010-03-26
> **Iowan said:**
> Do those connections come in through different interfaces? Having them both in the same subnet *might* be problematic.

They're on the same subnet, and it surprises me to hear that you'd anticipate problems with that.  The windows machine, as I say, has no trouble at all.

Can you suggest some reading I might do to understand why it's a bad idea?

---

