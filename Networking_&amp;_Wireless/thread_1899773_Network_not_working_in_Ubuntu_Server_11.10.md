---
title: "Network not working in Ubuntu Server 11.10"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by terabytest on 2011-12-24
I'm trying to get 11.10 server running on an old pc but the network configuration failed on install and now it can't connect to the network.When I went to edit /etc/network/interfaces I noticed that it only contained the information for "lo" and none for eth0. So I tried adding:
```
auto eth0
iface eth0 inet dhcp
```
But then, when I restarted the networking service it hung and didn't complete the configuration.What might be the cause? Drivers? Configuration? Thanks in advance.

EDIT:
I looked inside my computer and discovered that my network adapter is a Realtek rtl8139 (non integrated) card. Doing lsmod shows no 8139-related drivers active. Doing modprobe 8139too runs the driver but restarting the networking interfaces still doesn't work (it says that eth0 is not found). What should I do?

---

### Post by dandnsmith on 2011-12-24
Have you looked to see what *lshw* is currently reporting about it, and what is in the messages and boot logs - sounds like you might, as have I several times, got a failed interface.

---

