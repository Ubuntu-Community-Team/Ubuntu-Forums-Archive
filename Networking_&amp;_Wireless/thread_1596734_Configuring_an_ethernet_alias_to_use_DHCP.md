---
title: "Configuring an ethernet alias to use DHCP"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by ubuguy on 2010-10-14
Hi,

I'm trying to setup my interface to default a static IP and use an alias to get a DHCP address.

I followed the example from:
[http://www.linuxtopia.org/online_books/linux_system_administration/debian_linux_guides/debian_linux_reference_guide/ch-gateway.en_016.html](http://www.linuxtopia.org/online_books/linux_system_administration/debian_linux_guides/debian_linux_reference_guide/ch-gateway.en_016.html)

**10.6.1.7 Configuring virtual interfaces**

   Using virtual interfaces you can configure a single Ethernet card to be an interface to several IP subnetworks.  For example, suppose your host is on LAN network 192.168.0.x/24.  You want to connect the host to the Internet using a public IP address provided via DHCP using your existing Ethernet card.  Edit /etc/network/interfaces so that it includes stanzas like these: 
       ```
iface eth0 inet static
             address 192.168.0.1
             netmask 255.255.255.0
             network 192.168.0.0
             broadcast 192.168.0.255
     



     iface eth0:dhcp inet dhcp
```  The interface eth0:0 is a virtual interface.  When it is brought up, so will its parent eth0. 



However, I get the following error when I try to start this up:

```
wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0:dhcp
```

---

### Post by Iowan on 2010-10-14
Have you tried it as in the article:> iface eth0:0 inet dhcp


---

