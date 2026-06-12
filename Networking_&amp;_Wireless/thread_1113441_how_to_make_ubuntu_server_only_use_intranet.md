---
title: "how to make ubuntu server only use intranet"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by jmore9 on 2009-04-01
> OK i have been messing around for a while now on stopping my server from using the internet and only using the intranet .  I have a router to conect them to but so far it keeps connecting to the internet, which i don't want.

I have googled and read the debian manuals and am still confused on a simple way of allowing local computers to access the server and not allow the server to be seen on the internet.

Any one have any ideas or books or anything at all to get this thing finshed ?

using ubnutu server 7.04

Thanks in advance

---

### Post by capscrew on 2009-04-01
You should NAT the local network (LAN) and use a private IP address subnet.

See:

[http://en.wikipedia.org/wiki/Network_address_translation]("http://en.wikipedia.org/wiki/Network_address_translation")

[http://en.wikipedia.org/wiki/Private_network]("http://en.wikipedia.org/wiki/Private_network")

---

