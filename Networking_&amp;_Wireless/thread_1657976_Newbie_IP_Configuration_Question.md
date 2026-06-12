---
title: "Newbie IP Configuration Question"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by TomOttaway on 2011-01-01
I just installed Ubuntu Server 10.10 on an old Dell PowerEdge server just to learn about Ubuntu.  I edited /etc/network/interfaces to contain:

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

I edited /etc/resolv.conf to point at my ISP's DNS servers:

nameserver 24.116.2.50
nameserver 24.116.2.34

and then did an ipup, and restarted OpenSSH, and httpd.  I can ping the server, but the server can't ping anything (other than the loopback addresse).  I can't see Apache from a different computer.  I can connect using PuTTY from a Windows laptop.  Any thoughts on errors in my configuration?  With the exception of SSH it seems like the server can receive but not transmit.

Thanks for any hints,

Tom Ottaway

---

### Post by PatchesTheCaveman on 2011-01-02
Hi TomOttaway!

Run these commands to see whether all your configuration options are in effect:
```
ifconfig -a
ip route show
```

---

### Post by perspectoff on 2011-01-02
Network Manager interferes with managing your connections through the /etc/network/interfaces file.

If you want to manage your network connections manually like this, you probably should remove Network Manager.

---

### Post by chili555 on 2011-01-02
> you probably should remove Network Manager.Is it included on a server install?

---

