---
title: "ssh socks proxy - not working"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2011-08-10
Hi all.

I'm trying to connect to the web using a remote proxy via an ssh tunnel. I'm using the service 'tunnelr'. They are inexpensive, friendly and seem pretty cool.

I'm using this command to create the tunnel:
```
ssh -N -D 8888 username@la.tunnelr.com
```

I've set up both opera and a profile in firefox to use the socks proxy at port 8888 on the localhost.

When I try to open a page in firefox, I get a blank page. In opera, when I send a request to any site, I see "Connection closed by remote server".

When I fire up wireshark, I see very little ssh traffic. Probably only enough to account for control traffic between my host and the remote host.
The amount of traffic does not spike when I make web requests, as I expect it should.

What could be going wrong?

---

### Post by papibe on 2011-08-10
I've done that with my own home server, when at a Internet Café. It works great. Since the host you are connecting to is not yours, my guess is that you need some sort of support from them.

Just some thoughts,
Regards.

---

### Post by bobdobbs on 2011-08-10
> **papibe said:**
> I've done that with my own home server, when at a Internet Café. It works great. Since the host you are connecting to is not yours, my guess is that you need some sort of support from them.

Just some thoughts,
Regards.

I suspect that the problem is at my end, because of the low level of ssh traffic passing out from my host.

---

