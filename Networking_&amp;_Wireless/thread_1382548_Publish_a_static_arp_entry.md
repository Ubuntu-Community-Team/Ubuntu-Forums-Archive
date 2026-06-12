---
title: "Publish a static arp entry"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by graag on 2010-01-16
Hi,

I would like to publish a static ARP entry. I hoped that
```
arp -i eth0 -s server 00:11:22:33:44:55 pub
```
would do the trick but it does not seem to work as I expected.

I'll try and explain what I'm trying to achieve. I have three boxes:

server -- router -- client.

I would like the client to do a PXE boot from an image that is stored on the server. And I would like the server to be able to power down when not used and wake up upon a unicast package (ethtool -s wol u).

I was able to get the two things to work independently. The PXE boot works when the server is on. The wake on lan via e.g. ping or http request works when I add a static ARP entry on the client.

But for the PXE boot I don't have an option to set a static ARP entry on the client. So I would like that the router would answer to ARP queries from client with the proper MAC address of the server nic.

Is this doable? If yes then how?

---

