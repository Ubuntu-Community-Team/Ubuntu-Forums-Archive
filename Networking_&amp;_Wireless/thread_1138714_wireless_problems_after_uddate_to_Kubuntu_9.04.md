---
title: "wireless problems after uddate to Kubuntu 9.04"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Odeldodel on 2009-04-26
Hello,
i hope someone can help me. I&#7743; new to linux. last week I installed Kubuntu 8.10 und my laptop and after a while i got everything working perfectly.
But on some days ago i got a message that an update is available and I updated to Kubuntu 9.04.
Since then 
- I don't get wireless connection
- The Knetworkmanager is not in the Kickoff-application-starter anymore
-(and the battery-picture in the systray has evaporated)
[SIZE=1][COLOR=Blue]
[/COLOR][/SIZE][SIZE=2][SIZE=1][COLOR=Blue][COLOR=Red]sudo lshw -C network[/COLOR]
[sudo] password for headhunter:                  
  *-network                                      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:23:67:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernetphysical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:d2:0e:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.1 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:83:a4:9d:ca:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/COLOR][/SIZE]
[/SIZE]
[COLOR=Red]
iwconfig[/COLOR]
[COLOR=Blue]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.[/COLOR]




[COLOR=Black]can please someone help me?!

thanks
[/COLOR]

---

### Post by xghstst0riesx on 2009-04-28
> - The Knetworkmanager is not in the Kickoff-application-starter anymore

The network manager applet has been updated in Kubuntu 9.04 and need to be re-added to your panel. There are directions for how to do this on the release notes page: [http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904").

---

