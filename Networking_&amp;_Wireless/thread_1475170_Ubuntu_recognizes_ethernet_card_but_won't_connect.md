---
title: "Ubuntu recognizes ethernet card but won't connect"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by lerwys on 2010-05-06
Hi all,

I own a D-Link DI-604 wired router and I've started getting some issues after Ubuntu 9.10 to 10.04 upgrade(Ubuntu 9.04 used to work OK!).

The problem is that Ubuntu recognizes all my ethernet cards (see below), but I can only connect to the internet through eth1 not eth0 (which is my Windows default). If I try to plug the cable in eth0 nothing happens (at least not in Ubuntu 10.04 and 9.10).

Thanks in advance.

```

lucas@lucas-desktop:~$ sudo lshw -C network
[sudo] password for lucas: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:ea:45:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:d800(size=256) memory:f7effc00-f7effcff
  *-network:1
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth2
       version: 01
       serial: 00:e0:4e:20:49:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full ip=192.168.0.171 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:f7eff800-f7eff8ff ioport:d400(size=256) memory:40000000-4001ffff(prefetchable)
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 10
       serial: 00:e0:7d:ab:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:d000(size=256) memory:f7eff400-f7eff4ff

```

---

### Post by doas777 on 2010-05-06
do they show up in network-manager? also do you have a router, or are you directly connected to ISP equipment?

whats teh output of 
```

cat /etc/network/interfaces

```

---

### Post by lerwys on 2010-05-06
> **doas777 said:**
> do they show up in network-manager? also do you have a router, or are you directly connected to ISP equipment?

whats teh output of 
```

cat /etc/network/interfaces

```

Hi,

Yes, they all show in network-manager and I have a router (D-Link DI-604) to share the connection with other computer.

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

```

Thanks for replying!

---

### Post by lerwys on 2010-05-07
Does anyone got any ideas?

Thanks

---

### Post by doas777 on 2010-05-07
> **lerwys said:**
> Hi,

Yes, they all show in network-manager and I have a router (D-Link DI-604) to share the connection with other computer.

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

```Thanks for replying!

add a like like so:
```
auto eth0
iface eth0 inet manual
```
save the file and restart networking with ;
```
sudo /etc/init.d/networking restart
```.
or just reboot.

I've never seen 'manual' in an iface line, but perhaps it's new. I usually use either 'DHCP' or 'static'. 

sorry I didn;t get back to you earlier, but was occupied last night. 
let us know how it works.

---

### Post by lerwys on 2010-05-07
Ok! and no problem!

I will do it as soon as I get back home.

Thanks again!

---

### Post by lerwys on 2010-05-07
Hi!

Here's what I got by adding those two lines and restarting:

```

lucas@lucas-desktop:~$ sudo vim /etc/network/interfaces
lucas@lucas-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
                                                                         [ OK ]

```

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

auto eth0
iface eth0 inet manual

```

Was these two last lines you meant before?

Still no connection.

---

### Post by doas777 on 2010-05-07
yeah, thats it. 

so what do you get now from 
```
sudo ifconfig
```also how do you get your IPs? static or DHCP?

---

### Post by lerwys on 2010-05-07
```

lucas@lucas-desktop:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:e0:7d:ab:f0:3c  
          inet6 addr: fe80::2e0:7dff:feab:f03c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1188 (1.1 KB)
          Interrupt:20 Base address:0xd000 

eth2      Link encap:Ethernet  HWaddr 00:e0:4e:20:49:b6  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4eff:fe20:49b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9941844 (9.9 MB)  TX bytes:2099619 (2.0 MB)
          Interrupt:21 Memory:f7eff800-f7eff8ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31776 (31.7 KB)  TX bytes:31776 (31.7 KB)

```

It appears now that eth0 is gone... =]

Also I get my IP through DHCP, but I'm using a router. Could it be a config problem in router?

---

### Post by doas777 on 2010-05-07
> **lerwys said:**
> ```

lucas@lucas-desktop:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:e0:7d:ab:f0:3c  
          inet6 addr: fe80::2e0:7dff:feab:f03c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1188 (1.1 KB)
          Interrupt:20 Base address:0xd000 

eth2      Link encap:Ethernet  HWaddr 00:e0:4e:20:49:b6  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4eff:fe20:49b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9941844 (9.9 MB)  TX bytes:2099619 (2.0 MB)
          Interrupt:21 Memory:f7eff800-f7eff8ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31776 (31.7 KB)  TX bytes:31776 (31.7 KB)

```It appears now that eth0 is gone... =]

Also I get my IP through DHCP, but I'm using a router. Could it be a config problem in router?

the router is probably fine if it is working for windows and for Eth1

it actually appears like your system is pushing each of the nics up one (eth0 => eht1, eth1=>eth2, etc). you only have 2 NICs right? if so, you may want to write down the MAC, and compare it with the MACs in windows to see if they are offset. that may be useful to know.  

anyway, since you use DHCP, try chaning the eth0 iface line in your interfaces file to this:
```

