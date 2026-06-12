---
title: "Client-side routing"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2010-01-04
Is there a way by which I can control the routes of packets my pc is sending?

Like, if I want to send packet to some ip, i just send it to my gateway. The gateway forwards it to appropriate location, using hops: GW > A > B > C > DST

What I want to do is, send a packet which follows the alternative route that I specify, rather than the gateway: GW > X > Y > Z > DST

i.e I want control over not just the first hop, but subsequent hops as well...

---

### Post by puppywhacker on 2010-01-04
IP uses hop-by-hop routing, so you can only explicitly influence the first route to be taken. You can use source-list routing which is an IP option, which is rather a suggestion to the router than a hard directive.

---

### Post by hammad1337 on 2010-01-04
Thank you for your reply.
Actually, I needed the right term to google this up for more info, and you provided just that. :D

---

### Post by Vaidok on 2010-01-04
> **hammad1337 said:**
> Thank you for your reply.
Actually, I needed the right term to google this up for more info, and you provided just that. :D

Can you please post a source or two that you found on google?

---

