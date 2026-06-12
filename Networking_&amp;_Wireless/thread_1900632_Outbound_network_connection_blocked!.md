---
title: "Outbound network connection blocked!"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by Gyurltrini on 2011-12-26
Hi!,
I've been having a number of issues with networking on an 11.10 server (no gui).
First I was trying to get my wireless card working, but no such luck (I think the card might be too old and possibly not working properly)
Then, initially I had the wired connection working, but then for some reason it began giving trouble. I don't know why, but, while I can connect to it on the network, the server can not connect to the internet to receive updates. I've tried to ping and nothing outside of the network gets through.

I tried to trace the route (i don't recall the correct command line for that right now) and that did nothing / did not bring up any script telling me the route

I've read that it is possible the outgoing port may be blocked, but ... well I've been looking at the server via webmin and in the networking interfaces area it says there is nothing blocked

Is there something that I have to do / check on the router? or anything else I could do / look at on the server?

---

### Post by Gyurltrini on 2011-12-26
I should also mention that the server is a development server but somehow it has dns enabled ... but since it is a development server there's no domain literally associated with it. The domain that was used is the isp's domain name.

As for the pinging thing, I discovered that it can connect and ping ip addresses outside the network, but can not ping domain names.

---

