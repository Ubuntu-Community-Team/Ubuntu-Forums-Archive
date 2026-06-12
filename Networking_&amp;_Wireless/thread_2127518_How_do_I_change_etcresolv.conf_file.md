---
title: "How do I change /etc/resolv.conf file ?"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by purohit on 2013-03-20
am using ubuntu 12.04. How do I change /etc/resolv.conf file ? Every time I edit it , it automatically gets reset. If I want to retain changes in the file what needs to be done. when I browsed through internet I found some solutions one of them was   adding the nameserver to /etc/resolvconf/resolv.conf.d/head  adding the nameserver to /etc/resolvconf/resolv.conf.d/base
  But even after adding the nameserver to above mentioned files and  restarting the services , the /etc/resolv.conf  automatically gets  reset. 
  I want to permanently retain changes in /etc/resolv.conf file .

---

### Post by Karlchen on 2013-03-20
Hello, purohit.Edit the file  /etc/resolvconf/resolv.conf.d/tail instead. If it does not exist, create it. For further details run ```
man 8 resolvconf
```Kind regards,Karl

---

### Post by Cheesemill on 2013-03-20
Or you can add a dns-nameservers line to your /etc/network/interfaces file...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# External interface
auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.254
    dns-nameservers 192.168.1.254
```

---

### Post by jdthood on 2013-03-20
If your interface is configured via DHCP you don't have to enter nameserver addresses anywhere.

If your interface is configured statically by NetworkManager, use the Connection Editor to enter nameserver addresses. 

If your interface is configured statically by ifupdown, enter the nameserver addresses on a "dns-nameservers" line as Cheesemill suggested.

Do *not* put "nameserver" lines in any of the files in /etc/resolvconf/resolv.conf.d/ except as a temporary measure.

The OP wrote:
> But even after adding the nameserver to above mentioned files and restarting the services ,
> the /etc/resolv.conf automatically gets reset. 

Sounds as if resolvconf isn't in control of resolv.conf, otherwise the contents of the above mentioned files would show up in resolv.conf. Run "sudo dpkg-reconfigure resolvconf" to recreate the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf. Are you by any chance using a third-party VPN client program or something like that which futzes directly with the /etc/resolv.conf file?

---

