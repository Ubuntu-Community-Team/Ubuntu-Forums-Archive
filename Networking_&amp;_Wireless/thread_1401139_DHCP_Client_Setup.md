---
title: "DHCP Client Setup"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by mjlackner on 2010-02-07
I feel a little funny opening this thread because everything is working well, I just want to understand why.

I have my DHCP Server running on my LinkSys Router (WRT54G), and my Ubuntu 9.10 desktop is showing an inet IP address in my ifconfig output.  I am getting to the Internet from all devices.

Trouble is, I am not seeing the IP/MAC entry in the LinkSys' DHCP Active IP Table list.  I am seeing several other devices (primary Windows XP box, wife's Win7 netbook, son's Win7 netbook, my iPhone, my work Win XP laptop), but not my fun new Ubuntu toybox.

My etc/dhclient.conf and etc/dhcpf.conf are both present, but empty.  I don't know for sure if the IP address I'm using is truly from a dynamic setup or static somewhere in the bowels of my toybox.

Does DHCP client have a parameter that executes the function, but hides the fact that it did so?

Thanks for any feedback.

---

### Post by Iowan on 2010-02-07
Look under */etc/dhcp3* - you should find dhclient.conf there.

---