iface eth0 inet DHCP

```

and restart networking again. 

your lshw output looks a little weird. interfaces 1 and 3 report as realtek 8139's as does the 2nd, but the second one is made by a differant vendor (differant vendor name and highorder field in the MAC).  the first nic is reporting that its size is only 10mb/s.

so which of these are your physical nics, and which is for the dsl connection?

---

### Post by lerwys on 2010-05-07
Well... I got an error after changing "manual" to "DHCP" and tried to restart the connection.

```

lucas@lucas-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:14: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:14: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

```

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces

iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

auto eth0
iface eth0 inet DHCP 

```

In fact, I have three NICs: 1 is my onboard network (which I never use) and the other two are NIC connected to PCI bus. One last thing is that I ran "sudo lshw -C network" and look I got:

```

lucas@lucas-desktop:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:ea:45:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:d800(size=256) memory:f7effc00-f7effcff
  *-network:1
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth2
       version: 01
       serial: 00:e0:4e:20:49:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full ip=192.168.0.171 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:f7eff800-f7eff8ff ioport:d400(size=256) memory:40000000-4001ffff(prefetchable)
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 10
       serial: 00:e0:7d:ab:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:d000(size=256) memory:f7eff400-f7eff4ff

```

It says "-network:0 DISABLED". Was it suppose to happen?

---

### Post by doas777 on 2010-05-07
no not really. 
it appears that the interfaces file has changed a good deal from the last version. 

well, lets try removing the eth0 iface line (but leave teh 'auto eth0') line and see what that does to lshw, ifconfig, and network-manager. 

after that try running 
```
sudo ethtool eth0
```
so we can see if it is a cabling or nic driver setting issue.

---

### Post by lerwys on 2010-05-07
Here:

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces

iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

auto eth0

```

```

lucas@lucas-desktop:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:ea:45:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:d800(size=256) memory:f7effc00-f7effcff
  *-network:1
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth2
       version: 01
       serial: 00:e0:4e:20:49:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full ip=192.168.0.171 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:f7eff800-f7eff8ff ioport:d400(size=256) memory:40000000-4001ffff(prefetchable)
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 10
       serial: 00:e0:7d:ab:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:d000(size=256) memory:f7eff400-f7eff4ff

```

```

lucas@lucas-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:e0:7d:ab:f0:3c  
          inet6 addr: fe80::2e0:7dff:feab:f03c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1188 (1.1 KB)
          Interrupt:20 Base address:0xd000 

eth2      Link encap:Ethernet  HWaddr 00:e0:4e:20:49:b6  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4eff:fe20:49b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38251967 (38.2 MB)  TX bytes:4675793 (4.6 MB)
          Interrupt:21 Memory:f7eff800-f7eff8ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31776 (31.7 KB)  TX bytes:31776 (31.7 KB)

```

```

lucas@lucas-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

```

---

### Post by doas777 on 2010-05-07
ok, well it shows the network cable unplugged on eth0, so that is why it is reporting 10mb half dup. 

go ahead and remove the auto eth0 line from your interfaces as it appears that whole route is a dead end. then reboot and check lshw to see if the device is still disabled.

---

### Post by lerwys on 2010-05-07
```

lucas@lucas-desktop:~$ cat /etc/network/interfaces

iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

```

```

lucas@lucas-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /usr/bin/poff: No pppd is running.  None stopped.
Ignoring unknown interface eth0=eth0.
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

```

```

lucas@lucas-desktop:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:ea:45:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:d800(size=256) memory:f7effc00-f7effcff
  *-network:1
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth2
       version: 01
       serial: 00:e0:4e:20:49:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full ip=192.168.0.171 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:f7eff800-f7eff8ff ioport:d400(size=256) memory:40000000-4001ffff(prefetchable)
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 10
       serial: 00:e0:7d:ab:f0:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:d000(size=256) memory:f7eff400-f7eff4ff

```

It appears eth0 is still disabled. What should I do now?

---

### Post by doas777 on 2010-05-08
what do you get from 
```
ifconfig eth0 up
```?

this thread seems very similar to your issue.
[http://ubuntuforums.org/showthread.php?t=327417](http://ubuntuforums.org/showthread.php?t=327417)
[http://www.linuxquestions.org/questions/ubuntu-63/network-device-name-595024/](http://www.linuxquestions.org/questions/ubuntu-63/network-device-name-595024/)

btw, it looks like I screwed up with the upper case DHCP in the interfaces file. it should be lower. sry bout that. I should have confirmed it first.

if the interface does come up, the op solved his issue, by putting in both the auto and iface lines (correctly cased).

---

### Post by lerwys on 2010-05-08
Hi!

It appears we're in the right way (=]), but interface eth0 did not connect:

changed the /network/interfaces

```

