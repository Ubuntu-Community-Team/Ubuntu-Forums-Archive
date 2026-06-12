---
title: "Ubuntu Router with Multiple USB HSDPA Modems"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by spynappels on 2011-05-02
Hi knowledgeable folks

I'm looking for some help with some multiple WAN links on an Ubuntu router box I am building for a project.

The setup I'm trying to achieve is this:

eth0         WAN Link 1 through ADSL modem
USB Modem 1  WAN Link 2 for Failover
USB Modem 2  WAN Link 3 for Failover

eth1         LAN interface

The server would look after NAT, Firewall and routing to external networks. I also want it to look after Internet connection failover, so if the main WAN link goes down, it will fail over to whichever of the two USB HSDPA modems has the better signal strength and quality.

How would I go about this, if it is in fact possible?

---

### Post by lz1dsb on 2011-05-02
That's quite an interesting project. It would be interesting for me too if there's such a solution for Linux...

---

### Post by spynappels on 2011-05-03
Ok, just a friendly bump, can anyone help me with this?

---

