---
title: "Varying packet loss on lan."
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by mojamoja on 2006-06-25
I'm having trouble with my network connection since yesterday, where I installed a few different VPN related packets and network manager (just added them, never ran or configured them).

I can't use SSH or anything else that needs low amounts of packet loss. I can use a browser, but every third time or so that I load a page I get a connection reset message.

Pinging with the default intervals return no errors, but if I flood ping a local host on the network (ping -f) I get about 7-10% packet loss. Routing seems to be normal as does my ipconfig. I have another computer next to it on the same hub, with no problems, and I have tried switching the network cable. I think this must be a software problem since I have not changed anything in the hardware configuration for many months. However I can flood ping localhost without getting any errors. My dmesg reports "eth0: no IPv6 routers present" but It doesnt seem to have any connections to my problem.

Please help me out.

---

