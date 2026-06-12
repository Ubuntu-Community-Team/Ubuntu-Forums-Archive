---
title: "Separating download from upload"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by elfmind on 2010-07-08
I have the following network setup:

[IMG]http://i636.photobucket.com/albums/uu81/elfmind/NetworkSetup.jpg[/IMG]

The idea is to separate the download and the upload, namely to send the upload on Net1 and the download on Net2, completely transparent to the client.
My first ideas were using simple routing rules....having the default gateway for Gateway A over Net1 and having the route to the client in Gateway B over Net2. However, if I do that, the packets arriving in Gateway B from the client, aren't forwarded anymore. The same thing happens if I don't have any route to the client in Gateway B.
In order to forward the packets, does it really matter if the router knows how to route to the source and does it really mater if the packet arrives on the same interface as the routing rules point to?

---

### Post by elfmind on 2010-07-08
Solved. Just had to modify an option in sysctl to disable source verification.

---

