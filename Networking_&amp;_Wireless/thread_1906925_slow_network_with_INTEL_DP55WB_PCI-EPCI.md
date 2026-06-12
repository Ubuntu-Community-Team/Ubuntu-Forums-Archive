---
title: "slow network with INTEL DP55WB PCI-E/PCI"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by maxniki on 2012-01-10
Recently I replaced an old Redhat Server by a new machine installed with the latest Ubuntu Server version. A Samba share is made on the new server. But the transfer of files from the client PC's to the server is about 20 times slower then before. When I transfer the files between two Client PC's in the same network it goes fast.

I'm not an Ubuntu expert, but I did some other installations and never had problems with the network or network cards. Always everything works automatically.

The configuration of the machine is:
motherboard: INTEL DP55WB PCI-E/PCI with onboard network 1Gb
processor: INTEL I7-870 2930 Mhz

I tried some things within ubuntu, but that didn't help. So, I thought, just leave it, disable the onboard network card in de BIOS and put another network card in the machine. I tried two basic network cards (RealteK). I put them in the only PCI-slot in the machine and can see in the BIOS that the machine noticed there is new hardware in the machine. But in Ubuntu the network cards are not found. There is simply no eth0 when I do ifconfig. I think that is strange because normally those cards are automatically visible in Ubuntu.

Any Ideas or suggestions. Is it a hardware problem, a corrupt motherboard or some BIOS setting. I read somewhere that the DP55WB is a unreliable motherboard.

---

### Post by Buntumatic on 2012-01-10
Did you check if onboard Intel NIC was running in 10 Mbit/s mode?
Every new card you add will create a new node, as eth1, eth2, etc.
Unless you edit /etc/udev/rules.d/70-persistent-net.rules and remove references to old cards.
Your hardware choice reminds me desktop, not server. Server should have sufficient CPU - i7 is probably terrible overkill unless you run lots of virtual machines and a quality motherboard which DP55WB is not.
Most of time people replacing their aging servers would be much better off with a used Blade from eBay.

---

### Post by maxniki on 2012-01-10
How can I check if onboard Intel NIC was running in 10 Mbit/s mode? Do I have to check it in the BIOS or in Ubuntu?
 
I did not edit the file you mention. The current content of the file is:
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:69:95:88:ec:27", ATTR{dev_id}=="0x0", ATTR{type}=="1"
, KERNEL=="eth*", NAME="eth0"
 
Note that a new network card does not result in a eth1, eth2, etc. That is exactly one of the two problems. Problem 1 is that the onboard network card is slow. Problem 2 is that additional cards I put in the machine are not recognised by Ubuntu.
 
The hardware of the machine was advised by my hardware vendor. I'm not 100 %sure if I understand what you mean. Do you say that the hardware is not a good choice for Ubuntu server?
 
 
Some additional info. I installed the 32 bits version of Ubuntu server. Can that be the problem.
 
uname -a gives:
Linux boca2 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux
 
ethtool eth0 gives:
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
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 2
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes

---

