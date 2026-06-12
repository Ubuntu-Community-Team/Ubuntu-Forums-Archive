---
title: "openconnect - major routing issues, Cisco VPN, 11.10"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by rigidkitchen on 2011-11-23
I am trying to connect remotely to my company's resources via their Cisco VPN.  They offer SSL-based ASA gateways that I can successfully connect to and navigate company resources, access email, etc.  However, I am not able to navigate to resources located outside of the company intranet while connected; for example, google.com or en.wikipedia.org are unreachable and I receive '503 Gateway' errors when navigating to external URLS.  I am also unable to split tunnel with this connection using network-manager-openconnect (the infamous 'Use this connection only for resources on its network' option).  Using openconnect from CLI yields similar results.

**Main operating system**: Xubuntu 11.10.  Tested in Kubuntu 11.10, Ubuntu 11.10, Ubuntu 10.10

**Installed packages**: openconnect, network-manager-openconnect, network-manager-openconnect-gnome.  Network Manager is ver. 0.9

**BEFORE**
*numerically*:
```

root@raft:/etc/vpnc# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2

```**AFTER**
```

oot@raft:/etc/vpnc# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 tun0
172.28.48.0     0.0.0.0         255.255.240.0   U         0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
<company HTTPS VPN gateway> 192.168.1.1     255.255.255.255 UGH       0 0          0 eth2

```Can someone who is more gifted at routing than me please explain why the route is failing once connecting to the VPN?  In the meantime I will attempt to connect manually and play around with default routes

---

### Post by dwmw2 on 2011-11-24
Please see the "Getting Help" section of [http://www.infradead.org/openconnect/mail.html](http://www.infradead.org/openconnect/mail.html)

---

### Post by rigidkitchen on 2011-11-24
Thanks for not skipping over my post and replying with this information!  I really appreciate it

---

### Post by BlastXng on 2012-03-01
> **rigidkitchen said:**
> I am trying to connect remotely to my company's resources via their Cisco VPN.  They offer SSL-based ASA gateways that I can successfully connect to and navigate company resources, access email, etc.  However, I am not able to navigate to resources located outside of the company intranet while connected; for example, google.com or en.wikipedia.org are unreachable and I receive '503 Gateway' errors when navigating to external URLS.  I am also unable to split tunnel with this connection using network-manager-openconnect (the infamous 'Use this connection only for resources on its network' option).  Using openconnect from CLI yields similar results.

**Main operating system**: Xubuntu 11.10.  Tested in Kubuntu 11.10, Ubuntu 11.10, Ubuntu 10.10

**Installed packages**: openconnect, network-manager-openconnect, network-manager-openconnect-gnome.  Network Manager is ver. 0.9

**BEFORE**
*numerically*:
```

root@raft:/etc/vpnc# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2

```**AFTER**
```

oot@raft:/etc/vpnc# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 tun0
172.28.48.0     0.0.0.0         255.255.240.0   U         0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
<company HTTPS VPN gateway> 192.168.1.1     255.255.255.255 UGH       0 0          0 eth2

```Can someone who is more gifted at routing than me please explain why the route is failing once connecting to the VPN?  In the meantime I will attempt to connect manually and play around with default routes

rigidkitchen

Did you get this corrected?

I looked at the route table, and what it appears is that your VPN Termination device is forcing all traffic toward it except if it local to your machine. I have seen this happen on Gentoo when working with ssl VPN's into Netscreen and Cisco. Did your IT guys tell you if they are requiring all traffic to come to them when you are connected?

L8r

Blast

---

