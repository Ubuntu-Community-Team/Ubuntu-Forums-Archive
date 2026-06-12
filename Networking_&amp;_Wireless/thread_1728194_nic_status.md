---
title: "nic status"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by ipfreak on 2011-04-13
hi all:

how to identify the status of the ethernet interafces? on my machine, every interface shows "UP" nn matter the interface is connected or not:

UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

thanks

---

### Post by Cheesehead on 2011-04-13
Well, if you can ping a remote machine over an interface, then it's connected.

Are you sure you are asking the right question? Is that really all you wanted to know? Or did you intend to ask for help to diagnose a connection problem? If so, then we'll need much more information...like the symptoms.

---

### Post by ipfreak on 2011-04-14
> **Cheesehead said:**
> Well, if you can ping a remote machine over an interface, then it's connected.

Are you sure you are asking the right question? Is that really all you wanted to know? Or did you intend to ask for help to diagnose a connection problem? If so, then we'll need much more information...like the symptoms.

   thanks. guess i didn't phrase the question right.    

on ubuntu, every ethernet interface start its name in "eth". i have five interfaces on that machine and only two is connected. when i use command "ifconfig", under every interface i have this: 

eth5    Link encap:Ethernet  HWaddr 00:15:17:e7:b7:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x9f00 Memory:fd9e0000-fda00000 

how could i know it is an active interface or not?  

at this moment i am using ethtool to identify the active interface. 

i am wondering why not "ifconfig ethx" gives me that information. freebsd does:

user@freebsd:~:$ ifconfig 
bge0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> metric 0 mtu 1500
        options=8009b<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,VLAN_HWCSUM,LINKSTATE>
        ether 00:12:3f:1f:21:c2
        inet 192.168.1.128 netmask 0xffffff00 broadcast 192.168.1.255
        inet6 fe80::212:3fff:fe1f:21c2%bge0 prefixlen 64 scopeid 0x1 
        nd6 options=3<PERFORMNUD,ACCEPT_RTADV>
        media: Ethernet autoselect (100baseTX <full-duplex>)
        status: active

---

### Post by uncaspi on 2011-04-14
You cannot see it with ifconfig but use sudo netstat -i

---

### Post by Cheesehead on 2011-05-05
Easy ways to tell if an interface is connected:
1) If using dhcp, it has received an IP address.
2) TX and RX activity is greater than zero.
```
eth0    Link encap:Ethernet  HWaddr 00:23:5a:94:49:c3  
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000 
        RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        Interrupt:42 

eth1    Link encap:Ethernet  HWaddr 00:24:2c:7c:6b:7a  
[B]        inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: fe80::224:2cff:fe7c:6b7a/64 Scope:Link[/B]
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        **RX packets:7738112** errors:0 dropped:0 overruns:0 frame:0
        **TX packets:6503359** errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000 
        **RX bytes:3720824705 (3.7 GB)  TX bytes:1458263937 (1.4 GB)**

```

---

