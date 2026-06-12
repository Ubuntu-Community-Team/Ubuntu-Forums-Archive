---
title: "Need help w/ tricky firewall forwarding"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-07-25
Hi,

Any idea how to do this?

I want to forward incoming SSH (port 22) traffic to a specific LAN client BUT ONLY when it comes from one particular IP block.

So for example, if the incoming IP is 111.111.111.110/24 and the incoming port is 22 then forward this traffic to 192.168.0.222

Otherwise, treat it as "normal" SSH traffic.  By normal, I mean we are already listening for SSH on the ubuntu server (localhost).  Any traffic NOT from 111.111.111.110/24 should be processed locally.

Does that make sense?  Is it doable?

Thanks

---

