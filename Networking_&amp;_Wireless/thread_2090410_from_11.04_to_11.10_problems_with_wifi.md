---
title: "from 11.04 to 11.10 problems with wifi"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by wiligelmo on 2012-12-02
Hi,
i upgraded ubuntu from 11.04 to 11.10 and wifi is not working anymore. my pc is connected to a router.
Now Internet is working just with ethernet. 
i've got a Atheros card.
on the menu bar on the top, the wifi icon disappeared. and the wifi connection disappeared as well.
in "additional driver" the list is empty.

this is the result for** ifconfig**:
```
marconicole@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:c7:9e:74  
          indirizzo inet:192.168.1.3  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::e2cb:4eff:fec7:9e74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13305 errors:0 dropped:0 overruns:0 carrier:2
          collisioni:0 txqueuelen:1000 
          Byte RX:11762552 (11.7 MB)  Byte TX:2127781 (2.1 MB)
          Interrupt:44 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:740 (740.0 B)  Byte TX:740 (740.0 B)
```

I've already read a lot of threads and surfed on internet without finding a solution. I hope someone will help me. Thanks in advance.

---

### Post by 2F4U on 2012-12-02
Without any information about your wireless hardware you won't get much support.

---

### Post by wiligelmo on 2012-12-02
I've got a router Digicom adsl2/2+ wireless router. It's a Michelangelo Wave 54C router.

this is the result for **sudo lshw -C network**:
```
marconicole@desktop:~$ sudo lshw -C network
[sudo] password for marconicole: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: e0:cb:4e:c7:9e:74
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=ATL1E  driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.3  latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)
```

which others information could i give you?
thanks!!

---

