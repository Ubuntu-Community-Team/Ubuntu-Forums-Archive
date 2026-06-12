---
title: "dhcp getting IP despite interface being marked as static (from local dhcpd)"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by spip on 2013-08-02
When the network first comes up, or I restart it via /etc/init.d/networking restart, my interfaces are configured correctly, that is eth0 has address 192.168.1.1 and eth1 gets an IP fetched via DHCP.

I have dhcpd running on this machine and serving off IPs off eth0 (what I mean is that in dhcpd.conf I only defined subnets within eth0's address range).

After a little while, eth0 gets an IP address in the dynamic range assigned by my local dhcpd server, despite being marked as static. Looking at the dhcp lease files confirms that an IP was fetched for it.

My interfaces file seems correct... is there something else that I should be aware of?

Appreciate any help. Regards,
spip


/etc/network/interfaces file inlined below, and the dhclient.conf (stock, untouched) and dhcpd.conf (nothing out of the ordinary) files are attached.


# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

# The primary network interface
auto eth1
iface eth1 inet dhcp

---

### Post by praseodym on 2013-08-02
Change "false" to "true" in the /etc/NetworkManager/NetworkManager.conf file. Otherwise the NWM cannot handle the manual config

---

### Post by spip on 2013-08-03
Hi there,

No such file. I forgot to mention, this is ubuntu server 12.04.  Would there be another process/service that does the same thing as NetworkManager and that would need to be disabled or configured properly?

spip

---

### Post by spip on 2013-08-03
Hmm, doing ps | grep dhclient showed the dhcp client was still running on eth0. I thought I had rebooted in between, but that was probably it. It is not running now. The problem may still occur if something else was launching the dhclient. I'll know in a few hours. :)

spip

---

### Post by spip on 2013-08-04
Ok that was it, I must not have rebooted. Must manually kill the dhclient after changing an interface from dynamic to static (opposite probably also true).

---

