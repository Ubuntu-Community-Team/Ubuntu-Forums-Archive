---
title: "Reach guests on other host machines on the same network"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by varelov on 2011-07-08
I have a laptop and a desktop, both running ubuntu 10.04 and Virtual Box OSE edition. Both have various guests installed on them. For the purpose of guests on both laptop and the desktop communicating with each other, I have added a bridged NIC to each VM that is supposed to communicate over the physical network. All guests on both machines are linux too. What else is there to configure in order to achieve communication of guests on different machines?
Both laptop and desktop connect to the router via wireless and both can ping each other.
I am trying to set the bridged NIC of one of the guests to be the default route for that guest (and possibly others with their internal network NIC's set to be in their own subnet) but the bridged NIC is shown to have only IPv6 address.

---

