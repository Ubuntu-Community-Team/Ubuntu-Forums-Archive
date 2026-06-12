---
title: "My PC cannot see anymore the LAN, but eth0 is up"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by dejudicibus on 2009-11-13
I am getting crazy with networking settings of Ubuntu (9.10 karmic gnome). I have a home LAN connected to Internet through an ADSL router (192.168.1.1). Several PC's, NAS and other devices are connected to that LAN. Some get the IP address through DHCP, some have a static IP address (e.g. NAS). One of the PC is a laptop where I installed Ubuntu 9.10. I had no problem to connect it to the network, even if I had to uninstall Firestarter and use UFW to browse the Windows shares.

Few hours ago, after an update and the installation of Gnome Do (which froze my machine several times), the laptop stopped to see the LAN. It can see both eth0 (wired connection) and eth1 (wireless) but I cannot ping anymore other IP addresses (router included) or see the web. 

I spent several hours to play with various configuration files as smb.conf, resolv.conf, hosts, interfaces, nsswitch.conf and so forth, with no result. If I use route -n command I get now:

```
192.168.1.0  0.0.0.0      255.255.255.0 U   0    0 0 eth1
192.168.1.0  0.0.0.0      255.255.255.0 U   1    0 0 eth0
169.254.0.0  0.0.0.0      255.255.0.0   U   1000 0 0 eth0
0.0.0.0      192.168.1.1  0.0.0.0       UG  0    0 0 eth0
0.0.0.0      192.168.1.1  0.0.0.0       UG  100  0 0 eth1
0.0.0.0      192.168.1.1  0.0.0.0       UG  100  0 0 eth0
```

Any idea what's wrong? I am new to ubuntu since I work with it only from the last week.

INTERFACES
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
```

SBM.CONF
```
...
workgroup = MYWG
netbios name = mynbn
domain master = yes
wins support = yes
name resolve order = lmhosts wins bcast host
...

```
HOSTS
```
127.0.0.1 localhost
```

RESOLV.CONF
```
nameserver 192.168.1.1
```

NSSWITCH.CONF
```
...
hosts: files msdns4_minimal [NOTFOUND=return] dns wins mdns4
networks: files
...
```

OUTPUT of IFCONFIG
```
eth0 --> 192.168.1.10/255.255.255.0
eth1 --> 192.168.1.5/255.255.255.0
lo   --> 127.0.0.1/0.0.0.0
```

---

### Post by Iowan on 2009-11-13
Having both interfaces in the same subnet is gonna play havoc with routing.  With two default gateways, it's hard to tell where (or if) traffic will go. You may be able to get back network access by taking down either interface.

---

### Post by dejudicibus on 2009-11-13
> **Iowan said:**
> Having both interfaces in the same subnet is gonna play havoc with routing.  With two default gateways, it's hard to tell where (or if) traffic will go. You may be able to get back network access by taking down either interface.

OK, but that's a laptop, that is, it has a wireless adapter and an Ethernet card. It always had two interfaces. The point is, how should I change my conf files to make it work? It worked before updating Ubuntu, so there should be a way. Any suggestion? By the way, I tried to comment out eth1 in a conf file but it made no change. I also disabled wireless. No result.

---

### Post by dejudicibus on 2009-11-15
Sigh... no hints?

---

### Post by Iowan on 2009-11-15
Did you reboot/restart after making changes? Re-check **route**. The multiple (default) gateways will probably be an issue.  There are ways to remove them - if a reboot/restart doesn't do it.

---

### Post by utnubuuser on 2009-11-15
I hate to say it, but I've had better luck with wicd instead of the default network manager

---

### Post by dejudicibus on 2009-11-15
> **Iowan said:**
> Did you reboot/restart after making changes? Re-check **route**. The multiple (default) gateways will probably be an issue.  There are ways to remove them - if a reboot/restart doesn't do it.

Yes I did. I tried both restarting networking and a complete reboot. No way. Any hint is appreciated. I suspect it is a matter of tuning the conf files.

---

### Post by dejudicibus on 2009-11-15
> **utnubuuser said:**
> I hate to say it, but I've had better luck with wicd instead of the default network manager

I do not know what WICD is. What I do not understand it is why it worked before and now it does not anymore. My understanding is that the only conf files infolved are nsswitch.conf, resolc.cong, smb.conf, interfaces and hosts. Any more?

---

### Post by dejudicibus on 2009-11-17
SOLVED See [URL="http://lindipendente.splinder.com/post/21707535/Solved%3A+Ubuntu+9.10+does+not+s"]article
[/URL]

---

### Post by dejudicibus on 2009-11-17
PS It looks like 9.10 has a lot of troubles. I have now problems with Rythmbox and Gnome Do, but I am not alone. There are a lot of articles about problems when upgrading from 9.04 to 9.10. 9.04 seems much more stable. I would recommend not to upgrade to 9.10 unless strictly necessary if you do not want to spend a lot of time fixing problems.

---

