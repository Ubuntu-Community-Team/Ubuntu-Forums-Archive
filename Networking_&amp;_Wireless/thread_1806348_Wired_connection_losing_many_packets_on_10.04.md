---
title: "Wired connection losing many packets on 10.04"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by testingMySetup on 2011-07-17
Hello, I recently did a fresh install of Ubuntu 10.04. I have been having lots of trouble getting my wired internet to work. I recently switched from a cat5 to a cat5e cable but still did not fix the issue.

I referenced "http://ubuntuforums.org/showthread.php?t=1806215" for help. I have no idea what could be wrong. Any help would be greatly appreciated. Thanks.


SYSTEM INFORMATION:
lspci | grep -i ether
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 50:e5:49:35:fd:49  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe35:fd49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4992 errors:0 dropped:4992 overruns:0 frame:4992
          TX packets:4430 errors:0 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4577192 (4.5 MB)  TX bytes:711899 (711.8 KB)
          Interrupt:29 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7980 (7.9 KB)  TX bytes:7980 (7.9 KB)

[www.google.com]("http://www.google.com")
;; global options: +cmd
;; connection timed out; no servers could be reached


traceroute to [www.google.com]("http://www.google.com") (74.125.224.48), 30 hops max, 60 byte packets
 1  home (192.168.1.254)  5.020 ms  5.003 ms  4.991 ms
 2  bras11-l0.pltnca.sbcglobal.net (151.164.184.67)  17.074 ms  20.907 ms  23.011 ms
 3  64.164.107.1 (64.164.107.1)  23.011 ms  26.762 ms  28.682 ms
 4  bb1-10g2-0.pltnca.sbcglobal.net (151.164.42.100)  30.662 ms  32.574 ms  36.541 ms
 5  ppp-151-164-52-161.rcsntx.swbell.net (151.164.52.161)  40.461 ms  42.818 ms  46.329 ms
 6  gar7.sffca.ip.att.net (12.122.79.97)  48.214 ms  35.411 ms  39.270 ms
 7  cr1.sffca.ip.att.net (12.122.110.118)  43.823 ms  17.253 ms  48.948 ms
 8  cr1.sffca.ip.att.net (12.123.15.109)  21.261 ms  23.084 ms  27.106 ms
 9  cr81.sj2ca.ip.att.net (12.122.1.118)  29.063 ms  35.106 ms  35.079 ms
10  gar4.sn1ca.ip.att.net (12.122.110.61)  35.057 ms  36.801 ms  40.576 ms
11  12.248.108.10 (12.248.108.10)  42.563 ms  44.553 ms  48.641 ms
12  216.239.49.168 (216.239.49.168)  51.032 ms  16.880 ms  19.069 ms
13  64.233.174.15 (64.233.174.15)  20.371 ms  22.138 ms  26.110 ms
14  74.125.224.48 (74.125.224.48)  28.201 ms  30.211 ms  32.033 ms


ethtool -i eth0
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:04:00.0

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

---

### Post by jmoorse on 2011-07-17
Can you post the output of some MTRs for us:

mtr -r [www.google.com](www.google.com)
mtr -r [www.ubuntu.com](www.ubuntu.com)
mtr -r [www.subaru.com](www.subaru.com)

I am concerned about some of the output from your nic:

"dropped:4992 overruns:0 frame:4992"

Perhaps try a different port on the router?

---

### Post by testingMySetup on 2011-07-18
[IMG]http://i52.photobucket.com/albums/g8/protoss1210/Screenshot-1.png[/IMG]

---

### Post by jmoorse on 2011-07-18
Yikes, we are seeing the loss on the first hop.  

Eg: client <> router

Can you try a different port on the router?  Do you have a different nic to try?

---

### Post by testingMySetup on 2011-07-18
Hello, I switched to another port but still I am running into the same packet losses. Is there anything else I can try? Thanks.

---

### Post by jmoorse on 2011-07-18
Different network card, or a different ethernet cable (again).

---

### Post by testingMySetup on 2011-07-18
Hmm, seeing as its a new computer and windows 7x64 works fine I probably won't do that. Maybe I'll have to install some different version of Ubuntu.

---

### Post by jmoorse on 2011-07-18
> **testingMySetup said:**
> Hmm, seeing as its a new computer and windows 7x64 works fine I probably won't do that. Maybe I'll have to install some different version of Ubuntu.

Ahh, the fact that you dual boot would have been good to know.  

Check this out:
[http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168](http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168)

---

### Post by testingMySetup on 2011-07-18
Sorry. I will check that out. I have a "Realtek PCIe GBE Family Controller." Hopefully this works.

---

### Post by jmoorse on 2011-07-18
> **testingMySetup said:**
> Sorry. Does that help the issue any?

Yeah, we can blame the network driver then.  Have you been able to follow the instructions towards the end of the post I linked?

---

### Post by testingMySetup on 2011-07-18
Yes, I followed the instructions and now I can run "mtr -r www.google.com" with 0% loss. I ran 100 ping requests to google and they were 100% success (similar performance to Win7 x64).

Amazing success! Thank you so much for the help:P. I had no idea it was a bad driver on a fresh install.

---

