---
title: "jmc250 gigabit problem"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by The Mighty Orange on 2013-01-07
Hello.

My jmc250 network card seems to have problems with gigabit networks.
Connecting it to a 100mbit network works out off the box.
When connected to a gigabit network it shows "cable unplugged".
Setting the network speed to 100mbit establishes a working 100mbit connection.

I tried several driver version, but none of them worked.

Here is the output off "ethtool -i eth0":

```

driver: jme
version: 1.0.8.4-jmmod
firmware-version: 
bus-info: 0000:05:00.5
supports-statistics: no
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes
supports-priv-flags: no

```"lshw -C network":

```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:68:c9:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-21-generic firmware=N/A ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2a00000-d2a0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:05:00.5
       logical name: eth0
       version: 03
       serial: bc:ae:c5:9d:26:a0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8.4-jmmod duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 memory:d0200000-d0203fff ioport:9100(size=128) ioport:9000(size=256)

```"lspci | grep -i net":

```

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

```

---

### Post by The Mighty Orange on 2013-01-09
Some additional info:
I am running ubuntu 12.10 64 bit, but the same seems to happen on fedora 17 64 bit.
On windows it automatically connects to the switch, but only with a 100mbit speed.

The switch is capable of: 10BASE-T, 100BASE-TX or 1000BASE-T.

I connected another gigabit capable pc to the witch and it works. Conecting the two pcs together says connecting and it doesn't connect.

As seeing on this page [http://www.freebsd.org/cgi/man.cgi?query=jme&sektion=4](http://www.freebsd.org/cgi/man.cgi?query=jme&sektion=4)
it has some issues with 1000BASE-T, and maybe a possible fix, which i don' understand.

Anyone got any idea how to solve this?

---

### Post by flash63 on 2013-01-09
Hello,
a known problem.

JME offers an updated driver version 1.0.8.5 from January 2012.

[ftp://driver.jmicron.com.tw/Ethernet/Linux/](ftp://driver.jmicron.com.tw/Ethernet/Linux/)

Installation:
```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget ftp://driver.jmicron.com.tw/Ethernet/Linux/jmebp-1.0.8.5.tar.bz
tar xvf jmebp-1.0.8.5.tar.bz
cd jmebp-1.0.8.5
make
sudo make install
sudo update-initramfs -u 

```
Restart.

---

### Post by The Mighty Orange on 2013-01-09
Hello flash63,

thank you for your reply.
I tried your procedure, but with no luck. I still get a maximum speed of 100mbit.
I even tried the driver from git and the same happens.

---

### Post by flash63 on 2013-01-09
So it should be a problem with the cables or Ethernet-Port at the switch

> I connected another gigabit capable pc to the witch and it works.

try ethtool
```
sudo apt-get install ethtool
sudo ethtool eth0
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
```

---

### Post by The Mighty Orange on 2013-01-09
> 
So it should be a problem with the cables or Ethernet-Port at the switch


I tried different ports and different cables. Even the port and the cable of the working pc, but still it didn't work.

```

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: yes

```

```

sudo ethtool -s eth0 speed 1000 duplex full autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

```

Without the autoneg off it sets it to 100mbit speed.

---

### Post by flash63 on 2013-01-10
Hmm
```
[COLOR="Red"]Link partner advertised link modes:[/COLOR]  10baseT/Half 10baseT/Full 
                                     100baseT/Half 100baseT/Full 
Link partner advertised pause frame use: Symmetric Receive-only
Link partner advertised auto-negotiation: Yes
Speed: 100Mb/s
```

Which device is currently connected, the Switch? The remote site offers only 100T.

---

### Post by The Mighty Orange on 2013-01-10
It is connected to the gigabit switch(netgear gs105v4).

I connected the jmc250 to the school switch, and got this:

```

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: yes

```

So it actually estabilished a gigabit connection.
At home the jmc250 advertises only 100mbit speed to both the router and the switch.
At school it advertises 1000baset too.

---

### Post by flash63 on 2013-01-10
It seems an incompatibility between the two devices at home or the devices support only Fast Ethernet. Some routers also do not support at all ports Gigabit.

The jmc250 Ethernet card and the driver module is certainly ok.

---

