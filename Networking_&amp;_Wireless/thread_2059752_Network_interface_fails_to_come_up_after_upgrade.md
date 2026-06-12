---
title: "Network interface fails to come up after upgrade"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by brainswax on 2012-09-18
After upgrading from ubuntu 9.10 to 12.04, networking appears to be broken. During a reboot, I get the following messages:

Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting Server without full networking configuration...

After booting, DNS doesn't work and I get the following error:
```
$ ~$ sudo ifup -v eth4
Configuring interface eth4=eth4 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/bridge
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ip addr add 172.x.y.60/255.255.255.0 broadcast 172.x.y.255    dev eth4 label eth4
RTNETLINK answers: File exists
Failed to bring up eth4.
```Looking in my /etc/network/interfaces file:
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth4
iface eth4 inet static
        address 172.x.y.60
        netmask 255.255.255.0
        network 172.x.y.0
        broadcast 172.x.y.255
        gateway 172.x.y.254

up route add -net 172.x.z.0/24 gw 172.x.z.254
```Here's the lshw output:
```
$ sudo lshw -c network
  *-network:0
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth4
       version: 20
       serial: a4:ba:db:0b:5f:0e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.1.11 duplex=full firmware=5.0.12 bc 5.0.11 NCSI 2.0.5 ip=172.x.y.60 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:36 memory:d4000000-d5ffffff
...

```Here's the output from ifconfig:
```
$ ifconfig eth4
eth4      Link encap:Ethernet  HWaddr a4:ba:db:0b:5f:0e
          inet addr:172.x.y.60  Bcast:172.x.y.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fe0b:5f0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56312 errors:0 dropped:196 overruns:0 frame:0
          TX packets:34389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13042441 (13.0 MB)  TX bytes:3153942 (3.1 MB)
          Interrupt:36 Memory:d4000000-d4012800
```

Also, I am able to ping other IPs on the network, which I verified came from eth4 using tcpdump.

---

### Post by brainswax on 2012-09-18
I used a different Ethernet card and it seems to partially work:

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 172.x.y.60
        netmask 255.255.255.0
        network 172.x.y.0
        broadcast 172.x.y.255
        gateway 172.x.y.254

up route add -net 172.x.z.0/24 gw 172.x.z.254
``````
$ sudo lshw -c network
 *-network:0
       description: Ethernet interface
       product: 82576 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:21:54:7e:c0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=3.2.10-k duplex=full firmware=1.5-1 ip=172.x.y.60 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:ddfc0000-ddfdffff memory:de000000-de3fffff ioport:ecc0(size=32) memory:ddfb8000-ddfbbfff memory:ddc00000-ddc1ffff memory:ddc20000-ddc3ffff

```However, the interface only comes up for a minute or so before it shuts down. It appears that NetworkManager is to blame. A 'sudo pkill -9 NetworkManager' followed by a 'sudo apt-get purge NetworkManager' seems to have solved that.

To summarize, my guess is a combination between driver issues with the Broadcom NetXtreme II BCM5709 Gigabit Ethernet card and with the NetworkManager overriding and breaking my network configuration.

So now I can at least run apt-get to help solve my gnome windows from being busted.

---

