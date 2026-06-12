---
title: "cant get SiS900 wired ethernet to work"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by bambam511 on 2010-06-13
laptop: averatec 6200 series
ethernet driver: SiS 900
wirless lan driver: rt2500

I got 10.04 installed and running pretty well.I cant get the wired ethernet to work but the wireless works. i did the the command line

 lspci -v | less


as recommeded here 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

which gave me this for the wired lan (i think lol)

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Micro-Star International Co., Ltd. Device 0041
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d800 [size=256]
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sis900
        Kernel modules: sis900

and the wireless 
00:0e.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Device 6833
        Flags: bus master, slow devsel, latency 64, IRQ 10
        Memory at cfffa000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: rt2500pci
        Kernel modules: rt2500pci


im stumped...still a newbie but in the learning process...sry for the dumb questions but.......:p

also, dont know if i matters but ive got 8mbps/1.5mbps cable (motorala surfboard cable modem) and a linksys wrt54g wireless router.

---

### Post by bambam511 on 2010-06-14
el bumpo:p

---

### Post by warfacegod on 2010-06-14
Stupid question: Why are you using wireless documentation to get your wired connection working?

---

### Post by bambam511 on 2010-06-14
which gave me this for the wired lan (i think lol)

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI  Fast Ethernet (rev 91)
        Subsystem: Micro-Star International Co., Ltd. Device 0041
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d800 [size=256]
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sis900
        Kernel modules: sis900


that is the wired info. thought maybe since the wireless is working and the wired isnt, the wireless info my contain some info on why that is so...least that was my line of thinking after 6hrs of messing with it..lol....:p

---

### Post by warfacegod on 2010-06-14
Right click the Network icon on your Panel and make sure Networking is enabled.

If my memory serves, Ubuntu will only use one connection if wired and wireless are both present, disabling the other. Try disabling wireless.

---

