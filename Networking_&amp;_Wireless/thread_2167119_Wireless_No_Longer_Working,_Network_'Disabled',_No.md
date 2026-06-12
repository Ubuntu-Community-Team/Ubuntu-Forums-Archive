---
title: "Wireless No Longer Working, Network 'Disabled', Not Sure Why"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by M._Lengsfield on 2013-08-12
Went away for a few days and my family immediately lost wireless.  No upgrades, not sure what happened.  I've tried umpteen different solutions from the forums, but nothing has worked.   WICD tries to connect, gets past 'validating authentication', then loses it trying obtain an IP Address.  I get connection error: unable to obtain an IP address.  Other wifi devices have no such problems.  

Here's what I get: 
kitchen@kitchen-desktop:~$ sudo lspci  

 00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)  

 00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)  
 00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)  
 00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)  
 00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)  
 00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)  
 00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)  
 00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)  
 00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)  
 00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a2)  
 00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a2)  
 00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a2)  
 00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)  
 00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)  
 00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)  
 00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)  
 00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)  
 00:10.2 Multimedia audio controller: NVIDIA Corporation MCP51 AC97 Audio Controller (rev a2)  
 00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a1)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 03:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550]  
 03:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550 Series] (Secondary)  
 kitchen@kitchen-desktop:~$ sudo lspci  
 00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)  
 00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)  
 00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)  
 00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)  
 00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)  
 00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)  
 00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)  
 00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)  
 00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)  
 00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)  
 00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a2)  
 00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a2)  
 00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a2)  
 00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)  
 00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)  
 00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)  
 00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)  
 00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)  
 00:10.2 Multimedia audio controller: NVIDIA Corporation MCP51 AC97 Audio Controller (rev a2)  
 00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a1)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 03:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550]  
 03:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550 Series] (Secondary)  
 kitchen@kitchen-desktop:~$ sudo lspci -nn  
 00:00.0 RAM memory [0500]: NVIDIA Corporation C51 Host Bridge [10de:02f1] (rev a2)  
 00:00.1 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)  
 00:00.2 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)  
 00:00.3 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)  
 00:00.4 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)  
 00:00.5 RAM memory [0500]: NVIDIA Corporation C51 Host Bridge [10de:02ff] (rev a2)  
 00:00.6 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 3 [10de:027f] (rev a2)  
 00:00.7 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 2 [10de:027e] (rev a2)  
 00:02.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)  
 00:03.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)  
 00:04.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)  
 00:09.0 RAM memory [0500]: NVIDIA Corporation MCP51 Host Bridge [10de:0270] (rev a2)  
 00:0a.0 ISA bridge [0601]: NVIDIA Corporation MCP51 LPC Bridge [10de:0261] (rev a2)  
 00:0a.1 SMBus [0c05]: NVIDIA Corporation MCP51 SMBus [10de:0264] (rev a2)  
 00:0a.2 RAM memory [0500]: NVIDIA Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)  
 00:0b.0 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026d] (rev a2)  
 00:0b.1 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026e] (rev a2)  
 00:0d.0 IDE interface [0101]: NVIDIA Corporation MCP51 IDE [10de:0265] (rev a1)  
 00:0e.0 IDE interface [0101]: NVIDIA Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)  
 00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP51 PCI Bridge [10de:026f] (rev a2)  
 00:10.2 Multimedia audio controller [0401]: NVIDIA Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2)  
 00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)  
 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]  
 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]  
 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]  
 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]  
 03:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550] [1002:7146]  
 03:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]  
 kitchen@kitchen-desktop:~$ sudo lshw -c network  
   *-network DISABLED       
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:16:b6:53:7f:82  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b link=no multicast=yes wireless=IEEE 802.11bg  


I see the *-network DISABLED, but that may just reflect the fact that we're not connected.  Any ideas?

Many, many thanks.

---

### Post by M._Lengsfield on 2013-08-12
Running 13.04 on an ancient Evesham machine that came to me with Win XP loaded, 2gb ram.

Sorry for the duplicative info in the screenshot from Terminal. 

mhl

---

### Post by GwL3eNC on 2013-08-12
Hi,

i think you should give more information. You can view /var/log/syslog, but this file is very long. With a

cat /var/log/syslog | grep wlan0

you can cut out everything about  the interface wlan0. The messages repeat, try to select the messages from one
system startup and post them here. Hopefully someone can see something.

---

### Post by chili555 on 2013-08-12
In this context, 'Disabled' often means the wireless switch is off. What does this tell us?```
rfkill list all
```Can you find and switch the hardware switch or key combination?

