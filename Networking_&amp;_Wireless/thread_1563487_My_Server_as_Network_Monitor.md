---
title: "My Server as Network Monitor"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2010-08-29
Done a fair bit of searching on this, but can't find quite the exact answer?

I have an always on box that serves up files via nfs/samba to my local network, and I also use it as a development environment, and it is port forwarded to the router to enable me to connect to it from the outside world when away from the local network.

Having moved to a bandwidth capped internet provision, I want to monitor all bandwidth usage for all PCs on the LAN so I can apportion costs accordingly. (for when we have to buy more bandwidth!)

Now I know I have to install a second NIC to my always on box, and then place it between my router (ADSL connection) and all other PCs, so that BANDWIDTHD can monitor the traffic. I have enough hardware switches about the place to connect up the network. Everything is wired.

I sense that this won't be plug and play though, so am seeking advice on the interfaces configuration for the two NICs:

1. All outgoing and incoming traffic from/to the Internet
2. All requests and provisions to LAN PCs

Always on box will be CLI 10.04 (Server or Minimal Installation)

So how is this done, and will there be any impact on network speeds, if everything has to pass through the always on box before reaching its destination (I'll be using 100/10 / gigabit NICs across the LAN)?

I could setup a wireless access point on the LAN (not on the router side), will bandwidthd pick up this traffic too?

---

### Post by Jose Catre-Vandis on 2010-09-05
bump?

---

### Post by perspectoff on 2010-09-05
> **Jose Catre-Vandis said:**
> Done a fair bit of searching on this, but can't find quite the exact answer?

I have an always on box that serves up files via nfs/samba to my local network, and I also use it as a development environment, and it is port forwarded to the router to enable me to connect to it from the outside world when away from the local network.

Having moved to a bandwidth capped internet provision, I want to monitor all bandwidth usage for all PCs on the LAN so I can apportion costs accordingly. (for when we have to buy more bandwidth!)

Now I know I have to install a second NIC to my always on box, and then place it between my router (ADSL connection) and all other PCs, so that BANDWIDTHD can monitor the traffic. I have enough hardware switches about the place to connect up the network. Everything is wired.

I sense that this won't be plug and play though, so am seeking advice on the interfaces configuration for the two NICs:

1. All outgoing and incoming traffic from/to the Internet
2. All requests and provisions to LAN PCs

Always on box will be CLI 10.04 (Server or Minimal Installation)

So how is this done, and will there be any impact on network speeds, if everything has to pass through the always on box before reaching its destination (I'll be using 100/10 / gigabit NICs across the LAN)?

I could setup a wireless access point on the LAN (not on the router side), will bandwidthd pick up this traffic too?

Start here: [https://help.ubuntu.com/community/NetworkMonitoringBridge](https://help.ubuntu.com/community/NetworkMonitoringBridge). The instructions are very old, but have some basics in them that haven't changed.

What software are you going to use? Software like Zenoss has full instructions for you.

No, adding a network monitor server generally doesn't slow down traffic very much. The computer is generally far faster than the Internet connection and does not provide a bottleneck.

---

### Post by Jose Catre-Vandis on 2010-09-06
Thanks perspectoff, I'll check it out

---

