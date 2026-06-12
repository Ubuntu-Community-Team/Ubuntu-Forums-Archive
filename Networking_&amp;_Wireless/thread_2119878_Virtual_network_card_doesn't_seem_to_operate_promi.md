---
title: "Virtual network card doesn't seem to operate promiscuously"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by noah++ on 2013-02-25
Hi,

I'm using a lab environment comprising three Xubuntu 12.04.1 VMs under VirtualBox 4.0.6. Each VM has an adapter connected to the same VirtualBox internal-only network.

I need one VM to sniff the network traffic of another. But Wireshark isn't seeing a single packet not addressed to or from the sniffing VM itself.

What I've tried:
[LIST]
[*]Putting the adapter into promiscuous mode explicitly with [FONT="Courier New"]ip link set promisc on eth2[/FONT].
[*]Changing the network from internal to host-only. (When I do this, I can see some packets from a new network I'm not trying to sniff on, but that's all.)
[*]Changing the adapter from E1000 to the paravirtualized one.
[/LIST]

No change. Thoughts?

---

