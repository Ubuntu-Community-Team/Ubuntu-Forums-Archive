---
title: "Thinkpad t40 wireless connection problem with 9.04 Jaunty"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by TheCAG on 2009-04-30
I have an IBM T40 Thinkpad laptop which I just upgraded to Ubuntu 9.04. I am unable to get my wireless connection working. I have had a lot of problems with my built in AIRONET Wireless Cisco 802.11b wifi card in the past so I started using a Netgear Artheros AR5001x Wireless Network Adapter. It is PCMCIA card model WG511T. I am using WEP encryption. This was working reasonably well (not great but it worked) under Ibex 8.10 but when I recently upgraded to 9.04 it stopped working. 

When I try to connect to my wireless network, I am able to see the network but I am unable to connect to it. The NetworkManager icon just spins and spins. 

I recently purchased another wireless card because I read somewhere that the Ath9k driver would work with it. It is a D-Link System AR5008 Wireless Network adapter. It is also a PCMCIA card model DWA-642. This card exhibits the same problem as the others. 

Any suggestions would be greatly appreciated.

Here is the output of from the following command when using the Netgear wireless card.

TheCAG@TheCAG-laptop:~$ sudo lshw -C network
  *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network:0
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:5e:d8:f6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.80.250 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:de:6b:18
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 module=airo multicast=yes wireless=IEEE 802.11-DS
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi1
       version: 01
       serial: 00:1e:2a:53:3d:9c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:dd:c8:a6:e7:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by andersja on 2009-06-22
If this is still not working I would recommend you file a bug at the official Ubuntu bug tracker at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux]("https://bugs.launchpad.net/ubuntu/+source/linux")

If you tag it "jaunty-regression" developers are more likely to have a look...

---

