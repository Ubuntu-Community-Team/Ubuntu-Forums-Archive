---
title: "dns with dhcp/wireless broken"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by r.stiltskin on 2009-04-17
Solved: seems the problem wasn't in the laptop at all.  It now appears to be something wrong with a second wireless router in my network -- explained in post #3.


Ubuntu 8.04 Hardy Heron
Netgear WG511T PC Card - Atheros chipset
madwifi driver
DHCP
Westell 327W DSL modem/router  (Verizon dsl)

I have used this laptop with Edgy, Feisty and Gutsy with the same wireless card and madwifi, using DHCP, with no problems, and also for a little while with Hardy and had no trouble with either wireless or wired connections.  I haven't used it with wireless for a few months, until today, and suddenly it is not able to connect to anything on the internet when its ip address is assigned by dhcp.

I have no problem with wired connection using either a static address or dhclient.   Also, no problem if I configure the wireless interface with a static address.  And if I use dhclient to assign an ip address to the wireless interface, I can ping, ssh, etc., to any machine in my LAN, but can't connect (or even ping) anything outside.

AND the same thing is happening if I boot from a Knoppix 5.1.1 CD.

This seems crazy because I never had trouble like this before.  Can it be that the router is somehow causing this?  But how -- how can dns requests made from a static wireless address be answered, and all requests from a wired connection (static or dhcp) be answered, while dns requests from a dhcp-assigned wireless address are ignored?

---

### Post by r.stiltskin on 2009-04-17
Strangely, this problem did not seem to occur when I booted the laptop in WindowsXP.  Somehow the combination of Netgear's proprietary "Smart Configuration" program and XP's wireless network manager (configured to "obtain an IP address automatically" and "obtain DNS server address automatically" managed to make and maintain a fully-functional connection every time.

I also tried a PowerBook running Mac OSX which, not surprisingly, had the same problem as my Ubuntu notebook.

---

### Post by r.stiltskin on 2009-04-17
Apparently the problem was being caused by the DHCP server in a second wireless router in my network -- this one a Netgear WGT624.

At some point a few weeks ago the Westell router's DHCP server seemed to be causing trouble so I configured the Netgear router to also act as a DHCP server.  There was no address conflict -- the two routers were using different address ranges -- and it seemed to be working OK for my wife's Mac which has been connecting to the Netgear wirelessly from the far end of the house.

While playing with this last night, I discovered that I could get my laptop to connect wirelessly to the Westell router, but it couldn't use that connection to access any outside websites, so I thought that the Westell was the problem.  (I've been using it only for wired connections during the past few months.)

So, this morning I disabled the Westell's DHCP server & let the Netgear handle DHCP by itself: no good -- my laptop problem persisted.  It could still get a DHCP address that worked locally but couldn't get to the internet.

Then I disabled the Netgear DHCP server (leaving it functioning only as an access point) and set the Westell to handle the DHCP function by itself and now everything seems to be working.  I suppose it boils down to a defect or corrupted file in the Netgear router.

---

