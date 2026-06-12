---
title: "Speed on Gbit home network"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by blohan on 2011-09-15
i have 2 identical linux servers (compac 7700 ) running Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686) with intel Gig cards, have connected them to an deltaco gig switch with cat6 cables. The NIC's are in 1000tx/full duplex.

Now I been testing to move files beween the servers with FTP and the put/get command to see what speed I get.

The file that I put/get is a little bit over 1MB and it takes about 18-23 sek to copy the file, giving it about  45'-50' kB/s

is this what you can expect on an Gigabit network?


1065353216 bytes received in 20.04 secs (51924.7 kB/s)

1065353216 bytes received in 22.78 secs (45663.0 kB/s)

1065353216 bytes received in 22.78 secs (45663.0 kB/s)

txs / HasseB

---

### Post by SlugSlug on 2011-09-15
This may help
[http://www.t1shopper.com/tools/calculate/downloadcalculator.php](http://www.t1shopper.com/tools/calculate/downloadcalculator.php)

---

### Post by blohan on 2011-09-15
txs for the link


that one give me that the time for 1065353216 bytes on 1000 Mbps GIG E should be 8.52 Seconds and my ftp takes aound 20 sek ???

any ideas why and where to look

---

### Post by haqking on 2011-09-15
> **blohan said:**
> txs for the link


that one give me that the time for 1065353216 bytes on 1000 Mbps GIG E should be 8.52 Seconds and my ftp takes aound 20 sek ???

any ideas why and where to look

do you have ethtool installed ? if not then:

```
sudo apt-get install ethtool
```takes 2 secs then:

```
sudo ethtool eth**x** | grep -i speed
```or simply without ethtool
```

dmesg | grep ethx
```

To check the speed is correct

---

### Post by blohan on 2011-09-15
from srv01 and srv02 


Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbag
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes




hasseb@srv02:~$ sudo ethtool eth0 
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbag
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes






from srv02
hasseb@srv02:~$ sudo ethtool eth0 | grep -i speed
        Speed: 1000Mb/s

---

