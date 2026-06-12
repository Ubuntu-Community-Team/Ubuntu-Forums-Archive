---
title: "How to share network"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by nileshlog on 2009-07-01
I am able to get interned acces of my broadband on my laptop in ubuntu but am unable to share this network from ubuntu to access it on my mobile via Wifi. Pls guide me with the procedure.

---

### Post by t0mppa on 2009-07-01
So, if I understood you correctly your laptop is connected to the router through wired and you want to share the connection to your mobile phone through wireless?

You'll need a wireless interface that supports master mode (see [here]("https://help.ubuntu.com/community/WifiDocs/MasterMode") for more info) and then to route the traffic from it to your wired interface.

Never done this myself, so I'm not 100% sure, but I think you can just route the traffic from one NIC to another with the route command and thus create a bridge. But if that doesn't seem viable, then there are always the iptables (which feature a whole lot more configuration and even serve as a firewall, if you wish).

---

### Post by Iowan on 2009-07-01
[Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a help page that may be useful.

---