lucas@lucas-desktop:~$ cat /etc/network/interfaces

iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

auto eth0
iface eth0 inet dhcp

```ifconfig
```

lucas@lucas-desktop:~$ sudo ifconfig eth0 up
[sudo] password for lucas: 

```and restarted
```

lucas@lucas-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1177
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:d4:ea:45:b4
Sending on   LPF/eth0/00:13:d4:ea:45:b4
Sending on   Socket/fallback
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:d4:ea:45:b4
Sending on   LPF/eth0/00:13:d4:ea:45:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```at last, I ran ifconfig again and look eth0 (it appears active now, but no connection yet)

```

lucas@lucas-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:ea:45:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:e0:7d:ab:f0:3c  
          inet6 addr: fe80::2e0:7dff:feab:f03c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1428 (1.4 KB)
          Interrupt:20 Base address:0xd000 

eth2      Link encap:Ethernet  HWaddr 00:e0:4e:20:49:b6  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4eff:fe20:49b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:907917 (907.9 KB)  TX bytes:242815 (242.8 KB)
          Interrupt:21 Memory:f7eff800-f7eff8ff 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:d4:ea:45:b4  
          inet addr:169.254.10.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41200 (41.2 KB)  TX bytes:41200 (41.2 KB)

```(noob question probably) why do I have two eth0 interfaces now (sorry for the dumb question)?

---

### Post by doas777 on 2010-05-10
well, I can easily explain the 'eth0: avahi' part, but I'm not sure why eth0 is not recieving a DHCP response.

avahi is an autoconfiguration service for IP that, IMO is more trouble than it is worth. it's jsut a software interface though so you can just ignore it. 

as for the dhcp, 
what do you get when you enter:
```
dhclient eth0
```

and what do you get from:
```

sudo ethtool eth0

``` now? 

just to confirm, the cable attached to eth0, is directly connected to your router/dhcp server right?

---

### Post by marianlibrarian on 2010-05-10
Hmmm...
This sounds similar to my problem. Only I am using a WUSB54GC. It shows up in my network manager that is running on my windows machine but says that it is off line or now powered on.

I checked the interfaces file:
sudo gedit /etc/network/interfaces

and the following is what is in the file:
auto lo
iface lo inet loopback

It seems that there should be more to this?

---

### Post by lerwys on 2010-05-10
```

lucas@lucas-desktop:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

```

```

lucas@lucas-desktop:~$ sudo ethtool eth0
[sudo] password for lucas: 
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

```

And Yes. The cable is attached directly to the router.

---

### Post by doas777 on 2010-05-10
> **lerwys said:**
> ```

lucas@lucas-desktop:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

``````

lucas@lucas-desktop:~$ sudo ethtool eth0
[sudo] password for lucas: 
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

```And Yes. The cable is attached directly to the router.

sry, I should have had you run the dhcpclient command as root, but it would make no differance based on your ethtool output. note the bottom line; it believes that there is no cable plugged in. can you confirm that you are wired up, and that the nic lights come on when it is plugged in?

---

### Post by lerwys on 2010-05-10
Sorry about that. You are quite right. Before I was able to send the message I had to change the cable to the other NIC (the functional one eth2). Just after that I ran the commands (I don't know why) and posted its outputs. Sorry again. Here comes the right output:

```

lucas@lucas-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1427
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:d4:ea:45:b4
Sending on   LPF/eth0/00:13:d4:ea:45:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

lucas@lucas-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

```

---

### Post by doas777 on 2010-05-11
hmmmm,

until we see ethtool spitting out 'Link Detected: yes' we probably won't be able to get it working. have you tried plugging into eth0, and then fully rebooting? when you do, does ethtool still say that there is no link detected? I'm also worried that it claims the card is in 10mb/s half duplex mode. I assume you have a 100mbps swich on your router, right?

---

### Post by lerwys on 2010-05-11
Well. I've done what you said, but nothing happened.... 

What should I do next? =]

---

### Post by doas777 on 2010-05-11
> **lerwys said:**
> Well. I've done what you said, but nothing happened.... 

What should I do next? =]
are there lights on, on the router port and the nic port where you plugged the cable in? if you run 'sudo ethtool eth0' again, does it still report the card's 'link detected' as no?

I'm starting to run out of ideas on this. I'd have you troubleshoot DHCP were the card recognising the link, but I keep thinking of hardware solutions that don't track since you say it works fine in windows.

---

### Post by lerwys on 2010-05-11
There lights are on, both NIC and Router. The strange thing is that it used to work well on Ubuntu 9.04. When I upgraded to 9.10 (and 10.04 later) it just stopped working. I don't know what to do either.

Anyway, thank you very much for all the information you gave me!

---

