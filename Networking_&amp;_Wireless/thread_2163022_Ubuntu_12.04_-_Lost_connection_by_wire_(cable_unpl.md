---
title: "Ubuntu 12.04 - Lost connection by wire (cable unplugged)"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by chelazo on 2013-07-16
Hi all, 

I've been using 12.04 for several months, but now I've lost my wired connection. Status bar says "Wired: cable unplugged". Some outputs:

```
[SIZE=2][FONT=arial]chelazo@matraka ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 80:ee:73:2c:58:64  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6222155 (6.2 MB)  TX bytes:6222155 (6.2 MB)

wlan0     Link encap:Ethernet  HWaddr e0:91:53:67:52:cb  
          inet addr:192.168.30.72  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:53ff:fe67:52cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1050782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:511698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369128326 (369.1 MB)  TX bytes:171152594 (171.1 MB)[/FONT][/SIZE]
```

```
chelazo@matraka ~ $ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 80:ee:73:2c:58:64 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether e0:91:53:67:52:cb brd ff:ff:ff:ff:ff:ff

```

```
[FONT=arial]chelazo@matraka ~ $ lspci
.....
02:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
   Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 2020
   Flags: bus master, fast devsel, latency 0, IRQ 48
   Memory at f7d00000 (32-bit, non-prefetchable) [size=16K]
   I/O ports at d100 [size=128]
   I/O ports at d000 [size=256]
   Capabilities: <access denied>
   Kernel driver in use: jme
   Kernel modules: jme
....[/FONT]
```

```
[FONT=arial]chelazo@matraka ~ $ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback[/FONT]
```

```
[FONT=arial]chelazo@matraka ~ $ uname -a
Linux matraka 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
```

I checked the cable and it is working fine. Please help, I will appreciate any comment or clue to see what I am doing wrong. Let me know if any othe output is needed.

Thanks

Chelazo

---

### Post by newbie-user on 2013-07-16
Apparently it's a long-standing bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/880316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/880316)

There's a supposed fix in the comments from Jabba56

---

### Post by chelazo on 2013-07-17
I tried this solution before the first post :(

I am with the last jmicron driver installed (jmebp-1.0.8.5), and the only thing it showed was warning message: "Warning: No support for locale: en_US.utf8", but after rebooting the problem still remained.

Thanks for the reply though!

---

### Post by praseodym on 2013-07-17
Please check
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by chelazo on 2013-07-17
The output:

```
chelazo@matraka ~ $ sudo ethtool eth0
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
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: no


```

Thanks for the reply!

---

### Post by praseodym on 2013-07-18
Link detected: no

Check another cable.

---

### Post by chelazo on 2013-07-19
I inter-changed cables several times with my partners in the office before the first post as well :(

This is something I really dont get: the ethernet jack does not detect there is a cable connected in linux, but in windows (dual boot) it does without any problem.

Please tell me if you see any other thing I can try from this last output, or any other you may want to check.

Thanks for the reply!

---

### Post by praseodym on 2013-07-19
Have a look into your BIOS settings, maybe its not permanently "on" there.

---

### Post by olaf-lederer on 2014-01-28
> [COLOR=#000000]Apparently it's a long-standing bug. [/COLOR][https://bugs.launchpad.net/ubuntu/+s...ux/+bug/880316]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/880316")

[COLOR=#000000]There's a supposed fix in the comments from Jabba56[/COLOR]

The driver update suggested by Jabba56 did the trick, thanks!

---

