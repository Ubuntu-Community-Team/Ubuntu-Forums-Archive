---
title: "Can't get Realtek card to connect to D-Link switch at 1Gb"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by ctcarton on 2010-09-25
I'm hoping someone has had this problem and can tell me what is wrong here.

I have a D-Link DGS-1005D with two machines connected to it.  One has an nVidia ethernet chip and it connects at 1Gb just fine but one has a realtek chip and it cannot connect at 1Gb. On the nVidia side:

```
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)

Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
```

However my other machine, which has a RealTek card does not connect at 1Gb:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

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
```

I've tried swapping ports on the switch but it made no difference.  The nVidia card can connect on any port and the Realtek on none.  I've also tried with a windows OS on the realtek machine and it does not connect at 1Gb either so I don't think this is a linux specific problem, but I'm posting the question here anyway in case anyone has any idea's that can help.

---

### Post by CharlesA on 2010-09-25
Have you tried a different network cable? What model card is it?

---

### Post by ctcarton on 2010-09-27
The network cable was the problem.  Thank you!

---

### Post by Iowan on 2010-09-27
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :)

---