---

### Post by M._Lengsfield on 2013-08-12
Hi, 

Thanks.  Hope this is what you need.

: wlan0: link is not ready  
 Aug 12 09:00:37 kitchen-desktop kernel: [37071.001007] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:00:37 kitchen-desktop kernel: [37071.027205] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:00:38 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:00:38 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:00:38 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:00:38 kitchen-desktop kernel: [37071.721416] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:00:45 kitchen-desktop kernel: [37078.629382] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:00:45 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:00:45 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:00:45 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:00:45 kitchen-desktop kernel: [37078.812241] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:03:43 kitchen-desktop kernel: [37257.076064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:03:54 kitchen-desktop kernel: [37267.771979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:03:58 kitchen-desktop kernel: [37271.335983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:04:01 kitchen-desktop kernel: [37275.001033] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:04:01 kitchen-desktop kernel: [37275.027340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:04:02 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:04:02 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:04:02 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:04:02 kitchen-desktop kernel: [37275.437197] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:04:09 kitchen-desktop kernel: [37282.815777] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:04:09 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:04:09 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:04:09 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:04:09 kitchen-desktop kernel: [37282.996268] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:07:04 kitchen-desktop kernel: [37458.076090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:07:18 kitchen-desktop kernel: [37471.432023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:07:21 kitchen-desktop kernel: [37474.784029] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:07:24 kitchen-desktop kernel: [37478.001058] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:07:24 kitchen-desktop kernel: [37478.026991] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:07:25 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:07:25 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:07:25 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:07:25 kitchen-desktop kernel: [37478.801221] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:07:32 kitchen-desktop kernel: [37485.718673] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:07:32 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:07:32 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:07:32 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:07:32 kitchen-desktop kernel: [37485.900284] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:10:25 kitchen-desktop kernel: [37659.072116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:10:33 kitchen-desktop kernel: [37667.060049] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:10:37 kitchen-desktop kernel: [37670.416052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:10:40 kitchen-desktop kernel: [37674.001081] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:10:40 kitchen-desktop kernel: [37674.027015] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:10:40 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:10:40 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:10:40 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:10:40 kitchen-desktop kernel: [37674.194018] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:10:48 kitchen-desktop kernel: [37681.607213] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:10:48 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:10:48 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:10:48 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:10:48 kitchen-desktop kernel: [37681.788794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:13:46 kitchen-desktop kernel: [37860.080147] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:13:54 kitchen-desktop kernel: [37867.988070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:13:58 kitchen-desktop kernel: [37871.444072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:14:01 kitchen-desktop kernel: [37875.001107] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:14:01 kitchen-desktop kernel: [37875.027041] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:14:02 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:14:02 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:14:02 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:14:09 kitchen-desktop kernel: [37882.817232] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:14:09 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:14:09 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:14:09 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:14:09 kitchen-desktop kernel: [37883.000342] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:17:07 kitchen-desktop kernel: [38061.076157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:17:15 kitchen-desktop kernel: [38069.112095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:17:19 kitchen-desktop kernel: [38072.584097] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:17:22 kitchen-desktop kernel: [38076.001132] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:17:22 kitchen-desktop kernel: [38076.027064] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:17:23 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:17:23 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:17:23 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:17:23 kitchen-desktop kernel: [38076.717171] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:17:30 kitchen-desktop kernel: [38083.722628] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:17:30 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:17:30 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:17:30 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:17:30 kitchen-desktop kernel: [38083.904084] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:20:28 kitchen-desktop kernel: [38262.076419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:20:36 kitchen-desktop kernel: [38269.896234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:20:40 kitchen-desktop kernel: [38273.468269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:20:43 kitchen-desktop kernel: [38277.001158] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:20:43 kitchen-desktop kernel: [38277.027229] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:20:44 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:20:44 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:20:44 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:20:44 kitchen-desktop kernel: [38277.361197] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:20:51 kitchen-desktop kernel: [38284.712780] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:20:51 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:20:51 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:20:51 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:20:51 kitchen-desktop kernel: [38284.896364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:23:49 kitchen-desktop kernel: [38463.080190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:23:57 kitchen-desktop kernel: [38471.064134] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:24:01 kitchen-desktop kernel: [38474.540261] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:24:04 kitchen-desktop kernel: [38478.001185] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:24:04 kitchen-desktop kernel: [38478.027199] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:24:05 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:24:05 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:24:05 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:24:05 kitchen-desktop kernel: [38478.473222] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:24:12 kitchen-desktop kernel: [38485.582552] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:24:12 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:24:12 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:24:12 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:24:12 kitchen-desktop kernel: [38485.764118] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:27:10 kitchen-desktop kernel: [38664.076220] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:27:18 kitchen-desktop kernel: [38672.120284] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:27:22 kitchen-desktop kernel: [38675.576161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:27:25 kitchen-desktop kernel: [38679.001211] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:27:25 kitchen-desktop kernel: [38679.027219] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:27:25 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:27:25 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:27:25 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:27:25 kitchen-desktop kernel: [38679.177248] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:27:33 kitchen-desktop kernel: [38686.814204] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:27:33 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:27:33 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:27:33 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:27:33 kitchen-desktop kernel: [38686.996417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:30:31 kitchen-desktop kernel: [38865.076242] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:30:39 kitchen-desktop kernel: [38873.164183] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:30:43 kitchen-desktop kernel: [38876.628185] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:30:46 kitchen-desktop kernel: [38880.001234] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:30:46 kitchen-desktop kernel: [38880.027246] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:30:47 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:30:47 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:30:47 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:30:47 kitchen-desktop kernel: [38880.997283] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:30:54 kitchen-desktop kernel: [38887.580750] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:30:54 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:30:54 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:30:54 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:30:54 kitchen-desktop kernel: [38887.764450] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:33:52 kitchen-desktop kernel: [39066.080267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:34:00 kitchen-desktop kernel: [39073.948208] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:34:03 kitchen-desktop kernel: [39077.248209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:34:07 kitchen-desktop kernel: [39081.001261] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:34:07 kitchen-desktop kernel: [39081.027329] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:34:08 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:34:08 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:34:08 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:34:08 kitchen-desktop kernel: [39081.731300] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:34:15 kitchen-desktop kernel: [39088.814753] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:34:15 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:34:15 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:34:15 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:34:15 kitchen-desktop kernel: [39088.996471] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:37:13 kitchen-desktop kernel: [39267.076665] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:37:21 kitchen-desktop kernel: [39275.152236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:37:25 kitchen-desktop kernel: [39278.484237] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:37:28 kitchen-desktop kernel: [39282.001287] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:37:28 kitchen-desktop kernel: [39282.027234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:37:29 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:37:29 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:37:29 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:37:29 kitchen-desktop kernel: [39282.665950] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:37:36 kitchen-desktop kernel: [39289.721907] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:37:36 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:37:36 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:37:36 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:37:36 kitchen-desktop kernel: [39289.904222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:40:11 kitchen-desktop kernel: [39444.464227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:40:30 kitchen-desktop kernel: [39463.592216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:40:33 kitchen-desktop kernel: [39467.136222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 09:40:36 kitchen-desktop kernel: [39470.001311] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 09:40:36 kitchen-desktop kernel: [39470.027403] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 09:40:37 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:40:37 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 09:40:37 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 09:40:37 kitchen-desktop kernel: [39470.998226] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 09:40:43 kitchen-desktop kernel: [39476.670303] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 09:40:43 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 09:40:43 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 09:40:43 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 09:40:43 kitchen-desktop kernel: [39476.852526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:23:16 kitchen-desktop kernel: [45630.260040] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:24:37 kitchen-desktop kernel: [45711.160068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:24:41 kitchen-desktop kernel: [45714.512075] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:24:44 kitchen-desktop kernel: [45718.001104] rndis_wlan 1-4:1.0 wlan0: media connect  
 Aug 12 11:24:44 kitchen-desktop kernel: [45718.027120] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 11:24:45 kitchen-desktop avahi-daemon[943]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 11:24:45 kitchen-desktop avahi-daemon[943]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 11:24:45 kitchen-desktop avahi-daemon[943]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 11:24:45 kitchen-desktop kernel: [45718.566021] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 11:24:48 kitchen-desktop kernel: [45722.004101] rndis_wlan 1-4:1.0 wlan0: media disconnect  
 Aug 12 11:24:48 kitchen-desktop avahi-daemon[943]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 11:24:48 kitchen-desktop avahi-daemon[943]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 11:24:48 kitchen-desktop avahi-daemon[943]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 11:24:48 kitchen-desktop kernel: [45722.188328] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:46:54 kitchen-desktop kernel: [47048.076282] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 11:58:34 kitchen-desktop kernel: [   25.666270] rndis_wlan 1-4:1.0 wlan0: register 'rndis_wlan' at usb-0000:00:0b.1-4, Wireless RNDIS device, BCM4320b based, 00:16:b6:53:7f:82  
 Aug 12 11:58:41 kitchen-desktop kernel: [   38.084194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 15:56:07 kitchen-desktop kernel: [ 2283.895509] rndis_wlan 1-6:1.0 wlan0: register 'rndis_wlan' at usb-0000:00:0b.1-6, Wireless RNDIS device, BCM4320b based, 00:16:b6:53:7f:82  
 Aug 12 15:56:32 kitchen-desktop kernel: [ 2309.077154] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 16:59:12 kitchen-desktop avahi-daemon[932]: Withdrawing workstation service for wlan0.  
 Aug 12 16:59:12 kitchen-desktop kernel: [ 6068.968111] rndis_wlan 1-6:1.0 wlan0: unregister 'rndis_wlan' usb-0000:00:0b.1-6, Wireless RNDIS device, BCM4320b based  
 Aug 12 17:03:27 kitchen-desktop kernel: [ 6323.561632] rndis_wlan 1-6:1.0 wlan0: register 'rndis_wlan' at usb-0000:00:0b.1-6, Wireless RNDIS device, BCM4320b based, 00:16:b6:53:7f:82  
 Aug 12 17:03:50 kitchen-desktop kernel: [ 6347.076776] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:20 kitchen-desktop kernel: [ 7397.052227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:24 kitchen-desktop kernel: [ 7400.460250] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:33 kitchen-desktop kernel: [ 7410.001171] rndis_wlan 1-6:1.0 wlan0: media connect  
 Aug 12 17:21:33 kitchen-desktop kernel: [ 7410.027350] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 17:21:34 kitchen-desktop avahi-daemon[932]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:21:34 kitchen-desktop avahi-daemon[932]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 17:21:34 kitchen-desktop avahi-daemon[932]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 17:21:34 kitchen-desktop kernel: [ 7410.874094] IPv6: wlan0: IPv6 duplicate address fe80::216:b6ff:fe53:7f82 detected!  
 Aug 12 17:21:38 kitchen-desktop kernel: [ 7414.572921] rndis_wlan 1-6:1.0 wlan0: media disconnect  
 Aug 12 17:21:38 kitchen-desktop avahi-daemon[932]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 17:21:38 kitchen-desktop avahi-daemon[932]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:21:38 kitchen-desktop avahi-daemon[932]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 17:21:38 kitchen-desktop kernel: [ 7414.756523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:45 kitchen-desktop kernel: [ 7422.076308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:53 kitchen-desktop kernel: [ 7429.924251] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:21:59 kitchen-desktop kernel: [ 7435.764259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:22:02 kitchen-desktop kernel: [ 7439.001301] rndis_wlan 1-6:1.0 wlan0: media connect  
 Aug 12 17:22:02 kitchen-desktop kernel: [ 7439.027228] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 17:22:03 kitchen-desktop avahi-daemon[932]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:22:03 kitchen-desktop avahi-daemon[932]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 17:22:03 kitchen-desktop avahi-daemon[932]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 17:22:10 kitchen-desktop kernel: [ 7446.826548] rndis_wlan 1-6:1.0 wlan0: media disconnect  
 Aug 12 17:22:10 kitchen-desktop avahi-daemon[932]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 17:22:10 kitchen-desktop avahi-daemon[932]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:22:10 kitchen-desktop avahi-daemon[932]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 17:22:10 kitchen-desktop kernel: [ 7447.008568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:22:42 kitchen-desktop kernel: [ 7478.604211] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:22:55 kitchen-desktop kernel: [ 7491.528259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:22:58 kitchen-desktop kernel: [ 7494.900258] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:23:01 kitchen-desktop kernel: [ 7498.001309] rndis_wlan 1-6:1.0 wlan0: media connect  
 Aug 12 17:23:01 kitchen-desktop kernel: [ 7498.027362] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 17:23:03 kitchen-desktop avahi-daemon[932]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:23:03 kitchen-desktop avahi-daemon[932]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 17:23:03 kitchen-desktop avahi-daemon[932]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 17:23:06 kitchen-desktop kernel: [ 7502.842939] rndis_wlan 1-6:1.0 wlan0: media disconnect  
 Aug 12 17:23:06 kitchen-desktop avahi-daemon[932]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 17:23:06 kitchen-desktop avahi-daemon[932]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:23:06 kitchen-desktop avahi-daemon[932]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 17:23:06 kitchen-desktop kernel: [ 7503.024513] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:29:55 kitchen-desktop kernel: [ 7911.648321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:29:55 kitchen-desktop kernel: [ 7911.692437] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:29:58 kitchen-desktop kernel: [ 7915.124322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Aug 12 17:30:01 kitchen-desktop kernel: [ 7918.001362] rndis_wlan 1-6:1.0 wlan0: media connect  
 Aug 12 17:30:01 kitchen-desktop kernel: [ 7918.027939] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Aug 12 17:30:02 kitchen-desktop avahi-daemon[932]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:30:02 kitchen-desktop avahi-daemon[932]: New relevant interface wlan0.IPv6 for mDNS.  
 Aug 12 17:30:02 kitchen-desktop avahi-daemon[932]: Registering new address record for fe80::216:b6ff:fe53:7f82 on wlan0.*.  
 Aug 12 17:30:06 kitchen-desktop kernel: [ 7923.164490] rndis_wlan 1-6:1.0 wlan0: media disconnect  
 Aug 12 17:30:06 kitchen-desktop avahi-daemon[932]: Interface wlan0.IPv6 no longer relevant for mDNS.  
 Aug 12 17:30:06 kitchen-desktop avahi-daemon[932]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:b6ff:fe53:7f82.  
 Aug 12 17:30:06 kitchen-desktop avahi-daemon[932]: Withdrawing address record for fe80::216:b6ff:fe53:7f82 on wlan0.  
 Aug 12 17:30:06 kitchen-desktop kernel: [ 7923.348569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by M._Lengsfield on 2013-08-12
rfkill list all

2: phy3 Wireless LAN
soft blocked: no
hard blocked: no

It's a desktop with a usb adapter, so there's no switch that I can see.

---

### Post by GwL3eNC on 2013-08-12
Hi,

i am realy not shure and sooner or later someone can help you. If i do the cat on
my pc i see there many IPv4 entrys (no one IPv6). In yours i dont see one. Do you use
network manager or how do you configure you interfaces.

Has someone changed settings of your interface to IPv6?

---

### Post by M._Lengsfield on 2013-08-13
I go no deeper than WICD.  No idea how that would have been changed.

---

### Post by GwL3eNC on 2013-08-13
Hi M._Lengsfield,

sorry about my previous idea. Think thats not the problem. Found some other people in 09 have
also trouble with wicd automatic dhcp request [http://wicd.sourceforge.net/punbb/viewtopic.php?id=277](http://wicd.sourceforge.net/punbb/viewtopic.php?id=277). 
Before you talked about i dont know wicd. 

What happens if you try to restart internet manualy with 

sudo ifdown wlan0
sudo ifup wlan0

---

### Post by M._Lengsfield on 2013-08-13
Thanks, but it doesn't seem to work.  Still get the **Can't Obtain IP Address** message. 

This is weird in that I was working, but now cannot.  Most networking probs come in the setup.

Thanks again.

---

### Post by GwL3eNC on 2013-08-13
You are welcome. on the wicd manpage i found that the configuration and logging is stored in

/etc/wicd/manager-settings.conf
/etc/wicd/wireless-settings.conf
/var/lib/wicd/configurations/
/var/log/wicd/

I would now view this files to see if there something is wrong. Hopefully this files are not very long, so you can
post them eventually.

My personal last option would be to remove wicd and try the network manager. If it works you know that something
with wicd is wrong.

---

### Post by M._Lengsfield on 2013-08-13
My knowledge is so basic that I wouldn't know what to do with the settings.  I was going to uninstall- re-install WICD and see what happens.   I'd like to go back to Network Manager, but I have no wired connection for this computer, so I must download to another machine and transfer by memory stick.  I couldn't see where I could get Netwpork Manager in that form.  Any ideas?

thanks.

---

### Post by GwL3eNC on 2013-08-13
You can download the debian file from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
Search network manager and select it. At the bottom of the page you can donwload the deb file.
To install it use

sudo dpkg -i FILENAME.DEB

First you should completly remove wicd. 

sudp apt-get purge wicd

or something like that. It is shurly possible that you must download more packages
if network manager needs them. Cant you do a manual configuration wirh /etc/network/interfaces?
Would be easier. After remove wicd open your /etc/network/interfaces as sudo and try to adapt
it from mine. If you are done, save and try sudo service networking restart. If all wokrs you are connected
and can install all needed packages. (You only need to change YOURSSID and YOURSAFETYKEY)

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface. dynamic DHCP 
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOURSSID
    wpa-psk YOURSAFETYKEY
   

auto eth0 
 iface eth0 inet static
 address 192.168.0.1
 netmask 255.255.255.0

---

### Post by M._Lengsfield on 2013-08-13
thanks.  I'll give that a shot.
mhl

---

