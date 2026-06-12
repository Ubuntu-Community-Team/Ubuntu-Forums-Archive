---
title: "Ethernet / DHCP(?) trouble"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by aioobe on 2010-11-04
Have a strange problem with my wired network interface. Here goes:

1. I plug in the cable.

2. Both diodes light up (one green / one orange) and `dmesg` gives

        [   66.847512] tg3: eth0: Link is up at 1000 Mbps, full duplex.
        [   66.847516] tg3: eth0: Flow control is off for TX and off for RX.

3. `nm-applet` (network-management gnome applet) icon starts spinning, but gives up after a while.

4. I terminate the `nm-applet` and try `dhclient eth0` instead. This gives:

```
        $ sudo dhclient eth0
        Internet Systems Consortium DHCP Client V3.1.2
        Copyright 2004-2008 Internet Systems Consortium.
        All rights reserved.
        For info, please visit http://www.isc.org/sw/dhcp/
        
        Listening on LPF/eth0/00:16:d3:30:9e:73
        Sending on   LPF/eth0/00:16:d3:30:9e:73
        Sending on   Socket/fallback
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
        ...
```

5. I thought it might be a hardware problem so I booted on a BSD usb-stick and I can ping fine back and forth.

6. Back in Linux I tried with a USB-ethernet dongle, same result. Tried three different ethernet-connections. Same issue everywhere.

This is what `ifconfig eth0` gives when I've plugged in the cable:

```
    $ ifconfig eth0
    eth0      Link encap:Ethernet  HWaddr 00:16:d3:30:9e:73  
              inet6 addr: 2001:6b0:1:1de0:216:d3ff:fe30:9e73/64 Scope:Global
              inet6 addr: fe80::216:d3ff:fe30:9e73/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1056 errors:0 dropped:0 overruns:0 frame:0
              TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:244082 (244.0 KB)  TX bytes:4998 (4.9 KB)
              Interrupt:16 
```

What could the problem be?


----------


Update: Some extra information that may or may not be useful:

```
    $ sudo mii-tool -v
    eth0: negotiated 1000baseT-FD flow-control, link ok
      product info: vendor 00:08:18, model 24 rev 0
      basic mode:   autonegotiation enabled
      basic status: autonegotiation complete, link ok
      capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
      advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
      link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
```...and...

```
    $ sudo ethtool eth0
    Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes

```Wireless works just fine.

(This question has also been posted at [http://serverfault.com/questions/198058/ethernet-dhcp-trouble-on-linux](http://serverfault.com/questions/198058/ethernet-dhcp-trouble-on-linux))

---

### Post by Peter09 on 2010-11-04
Don't see any IP address has been allocated in any of that.
 
What is the output of the terminal command
 
```
route
```

---

### Post by aioobe on 2010-11-04
With Wifi connected, I get
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
130.237.222.0   *               255.255.255.0   U     0      0        0 eth0
130.229.128.0   *               255.255.224.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         130.229.128.1   0.0.0.0         UG    0      0        0 wlan0

```

Without wifi, (and a failed dhclient attempt) it looks like

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by Peter09 on 2010-11-04
I note this
 
> $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
130.237.222.0   *               [COLOR=red]255.255.255.0[/COLOR]   U     0      0        0 eth0
130.229.128.0   *               [COLOR=royalblue]255.255.224.0[/COLOR]   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         130.229.128.1   0.0.0.0         UG    0      0        0 wlan0
 
Your eth0 interface appears to have a different mask to your wlan0 interface, are you linking to different subnets?

---

### Post by aioobe on 2010-11-04
Yes, it seems so. According to my colleague, this is as it should be.

He actually opened up wireshark and saw that my DHCP-discover packages was sent, and that I actually received a response. However, the response was a "relay"-response which my computer apparently didn't pick up correctly :-(  he suggested to me that I try changing dhcpcd version...

---

### Post by Peter09 on 2010-11-04
I think Syslog should show any responses to DHCP.

---

