---
title: "wireless doesnt work in ubuntu 9.10 (lenovo T400)"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by runningpig001 on 2010-04-12
I am a quite freshman about linux and suddenly I am having trouble with my laptop's wireless. It doesnt work after a normal shut down. The version is 9.10 and my computer is lenovo T400.

Below are some outputs of commonds.
```

op@power:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

```

op@power:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:86:a1:62:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```

op@power:~$ ifconfig
other lines deleted.
eth0      Link encap:Ethernet  HWaddr 00:21:86:a1:62:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```

op@power:~$ lshw
WARNING: you should run this program as super-user.
power                     
        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:21:86:a1:62:7a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 multicast=yes
             resources: irq:29 memory:fc000000-fc01ffff memory:fc025000-fc025fff ioport:1840(size=32)
           *-network DISABLED
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:23:4d:dc:2a:f2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f4300000-f430ffff

```

```

op@power:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000001 (1)
Cannot get link status: Operation not permitted

```
```

op@power:~$ sudo ethtool eth0
[sudo] password for op: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: no

```
```

op@power:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:21:86:A1:62:7A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:23:4D:DC:2A:F2

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

```

op@power:~$ cat /etc/NetworkManager/nm-system-settings.conf 
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

So that's all the diagnostics I read in m4443' post . And I dont know what is wrong with mine.
Any suggestions? Thanks!!!

---

### Post by libei.twer on 2010-04-12
Mine doesn't work either. 

Well, to be exact, it worked only at one location (my apartment) and doesn't work anywhere else.

Very sad because of this I have to switch back to Win7.

Not sure if ubuntu 10.4 will fix that.

---

### Post by runningpig001 on 2010-04-12
after reinstalling ubuntu 9.10, it works  


 stupid solution...

---

