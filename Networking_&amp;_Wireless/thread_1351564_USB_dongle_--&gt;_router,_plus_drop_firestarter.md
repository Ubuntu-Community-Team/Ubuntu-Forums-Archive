---
title: "USB dongle --&gt; router, plus drop firestarter"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-12-10
Hi,

I have been using Ubuntu 9.04 (all updates applied) for quite a while, and want to purchase a 3G router. The one I'm getting is a [N3G002W 3G Wireless Router (PCMCIA & USB Modem Compatible): : NetComm Australia]("http://www.netcomm.com.au/products/3g/n3g002w")

My current interfaces file has been ..

> 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0



iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0


as I have been using the USB dongle directly connected to the computer. Now the USB will be attached to the router.

Firestarter has been giving me a lot of pain, and I'd rather drop it, and just use iptables.

What changes do I need to do all this please ?

* 'Flush' all firestarter rules from iptables, and have a clean/fresh iptables

* Modify /etc/network/interfaces, so that internet is via eth0, and not ppp0

* Still have ICS, so that other computers can access the internet via the lan, which will be hooke dup to the router.

* Network Manager has the current connection as 'wireless broadband', I assume that won't change.

The router should assign IP's, and also set the basic 'rules', what ports to open, etc.

Thanks,

Oygle

---

### Post by oygle on 2009-12-11
1. To flush iptables, do I just do this ?

```

iptables -F

```

2. To remove firestarter ?

```

sudo apt-get remove --purge firestarter

```

3. If I use the router to define incoming potrs allowed, is this all I need, or do I need it at all ?

```

# Add in any other ports you wish:
sudo iptables -A OUTPUT -p -tcp -m multiport --dport 80,443 -j ACCEPT
sudo iptables -A OUTPUT -p -udp --dport 53 -j ACCEPT
sudo iptables -A OUTPUT -j DROP

```

4. How do I modify /etc/network/interfaces, so that internet is via eth0, and not ppp0 ?

5. Any other issues , or things I need to change ?

Oygle

---

### Post by oygle on 2009-12-11
Any advice/guide here would be appreciated, thanks.  :)

Oygle

---

### Post by oygle on 2009-12-20
Does anyone have any ideas on this please ?

Oygle

---

