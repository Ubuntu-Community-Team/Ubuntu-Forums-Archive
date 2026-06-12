---
title: "New setup - didn't ask for ip - how to set fixed ip?"
date: 2009-12-26
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-12-26
I just installed 9.10 clean, and it didn't ask for an ip address to use (or else I missed it).  It picked up a DHCP assigned address, but I want to set it to the same fixed ip that my old mythtv install had.

What's the best way to change it, and if I do, will that upset other configurations, such as the mySQL database, web server etc?

---

### Post by nickrout on 2009-12-26
> **ubnewbie2 said:**
> I just installed 9.10 clean, and it didn't ask for an ip address to use (or else I missed it).  It picked up a DHCP assigned address, but I want to set it to the same fixed ip that my old mythtv install had.

What's the best way to change it, and if I do, will that upset other configurations, such as the mySQL database, web server etc?

your dhcp server SHOULD be able to allocate an IP based on your MAC address on the ethernet card.

Alternatively you can add to /etc/network/interfaces, something like this:

```
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

---

### Post by lisati on 2009-12-26
> **nickrout said:**
> your dhcp server SHOULD be able to allocate an IP based on your MAC address on the ethernet card.



+1. I usually let my router choose the IP address, setting fixed addresses on the router if required.

---

### Post by ubnewbie2 on 2009-12-26
> **nickrout said:**
> your dhcp server SHOULD be able to allocate an IP based on your MAC address on the ethernet card.

Alternatively you can add to /etc/network/interfaces, something like this:

```
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

Great thanks.  ...and changing the address after installing won't upset any of the programs like mySQL, Apache, etc?

---

### Post by scsever on 2010-01-05
If this is also your backend (which it probably is) you may want to run Mythtv setup and change the IPs to match your static setting.  If no other frontends connect to it then I don't think you need to do a thing, when I run Mythtv setup I always set the IPs to my static IP.

---

