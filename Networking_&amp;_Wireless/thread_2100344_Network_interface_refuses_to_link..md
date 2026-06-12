---
title: "Network interface refuses to link."
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by jchamb2010 on 2013-01-01
Hello and thanks for taking the time to read my thread.

I am trying to get Ubuntu Server 12.04 Minimal to connect to multiple network interfaces at the same time, both on completely different networks, one internal, and one external.

My current /etc/network/interfaces looks like this:
```

auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 10.10.10.0
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255
gateway 10.10.10.1
dns-nameservers 8.8.4.4 8.8.8.8


iface eth1 inet static
address x.y.z.45
netmask 255.255.255.248
network x.y.z.40
broadcast x.y.z.47
gateway x.y.z.41
dns-nameservers 8.8.4.4 8.8.8.8

```

This is what I've done for testing so far: I disable eth0, I can ping 74.91.21.41 (gateway) but I cannot ping 8.8.8.8 (GoogleDNS).

I have a fairly odd setup and I'll try to explain it to the best of my ability.

I'm using VMWare ESXi with two virtual networks one that is connected directly to the internet, and the other which is connected to the internet through a firewall OS.

I need the firewall OS there in order to NAT incoming traffic on one IP address to multiple different VMs. (I know it's a bad setup, and I'm trying to work away from it.)

This server I'm having issues is the first server I'm trying to work away from NAT with. I'm trying to make it so users using the existing IP address will still be able to connect while migrating to a new dedicated (non NAT'd) IP address.


I don't know if my network setup is confusing the OS in some way, or if I've mis-configured something. Any help in this situation would be appreciated.

Thanks!
John

---

### Post by jchamb2010 on 2013-01-01
Problem solved:

I had to remove one of the gateways. Apparently you cannot have two gateways enabled at the same time or things don't work.

Thanks qman__ in #ubuntu-server for your help!

---

