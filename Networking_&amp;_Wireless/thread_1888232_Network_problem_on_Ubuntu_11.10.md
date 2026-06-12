---
title: "Network problem on Ubuntu 11.10"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by JoeBahr on 2011-11-28
Hi Guys, 

just wanted to check if someone can help here. 
I did an upgrade of my Ubuntu server today and it ended up with network issues. 

here are the message i was seeing in the different logs : 

in dmesg : 
```
 dmesg | grep -e eth -e ipw
[    1.466604] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.467447] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.467464] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.530031] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:68:64:76:4f
[    1.530042] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[   15.980500] forcedeth 0000:00:0a.0: eth0: link down
[   26.192030] eth0: no IPv6 routers present
[  478.442309] forcedeth 0000:00:0a.0: eth0: link up
[  832.518817] forcedeth 0000:00:0a.0: eth0: link down
[  835.421232] forcedeth 0000:00:0a.0: eth0: link up
[  839.628461] forcedeth 0000:00:0a.0: eth0: link down
[  841.943888] forcedeth 0000:00:0a.0: eth0: link up
[  843.307022] forcedeth 0000:00:0a.0: eth0: link down
[  848.488510] forcedeth 0000:00:0a.0: eth0: link up
[  852.652244] forcedeth 0000:00:0a.0: eth0: link down
[  854.945595] forcedeth 0000:00:0a.0: eth0: link up
[  859.090764] forcedeth 0000:00:0a.0: eth0: link down
[  861.614547] forcedeth 0000:00:0a.0: eth0: link up
[  865.864822] forcedeth 0000:00:0a.0: eth0: link down
[  868.200092] forcedeth 0000:00:0a.0: eth0: link up
[  872.387216] forcedeth 0000:00:0a.0: eth0: link down
[  874.743186] forcedeth 0000:00:0a.0: eth0: link up
[  878.972558] forcedeth 0000:00:0a.0: eth0: link down
[  881.285736] forcedeth 0000:00:0a.0: eth0: link up
[  885.429424] forcedeth 0000:00:0a.0: eth0: link down
[  887.765905] forcedeth 0000:00:0a.0: eth0: link up
[  892.140550] forcedeth 0000:00:0a.0: eth0: link down
[  894.457873] forcedeth 0000:00:0a.0: eth0: link up
[  898.600054] forcedeth 0000:00:0a.0: eth0: link down
[  900.915490] forcedeth 0000:00:0a.0: eth0: link up
```

in syslog :
```
Nov 29 01:57:31 lafouine NetworkManager[769]: <info> (eth0): carrier now OFF (device state 10)
Nov 29 01:57:31 lafouine kernel: [  885.429424] forcedeth 0000:00:0a.0: eth0: link down
Nov 29 01:57:33 lafouine NetworkManager[769]: <info> (eth0): carrier now ON (device state 10)
Nov 29 01:57:33 lafouine kernel: [  887.765905] forcedeth 0000:00:0a.0: eth0: link up
Nov 29 01:57:37 lafouine NetworkManager[769]: <info> (eth0): carrier now OFF (device state 10)
Nov 29 01:57:37 lafouine kernel: [  892.140550] forcedeth 0000:00:0a.0: eth0: link down
Nov 29 01:57:40 lafouine NetworkManager[769]: <info> (eth0): carrier now ON (device state 10)
Nov 29 01:57:40 lafouine kernel: [  894.457873] forcedeth 0000:00:0a.0: eth0: link up
Nov 29 01:57:44 lafouine NetworkManager[769]: <info> (eth0): carrier now OFF (device state 10)
Nov 29 01:57:44 lafouine kernel: [  898.600054] forcedeth 0000:00:0a.0: eth0: link down
Nov 29 01:57:46 lafouine NetworkManager[769]: <info> (eth0): carrier now ON (device state 10)
```

after long research and couple manipulations between 2 switches, I figure out that it was an issue on the NIC driver. 

When I plugg it onto a 100 Meg switch it is working nicely. When i plugg it into a gigabit switch, it is not able to negotiate speed and duplex anymore (since the last update). 

Now I have this working as follow (on a gigabit switch i had to force it to 100 F/D)
```
ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: off
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes
```

I've used ethtool (apt-get install ethtool) to force the configuration : 
to see the configuration status of your interface
*ethtool eth0*

to force it to 100 F/D
[I]ethtool -s eth0 autoneg off
ethtool -s eth0 duplex full
ethtool -s eth0 speed 100[/I]

---

### Post by praseodym on 2011-11-29
Hi,

NVIDIA-Gigabit cards often need additional module parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```

and reboot.

---

