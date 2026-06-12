---
title: "pppoe seems ok but....."
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by SiriusTux on 2009-11-07
I'm just try to make my pppoe connection working with my local dsl-provider in Italy but I can't find where I do wrong.
I connect to my wireless modem with interface wlan0 and I receive from DHCP server a private address (192.168.1.166 from network 192.168.1.0/24). I configured pppoe with command:

```
sudo pppoeconf
```

when wlan0 is connect I start pppoe with the command:

```
pon dsl-proveder
```
 
everything seems to be ok, because ppp0 interface goes up, as one can see from the output of the command:

```

stefano@stefano-laptop:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:79.24.116.67  P-t-P:192.168.100.1 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:54 (54.0 B)
```

also routing seems to be right, netstat command gives the following output:

```
stefano@stefano-laptop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.100.1   *               255.255.255.255 UH        0 0          0 ppp0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
default         *               0.0.0.0         U         0 0          0 ppp0
```

Can anyone find where I'm wrong, because I cannot browse Internet with Firefox.
Thanx everyone

SiriusTux

---

### Post by Iowan on 2009-11-08
I haven't used **netstat** much - relying instead on **route** for routing information.  I notice there is no default gateway listed in your results.

---

