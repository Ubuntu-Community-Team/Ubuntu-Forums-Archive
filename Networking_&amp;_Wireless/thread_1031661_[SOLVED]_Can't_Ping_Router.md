---
title: "[SOLVED] Can't Ping Router"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2009-01-05
Ok... so I'm setting up a server with 8.04.

I want a static address, obviously.

**The problem:** I can't ping my router, or access the internet.

**Pertinent Information:** 
I can ping other machines on my network from the server. 
I can ping the server from other machines on my network.


ifconfig (condensed):
inet addr:192.168.0.2 
Bcast:192.168.0.15 
Mask: 255.255.255.240


/etc/network/interfaces (condensed):
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.240
network 192.168.0.0
broadcast 192.168.0.15
gateway 192.168.0.1
#dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1


I added a static route with:
route add -net default gw 192.168.0.1 dev eth0


ip neigh returns:
192.168.0.1 dev eth0 lladdr 00:15:e9:7e:5c:14 REACHABLE

---

### Post by Iowan on 2009-01-05
> **DGortze380 said:**
> I can ping other machines on my network from the server. 
I can ping the server from other machines on my network.
Can you ping the router from other machines (or vice-versa)?
Does the server have a firewall active?

---

### Post by DGortze380 on 2009-01-05
> **Iowan said:**
> Can you ping the router from other machines (or vice-versa)?
Does the server have a firewall active?

Yes, I can ping the router from other machines.
The server is a default 8.04 install, to the best of my knowledge that mean IPTABLES set to allow pings by default.

---

### Post by Iowan on 2009-01-05
>  Ok... so I'm setting up a server with 8.04.
> The server is a default 8.10 install
I'm confused... It may not matter. Just to verify that it's not a firewall issue, you might turn off **ufw** and restart to see if anything changes.

---

### Post by DGortze380 on 2009-01-05
> **Iowan said:**
> I'm confused... It may not matter. Just to verify that it's not a firewall issue, you might turn off **ufw** and restart to see if anything changes.

Sorry... typo. I have an 8.10 desktop. The server is definitely 8.04 LTS

---

### Post by DGortze380 on 2009-01-05
No change with the firewall disabled

---

### Post by Iowan on 2009-01-05
Hmmm, easy "fixes" don't... Another [thread]("http://ubuntuforums.org/showthread.php?t=1028944") suggests network and broadcast address may not be necessary in static setup.
I have an 8.04 server - it originally set up DHCP, I moved it to static, then let it get a static lease from router (based on MAC address) - are you sure you don't want to try a static lease?  ;)

---

### Post by DGortze380 on 2009-01-05
> **Iowan said:**
> Hmmm, easy "fixes" don't... Another [thread]("http://ubuntuforums.org/showthread.php?t=1028944") suggests network and broadcast address may not be necessary in static setup.
I have an 8.04 server - it originally set up DHCP, I moved it to static, then let it get a static lease from router (based on MAC address) - are you sure you don't want to try a static lease?  ;)

I would love a static lease, unfortunately my cheap a$$ router won't do it. I'll try removing network and broadcast.

---

