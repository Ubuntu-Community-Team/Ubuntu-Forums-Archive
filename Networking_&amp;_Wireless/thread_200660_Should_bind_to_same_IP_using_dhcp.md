---
title: "Should bind to same IP using dhcp?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Axier on 2006-06-20
A normal reboot with 6.06 on a LAMP-server and dhcp does not bind to the same IP as before. The normal procedure is that the dhcp-server offers the same IP to the client if it is not leased to another client. 

To acheive this the client shouldn't release the lease at reboot. As for now, the client gets a new IP every reboot. This is not standard in other distros like Fedora. does anyone know how to set the dhcp client to not release the IP at reboot? Static IP is not an option.

---

### Post by jvl on 2006-06-21
This depens on the dhcp server setup (i.e. the other side)
if you're the administrator, check out your dhcpd.conf file:

static binding looks like this (as an example):

host pc1 {
        hardware ethernet 00:E0:7D:DC:3E:53;
        fixed-address 10.123.19.2;
}

the time of the lease is influenced by the max-lease-time and default-lease-time settings, also found in the dhcpd.conf file.

If you're not the administrator of the dhcpd server, ask your ISP if they could provide you with static IP address. (static that could be acquired from the dhcp)

HTH

---

