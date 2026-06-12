---
title: "Wired Internet connections missing"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by martindee on 2009-04-10
Hello,
I am a "newby" to Ubuntu, I thought I would give it a try on an old Dell before moving across.

I had a successful installation, connected to the Internet, updated and added some new programmes with no problems at all.  Next time I booted and with no reason I seem to have lost network/internet connections.

The network symbols show an explanation mark, when I left click, it now says blanked in grey "No network devices connected".  There is no Eth0 which was previously shown under Network Connections. I tried adding a manual connection with a MAC address with no joy.

My system details are as follows Ubuntu 8.10, Router is a BT Broadband Wireless Router, but I am connected by ethernet cable. The computer used a D0Link DFE-530TX Fast Ethernet PCI adapter.

I have tried searching through current postings but can find now help there.  I have downloaded and read the Quick Ubuntu guide, but that seems to indicated that a wired network should be picked up and recognized and require nu further configuration.

I have tried to re-install Ubuntu with no luck.

I would be grateful for any assistance. I am enjoying the system and programmes that I can access, but internet connection is required togive me the fuller experience.

Martin

---

### Post by iponeverything on 2009-04-10
from a terminal prompt type "ifconfig" to see if it sees your interface.

If so -- It should just pull an address.  Are you showing a link light on the switch/router -- if not replace your cable.

---

### Post by martindee on 2009-04-14
> **iponeverything said:**
> from a terminal prompt type "ifconfig" to see if it sees your interface.

If so -- It should just pull an address.  Are you showing a link light on the switch/router -- if not replace your cable.
Iponeverything, Thanks for your prompt response. I did forget to menion that I am showing both lights on the connect from the router.

I have type ifconfig as suggested, her was the reply:-

"Link encap Loopback
inet addr: 127.0.0.1. Mask 255.0.0.0
inet6 addr:  ::1/128 Scope: Host
UP Loopback running MTU 16436  Mertric:1
RX packets 240  errors:0 dropped:0 overruns:0 frasme:0
TX packets 240  errors:0 dropped:0 overruns:0 frasme:0
Collisions:0 TXqueelen:0
RX bytes 15040 (15.0 KB)  TX bytes 15040 (15.0KB)"

Hope this helps

Martin

---

