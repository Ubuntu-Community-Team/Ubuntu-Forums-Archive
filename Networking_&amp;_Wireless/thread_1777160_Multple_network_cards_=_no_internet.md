---
title: "Multple network cards = no internet?"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by chasingshadows on 2011-06-07
Hi.

I have this setup in my /etc/network/interfaces

```

auto lo
iface lo inet loopback

eith eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 79.138.xxx.xxx
netmask 255.255.255.0
broadcast 79.138.xxx.xxx
gateway 79.138.xxx.xxx
dns-nameservers 79.138.xxx.xxx 85.8.xxx.xxx

```When I have both interfaces up, I cant ping any ip addresses.
If i take down either eth0 OR eth1 it starts working.

Resolv.conf contains nameservers for both interfaces.

I have setup networking plenty of times before but this time I just seem to have f-ed something up totally. And I can't seem to find where the error is.

Any suggestions as to where I should start searching?

---

### Post by Lloyd_mcse on 2011-06-07
Try and remove the gateway from eth0, I had a similar issue and that fixed it.

For example..

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1


auto eth2
iface eth2 inet static
address 192.168.1.101
netmask 255.255.255.0
    

Is working for me.

---

### Post by SeijiSensei on 2011-06-07
Does the DHCP server also give out a gateway address?  You can only have one default gateway, as that is the router that handles traffic that doesn't match any local subnets.  Since it appears eth0 is connected to the Internet, that's the one that needs the gateway.

If you can't change the configuration of the DHCP server, you can edit /etc/dhcp3/dhclient.conf and remove the "routers" entry from the "request" directive.

---

### Post by chasingshadows on 2011-06-07
Yeah it worked when I removed the gateway from my internet connection. However. removing it from the local dhcp that is only meant as a management network to the server seems like a better approach.

Thx for the solution to the problem.

---

