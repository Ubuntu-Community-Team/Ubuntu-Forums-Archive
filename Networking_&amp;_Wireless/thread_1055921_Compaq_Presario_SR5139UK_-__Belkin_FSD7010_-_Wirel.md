---
title: "Compaq Presario SR5139UK -  Belkin FSD7010 - Wireless"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by gordonreid1992 on 2009-01-31
> [SIZE="4"]Machine Brand and Model (PC/Laptop):-[/SIZE]
Compaq Presario SR5139UK (PC)

[SIZE="4"]Ubuntu Version:-[/SIZE]
8.10

[SIZE="4"]Kernal/architecture:-[/SIZE]
2.6.27-7-generic x86_64

[SIZE="4"]Wireless Brand, Model and Wireless Chipset:-[/SIZE]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

[SIZE="4"]ifconfig:-[/SIZE]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

[SIZE="4"]iwconfig:-[/SIZE]
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

[SIZE="4"]sudo lshw -C network:-[/SIZE]
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:d1:03:f4
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
[B]  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:60:9f:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B]
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:15:60:54:80:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[SIZE="4"]iwlist scan:-[/SIZE]
wlan0     No scan results

[SIZE="4"]Restarting the network:-[/SIZE]
* Reconfiguring network interfaces...         


Hello, I am running Ubuntu 8.10 x64 with no luck on my wireless connection, I'm using ndiswrapper and have installed Windows Network Drivers, ndiswrapper recognizes that there is networking hardware present but I can not find my router. Everything works okay in Vista Ultimate x64 and Windows 7 Beta x64.

I've included as much information as I could above, if you would like any more information please just ask.

EDIT: i've made some text bold which i think looks important, it appears my wlan0 is disabled, how would i go about enabling it?

---

### Post by Virtualism on 2009-02-01
Hey lads,

I have the same card and the same problem. I'm running a system very similar to gordons, difference being that i have less ram. Can't seem to get it to work in any way - anyone got any ideas?

---

### Post by gordonreid1992 on 2009-02-01
thanks for your reply, it appears it's just disabled although i might be wrong.

anyone any idea's how i can enable wlan0? sorry for such a stupid sounding question, i must seem very n00bish.

---

