---
title: "Networking A linux system with an Xp System"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by frankie31337 on 2009-10-04
Hey guys new to Linux. Running jaunty. Need help getting Ubuntu to network with Xp. Any help appreciated. I really dont even know where to start. I do believe jaunty at least recognizes my systems onboard network card. But the Auto Eth0 option in Network Manager never connects. Says Wired Network offline. Right now I just have it set to use automatic DHCP. Don't know what to do. If anyone has the time to walk me through this I would greatly appreciate it.

---

### Post by Achilles124 on 2009-10-04
I am by no means an expert in networking but as far as I know Samba is used for it.

---

### Post by ermeyers on 2009-10-04
> **frankie31337 said:**
> Hey guys new to Linux. Running jaunty. Need help getting Ubuntu to network with Xp. Any help appreciated. I really dont even know where to start. I do believe jaunty at least recognizes my systems onboard network card. But the Auto Eth0 option in Network Manager never connects. Says Wired Network offline. Right now I just have it set to use automatic DHCP. Don't know what to do. If anyone has the time to walk me through this I would greatly appreciate it.

 Here's my example.  I have two dual-boot Dell pcs with Ubuntu 9.04 and XP.  Both OSes are setup for the same network config.

XP requires its NAT providing computer to have IP 192.168.0.1, so the computer with the LAN and WAN (internet) connection has the following configuration in Ubuntu, and any other computers on your LAN will get 192.168.0.0 addresses, like 192.168.0.2 to start with.

The eth0 is my LAN, and eth1_rename is my WAN/DSL connection that provides a 192.168.1.0 network number.  Node 192.168.1.1 is the DSL service's nameserver listed in /etc/resolv.conf via DHCP.

Edit /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255

auto eth1_rename
iface eth1_rename inet dhcp

```

Edit /etc/rc.local to have eth1_rename provide NAT function:
```


#NAT
sysctl -w net.ipv4.ip_forward=1
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1_rename -j MASQUERADE

exit 0

```

---

### Post by Iowan on 2009-10-04
> **frankie31337 said:**
>  I really dont even know where to start.Is this network between only the two machines, or are you adding Ubuntu to an existing system (even if "system" is XP and internet)? Does your network have a router (for internet access)?

---

### Post by frankie31337 on 2009-10-04
> **Iowan said:**
> Is this network between only the two machines, or are you adding Ubuntu to an existing system (even if "system" is XP and internet)? Does your network have a router (for internet access)?
 
Ok.
 
System 1 (best computer) Running windows XP with Ubuntu installed as dual boot. Installed inside windows option.
 
System 2 Running windows XP.
 
The two computers had been networked together using windows.  At this point what I want to do is put my wireless adapter on system 2.  
     
    Now I need to figure out how to network the Ubuntu system with System 2 running XP.  Network them together and make ubuntu grab the internet access from system 2 as well.  If you know how to do this I would really appreciate your input.

---

### Post by ermeyers on 2009-10-04
Whichever Windows computer will have the internet, it's LAN IP will have to be 192.168.0.1, because Windows XP does that to do Source-NAT (SNAT).  So, your other computer "grabbing" the internet off of the other computer will have to be 192.168.0.2, etc.

---

