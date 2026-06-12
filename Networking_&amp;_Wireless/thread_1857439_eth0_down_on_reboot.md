---
title: "eth0 down on reboot"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by digitlman on 2011-10-10
Running 11.04 x64 server.

This is a vm with a single E1000 vmware network adapter.

kernel is v 2.6.38-11-server.

After recent round up updates, every time I reboot this vm eth0 is down.  I have to manually ifsown eth0 up from CLI.

Any ideas why this is happening?

---

### Post by newbie-user on 2011-10-11
You may want to check if the vm network interface for the server is set to "connect at power on" inside of vmware.

---

### Post by digitlman on 2011-10-11
It is.

---

### Post by newbie-user on 2011-10-11
Okay, then maybe check the settings in /etc/network/interfaces to see if the interface is being activated.  

change (for your specific interface):
auto eth0
#iface eth0 inet dhcp

to:
auto eth0
iface eth0 inet dhcp

---

