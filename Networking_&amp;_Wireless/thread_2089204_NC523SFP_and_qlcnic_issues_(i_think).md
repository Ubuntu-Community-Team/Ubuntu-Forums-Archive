---
title: "NC523SFP and qlcnic issues (i think)"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by pspierce on 2012-11-28
I have a NC523SFP 10Gb 2-port Server Adapter.  The switch's port has been configured; however, there is no activity on the switch nor are there any lights on the card.  I want to say it is something with the switch but I don't have control over that end so need to exhaust as much as possible on my end.


dmesg shows the card being recognized when loading the driver:
[1041450.770297] QLogic 1/10 GbE Converged/Intelligent Ethernet Driver v5.0.28
[1041450.770548] qlcnic 0000:04:00.0: 2MB memory map
[1041451.421716] qlcnic 0000:04:00.0: phy port: 0 switch_mode: 0,
[1041451.421716]        max_tx_q: 1 max_rx_q: 8 min_tx_bw: 0x0,
[1041451.421716]        max_tx_bw: 0x64 max_mtu:0x2580, capabilities: 0xea0fae
[1041451.453659] qlcnic 0000:04:00.0: Supports FW dump capability
[1041451.453661] qlcnic 0000:04:00.0: firmware v4.8.22
[1041451.469631] qlcnic: 2c:27:d7:50:b1:28: NC523SFP 10Gb 2-port Server Adapter Board Chip rev 0x54
[1041451.469778] qlcnic 0000:04:00.0: irq 106 for MSI/MSI-X
[1041451.469788] qlcnic 0000:04:00.0: irq 107 for MSI/MSI-X
[1041451.469803] qlcnic 0000:04:00.0: irq 108 for MSI/MSI-X
[1041451.469812] qlcnic 0000:04:00.0: irq 109 for MSI/MSI-X
[1041451.469835] qlcnic 0000:04:00.0: using msi-x interrupts
[1041451.469998] qlcnic 0000:04:00.0: eth0: XGbE port initialized
[1041451.470195] qlcnic 0000:04:00.1: 2MB memory map
[1041451.485594] qlcnic 0000:04:00.1: phy port: 1 switch_mode: 0,
[1041451.485594]        max_tx_q: 1 max_rx_q: 8 min_tx_bw: 0x0,
[1041451.485594]        max_tx_bw: 0x64 max_mtu:0x2580, capabilities: 0xea0fae
[1041451.517803] qlcnic 0000:04:00.1: Supports FW dump capability
[1041451.517806] qlcnic 0000:04:00.1: firmware v4.8.22
[1041451.533575] qlcnic 0000:04:00.1: irq 110 for MSI/MSI-X
[1041451.533600] qlcnic 0000:04:00.1: irq 111 for MSI/MSI-X
[1041451.533621] qlcnic 0000:04:00.1: irq 112 for MSI/MSI-X
[1041451.533630] qlcnic 0000:04:00.1: irq 113 for MSI/MSI-X
[1041451.533649] qlcnic 0000:04:00.1: using msi-x interrupts
[1041451.569789] qlcnic 0000:04:00.1: eth0: XGbE port initialized

ip link:
17: p1p1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT qlen 1000
    link/ether 2c:27:d7:50:b1:28 brd ff:ff:ff:ff:ff:ff

ethtool p1p1
Settings for p1p1:
        Supported ports: [ TP FIBRE ]
        Supported link modes:   10000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: No
        Advertised link modes:  10000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: Unknown!
        Duplex: Unknown! (255)
        Port: FIBRE
        PHYAD: 0
        Transceiver: external
        Auto-negotiation: off
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000000 (0)
                               
        Link detected: no


ifconfig p1p1
p1p1      Link encap:Ethernet  HWaddr 2c:27:d7:50:b1:28  
          inet addr:172.18.114.14  Bcast:172.18.114.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:106

---

