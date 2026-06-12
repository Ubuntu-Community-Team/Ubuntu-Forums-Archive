---
title: "ubuntu server: wlan  fails"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by alex1974 on 2013-04-08
Dear community,

I have set up an ubuntu server 12.04 LTS.  Without changing any settings the wlan fails since a few days.

The server is running ubuntu server 12.04 with dnsmasq and hostapd.
From the server I can ping both wan and wlan. I can dig both wan and wlan. I get no error message from dnsmasq nor hostapd. For testing purposes the iptables is wide open.

From the laptop I can ping and ssh the server. I can dig [www.ubuntuforums.org]("http://www.ubuntuforums.org") from the laptop and get an answer. But trying to open a website fails. I tried with Opera and Chrome with two laptops and my android mobile.

Any hint?

**8.4.2013 20:30**

Please it's rather urgent. Nobody out there who can help?

---

### Post by alex1974 on 2013-04-08
from the iptables script
```

...
# eth/wlan forward - NAT
$IPT -t nat -I PREROUTING 1 -s 192.168.3.0/24 -j LOG --log-prefix 'IPTABLES ICMP (PREROUTING): '
$IPT -t filter -I FORWARD 1 -s 192.168.3.0/24 -j LOG --log-prefix 'IPTABLES ICMP (FORWARD): '
$IPT -t nat -I POSTROUTING 1 -s 192.168.3.0/24 -j LOG --log-prefix 'IPTABLES ICMP (POSTROUTING): '
$IPT -A FORWARD -o $WAN -i $WLAN -s 192.168.3.0/24 -m conntrack --ctstate NEW -j ACCEPT
$IPT -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE
sysctl -w net.ipv4.ip_forward=1
...

```

```

alex@server:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
LOG        all  --  192.168.3.0/24       anywhere             LOG level warning prefix "IPTABLES ICMP (FORWARD): "
ACCEPT     all  --  192.168.3.0/24       anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

```

```

 alex@server:~$ sudo iptables -v -L -t nat
Chain PREROUTING (policy ACCEPT 168K packets, 12M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 144K 9188K LOG        all  --  any    any     192.168.3.0/24       anywhere             LOG level warning prefix "IPTABLES ICMP (PREROUTING): "

Chain INPUT (policy ACCEPT 167K packets, 12M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 5718 packets, 492K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1046 packets, 77703 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  871 68203 LOG        all  --  any    any     192.168.3.0/24       anywhere             LOG level warning prefix "IPTABLES ICMP (POSTROUTING): "
  5367  461K MASQUERADE  all  --  any    eth     anywhere             anywhere            

```

---

### Post by alex1974 on 2013-04-09
Is there anybody who can help?
I tried reinstalling the wireless driver but still the same problem.

---

### Post by ahallubuntu on 2013-04-09
~

---

### Post by alex1974 on 2013-04-09
```
alex@server:~$ sudo lshw -C network
[sudo] password for alex: 
  *-network               
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan
       version: 01
       serial: 64:70:02:d2:65:a0
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-26-generic firmware=N/A ip=192.168.3.1 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7e00000-f7e0ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth
       version: 10
       serial: 94:de:80:05:9d:10
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.2 duplex=full firmware=N/A ip=213.47.124.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:f7d00000-f7d3ffff ioport:e000(size=128)
alex@server:~$ sudo iwconfig
tun0      no wireless extensions.

wlan      IEEE 802.11bgn  Mode:Master  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth       no wireless extensions.

lo        no wireless extensions.

mon.wlan  IEEE 802.11bgn  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

### Post by ahallubuntu on 2013-04-09
~

---

### Post by alex1974 on 2013-04-09
The logs show that the athk was updated a few days ago. Before this the wireless worked like a charm out of the box. But still the wlan is up and I can reach the server. So doesn't that mean the driver is working.
Btw hw encryption is off.

---

