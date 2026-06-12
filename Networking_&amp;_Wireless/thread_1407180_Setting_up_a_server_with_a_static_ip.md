---
title: "Setting up a server with a static ip"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by Scootm on 2010-02-14
I'm trying to set my computer up as a server. I've installed LAMP, but now my problem is getting a static ip. I've tried several tutorials, but with each one, I seem to somehow disable my internet connection. 

I'm almost positive that this is all over my head, but my aim is for it to not be. So any direction would be great, thank you.

---

### Post by 2hot6ft2 on 2010-02-15
If you're using a router it's usually done in the routers configuration by assigning a static IP to the MAC of the interface you're using. Use ifconfig in a terminal on the server to find out the MAC address of your adapter.

---

### Post by lavinog on 2010-02-15
This should give you some insight:
```
man interfaces
```

---

### Post by lavinog on 2010-02-15
/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

```
this should set your static ip to 192.168.1.2

---

### Post by Scootm on 2010-02-15
Is the MAC address the same as the HWaddr listed when ifconfig is run?

---

### Post by jken146 on 2010-02-15
> **Scootm said:**
> Is the MAC address the same as the HWaddr listed when ifconfig is run?

Yes.

---

### Post by lavinog on 2010-02-15
> **Scootm said:**
> Is the MAC address the same as the HWaddr listed when ifconfig is run?

yes

---

### Post by lisati on 2010-02-15
> **2hot6ft2 said:**
> If you're using a router it's usually done in the routers configuration by assigning a static IP to the MAC of the interface you're using. Use ifconfig in a terminal on the server to find out the MAC address of your adapter.

+1. Using the router can make life a lot easier.

---

### Post by Scootm on 2010-02-15
Yes, I'm using a router, however, I can't figure out how to assign a static IP to the MAC address. I've tried looking up the manual (through the 192.168.1.1 router site) and it can't find the pdf. Ugh.

Thanks, though. Lots of help so far.

---

### Post by adam814 on 2010-02-15
Most routers (at least the last few I've used) will let you "reserve" an IP in the DHCP pool for specific MAC addresses.  If yours has no such option it should at least have an option to disable DHCP (then you'd need to configure all your machines statically, but at least you'd have your server static).

---

### Post by lavinog on 2010-02-15
> **adam814 said:**
> Most routers (at least the last few I've used) will let you "reserve" an IP in the DHCP pool for specific MAC addresses.  If yours has no such option it should at least have an option to disable DHCP (then you'd need to configure all your machines statically, but at least you'd have your server static).

Most routers use a range of ip address that are configured for dhcp.  addresses outside this range need to be configured statically.

I have a linksys router that has an option: Starting IP address: 192.168.1.[100]
This means I can statically assign my server to be an address under 100.

See my above post on how to assign a static address from the server.

---

