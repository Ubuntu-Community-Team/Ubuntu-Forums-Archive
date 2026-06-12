---
title: "multi-homed networking"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by efpob on 2011-09-12
I'm trying to set up an application server with two NICS

I want ETH1 to only answer and respond to internal network requests eg 192.168.0.1/24

and ETH2 to service requests from the Internet, routed from my firewall

I can only get one or other to work, not both at the same time.  It seems to hinge on the gateway settings, if I have a gateway on ETH1, the server does not respond to internet requests, if I have a gateway on ETH2, the server doesn't respond to internal requests.

Can you point me in the right direction?

Thanks

---

### Post by cap10Ibraim on 2011-09-12
I don't get the topology the same firewall is processing public and private packets and then send them to your server ?

---

### Post by efpob on 2011-09-15
I have a server with one nic connected to the internal network so it can authenticate internal users on our AD

I then have the other nic on the public IP so that it is available from the internet.

I need to ensure requests sent through the public IP are returned via that nic, and not that on the internal nic.

At the moment, my configuration is as follows, which works for the most, but I'm sure there's a better way of doing it as I cannot access the internet from this server (to install updates etc)

The eth1 address is on our DMZ and is mapped to a public IP by our firewall

```
iface eth2 inet static
        address 192.168.101.13
        netmask 255.255.255.0
        network 192.168.101.0
        dns-nameservers 192.168.101.249 192.168.101.226 8.8.8.8
        post-up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.101.254
	pre-down route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.101.254

auto eth1
iface eth1 inet static
        address 172.16.1.3
        netmask 255.255.255.0
	network 172.16.1.0
	gateway 172.16.1.254
	dns-nameservers 8.8.8.8
```

---

### Post by SeijiSensei on 2011-09-16
That's the right configuration.  With this configuration, if you're on the machine itself, can you ping addresses on the Internet?

Are you asking about routing packets on the 192.168.101.0/24 network out to the Internet, or just about connecting from the dual-homed machine itself?  If you want to route packets, you must edit /etc/sysctl.conf and turn on IPv4 forwarding. The file has instructions.

Oh, one more thing.  You can only have one set of nameservers.  (The information is used to populate /etc/resolv.conf.) Use the complete list you have for 192.168.101.13.  The resolver will try each one of the entries in order until it finds a server to connect to.

BTW, what happened to eth0?  Usually the first interface encountered during boot is numbered zero, not one.

---

### Post by efpob on 2011-09-18
With the current configuration I can't ping IPs (eg google DNS) or connect to the internet on the machine.

Everything else works fine, it's accessible internally and from the internet.  The reason I need this to work is because it uses reCAPTCHA and cannot send the results back to their servers with the current set up

no idea what happened with eth0 - it was a preconfigured VM and what I added the adapters, they assigned themselves eth1 and 2

---

### Post by efpob on 2011-09-25
any idea what route I need to add to enable access to the internet from the box?

If I have the gateway on eth1, I cannot access the internet from the box, but the box is contactable from the internet.

If I have the gateway on eth2, I can access the internet from the box, but the box is not contactable from the internet!

---

