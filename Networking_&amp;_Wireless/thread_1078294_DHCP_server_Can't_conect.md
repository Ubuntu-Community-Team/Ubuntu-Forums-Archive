---
title: "DHCP server Can't conect"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by f.sivas on 2009-02-23
I have a Dhcp server and a Windows pc, the cliente.
I'm trying to conect to Web or Lan but i can't.

i have internet in the Dhcp server and i can ping the client pc, but i can't do that in the other pc.

Can somebody tell me what else should i do?
My configuration files:

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:15:be:df  
          inet addr:213.22.173.154  Bcast:213.22.173.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe15:bedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:350500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27533928 (27.5 MB)  TX bytes:3681969 (3.6 MB)
          Interrupt:221 

eth2      Link encap:Ethernet  HWaddr 00:11:6b:95:e1:f0  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe95:e1f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53571 (53.5 KB)  TX bytes:10260 (10.2 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:238297 (238.2 KB)  TX bytes:238297 (238.2 KB)


```

```

# vi /etc/network/interfaces
auto lo eth0 eth2
iface lo inet loopback

iface eth0 inet dhcp

iface eth2 inet static
        address 192.168.1.9
        netmask 255.255.255.0

```

```

# vi /etc/network/interfaces
auto lo eth0 eth2
iface lo inet loopback

iface eth0 inet dhcp

iface eth2 inet static
        address 192.168.1.9
        netmask 255.255.255.0

```

```

# vi /etc/dhcp3/dhcpd.conf
ddns-update-style none;
option domain-name "localhost";

option domain-name-servers localhost;

default-lease-time 3600;
max-lease-time 7200;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.250;
  option routers 192.168.1.1;
}

```


```

# vi /etc/dhcp3/dhcp3-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth2"

```

---

### Post by mpokrywka on 2009-02-23
Your dhcp server has internal (LAN) addres 192.168.1.9
Is this server also gateway to internet? (I think it is because it has two network interfaces and one of them has public IP address)

If it is the case then you have misconfigured dhcp3-server:

option routers 192.168.1.1;
should be
**option routers 192.168.1.9;**

also you should add dns servers to serve through dhcp:
check your dns servers by:
**cat /etc/resolv.conf**
and add those IP addresses to dhcp.conf
**option domain-name-servers IP.ADD.RE.SS,IP.ADD.RE.SS;**

I also hope that you configured "internet connection sharing" because it looks like this is what you are trying to do. (ip_forward, MASQUERADE)

---

### Post by f.sivas on 2009-02-24
> **mpokrywka said:**
> 
option routers 192.168.1.1;
should be
**option routers 192.168.1.9;**

also you should add dns servers to serve through dhcp:
check your dns servers by:
**cat /etc/resolv.conf**
and add those IP addresses to dhcp.conf
**option domain-name-servers IP.ADD.RE.SS,IP.ADD.RE.SS;**

Now it's all OK. Thanks

---

