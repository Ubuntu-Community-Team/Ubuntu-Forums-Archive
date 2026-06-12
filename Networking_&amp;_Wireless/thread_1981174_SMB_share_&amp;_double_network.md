---
title: "SMB share &amp; double network"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by m0g on 2012-05-16
Hello everybody,

I'm actually trying to set on an Ubuntu home server with an old laptop. This server will mainly be used for smb file sharing & daap music streaming.

But the point is the following, I have two differents networks: the flat A with an internet connection and the flat B with an other internet connection. And I would like my smb sharing being accessible from both flat A & B.

To do so, I connected the laptop to the flat A with ethernet & to the flat B with wifi. Both are working (managed by network-manager), but it seems like the laptop can't manage the two connections and doesn't appears on the flat B network. I guess the fastest connection is privilegied (according to this [thread]("http://ubuntuforums.org/showthread.php?t=1093770")).

I use xubuntu 12.04 with the graphical interface for managing connections.

Thanks everybody for your help.

---

### Post by SeijiSensei on 2012-05-16
Are both Flats in the same subnet, e.g., 192.168.1.0/24? Can a machine in the Flat B network ping a machine in the Flat A network?  Are the two networks sharing the same router or do they have separate ones?

There's no issue of "privilege."  It's probably just a routing problem.  Pinging from one network to the other is a good place to start diagnosis.

---

### Post by m0g on 2012-05-16
No they're actually on two differents networks. And both uses their one router.

Both with the same address IP:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:5f:6a:be  
          inet adr:192.168.1.140  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21b:38ff:fe5f:6abe/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4264 erreurs:0 :0 overruns:0 frame:0
          TX packets:5590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:470596 (470.5 KB) Octets transmis:4800451 (4.8 MB)
          Interruption:18 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:281 erreurs:0 :0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:23360 (23.3 KB) Octets transmis:23360 (23.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:19:01:f0  
          inet adr:192.168.1.140  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21c:bfff:fe19:1f0/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:312 erreurs:0 :0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:19778 (19.7 KB) Octets transmis:14936 (14.9 KB)

```

---

### Post by SeijiSensei on 2012-05-16
Then you're much better off using separate subnets.  Put one of them in 192.168.2.0/24.  If the Linux box is routing between the networks, you need to enable IP forwarding in /etc/sysctl.conf by setting net.ipv4.ip_forward=1 as described in that file.  You'd want to have all the clients use the Linux box as their default gateway.  If you have Internet connectivity, the Linux box would then use the Internet router as its default gateway.

What's probably happening is that requests from the wifi side are coming into the Linux box, but replies are sent out the ethernet side.

---

