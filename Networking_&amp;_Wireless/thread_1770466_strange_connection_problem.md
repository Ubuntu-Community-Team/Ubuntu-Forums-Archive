---
title: "strange connection problem"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by baarn on 2011-05-29
Hey, 
I'm having some problems getting my wireless adaptors to work.
i'm using a thinkpad t510 with xubuntu

uname -r
```

2.6.38-8-generic

```lspci -v
```

[...]
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f8100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 0777:4f05
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```the first one is built in (wlan0) the second one is in my pc-card-slot (wlan1).
I want both working, atm neither does, so one of them working would be a good start. ;)

my wlan is wpa2-psk and uses static adresses. the network indicator on my panel tells me, that both adaptors are connected, one of the problems might be, that they are using the same IP:

ifconfig:
```

[...]
wlan0     Link encap:Ethernet  HWaddr 00:24:d7:70:04:dc  
          inet addr:192.168.0.206  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:fe70:4dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:399776 errors:0 dropped:6678 overruns:0 frame:0
          TX packets:264259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:455606496 (455.6 MB)  TX bytes:25126535 (25.1 MB)

wlan1     Link encap:Ethernet  HWaddr 00:15:6d:84:76:a7  
          inet addr:192.168.0.206  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:6dff:fe84:76a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65985 errors:0 dropped:6488 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5132596 (5.1 MB)  TX bytes:15238 (15.2 KB)

```i know this is bad, but i dont know how to tell them either to use seperate IPs or to let just one connect (atheros preferred) or to even bond them...
but nevertheless if i disconnect one of them, still no internet...

ok, so i  turned wlan0 off and: 
ping -I wlan1 [www.google.de]("http://www.google.de")
```

PING www.l.google.com (74.125.39.105) from 192.168.0.206 wlan1: 56(84) bytes of data.
64 bytes from fx-in-f105.1e100.net (74.125.39.105): icmp_req=1 ttl=57 time=32.7 ms
64 bytes from 74.125.39.105: icmp_req=2 ttl=57 time=25.2 ms
^C^X64 bytes from 74.125.39.105: icmp_req=3 ttl=56 time=25.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 16039ms
rtt min/avg/max/mdev = 25.255/27.852/32.753/3.467 ms

```so what is my problem now? (when i begun writing i thought i knew it, but now i am confused)
i can't access webpages (in firefox) with wireless adaptor which actually seems to have connection to internet... 

  edit: ok above ping was with eth0 connected, with cable off it looks like this:
ping -I wlan1 [www.google.de]("http://www.google.de") 
```
 
ping: unknown host www.google.de 

```ping -I wlan1 192.168.0.1
```
 
PING 192.168.0.1 (192.168.0.1) from 192.168.0.205 wlan1: 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
22 packets transmitted, 0 received, 100% packet loss, time 21008ms

```

---

### Post by baarn on 2011-05-29
ok, i found out other strange things...

i had no internet aswell when both wlan adaptors were turned off, i fact i needed ethernet and wireless connected to have networking access (i dont know what was wrong there).

what i did to solve the problem was to reconfigure network manager. it was a bit annoying that it didn't manage my wired connections from default, so i though while waiting for a response here i could atleast find a fix for that...

so this should be the fix: (substitute mousepad with fav. editor)
```

sudo mousepad /etc/NetworkManager/NetworkManager.conf

``````

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=[COLOR=Green]true[/COLOR]

```change the last line from false to true and
```

sudo service network-manager start

```to restart the NM


i consider it solved, case closed (atleast for me) ... :D

---

