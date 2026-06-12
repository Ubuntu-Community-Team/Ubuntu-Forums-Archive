---
title: "Realtek RTL8102EM problem accessing network"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by rosma on 2009-01-09
I have read many threads here and elsewhere on this subject and tried a variety of possible solutions but come to nothing, so I'll try posting my specific situation.

I recently bought a laptop HP G60-118EM with the intention of having Ubuntu as the main OS. I have left Vista on it and created a dual boot with Ubuntu 8.10 (Intrepid Ibex). It went pretty well except that I can't get access to the network using its wired Ethernet NIC. The NIC uses the Realtek RTL8102E which in turn is supposed to be supported by the R8169 driver.

Realtek have published a Linux driver on their web site, based on R8169 but called r8101, which is supposed to work with both 8101 and 8102 - it didn't help. I have also tried various versions and patches of the r8169 driver, also without success.

The nature of the problem is that the network status icon on the top right of Gnome reports the interface, together with MAC address, IP address, etc. correctly, but any use (e.g. Firefox) of the network fails. Also the Networking Tools show no information for this interface - IP address, MAC address, etc all blank, ping doesn't work, etc.

I am thinking of deploying a Wireless Access Point on my network and trying the laptop wirelessly, but it would be less expense and less hassle if I could get the wired networking working.

I have some previous experience of Ubuntu and rather more of Red Hat, but I haven't really delved into the kernel until the last few days, while investigating this problem.

Thanks for any help

Simon

---

### Post by paloke on 2009-02-17
Hi,

I have the same problem with an Medion Akoya (a MSI Wind clone). The network (Realtek RTL8101E/RTL8102E) work fine with the kernel version 2.6.27-7 but i can't connect with the latest version (2.6.27-12).

Best regards,

Paloke

---

### Post by KvW on 2009-03-07
Like paloke I use a Medion Akoya machine (MSI Wind Clone, Realtek RTL8101E/RTL8102E ethernet card) and it is exactly the same here. Since the kernel version 2.6.27-7 I cannot connect via lan.
I think the relevant part of Syslog is the following:

```
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  dhclient started with pid 6278 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  7 16:00:58 XXXXX dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar  7 16:00:58 XXXXX dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar  7 16:00:58 XXXXX dhclient: All rights reserved.
Mar  7 16:00:58 XXXXX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar  7 16:00:58 XXXXX dhclient: 
Mar  7 16:00:58 XXXXX NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Mar  7 16:00:58 XXXXX dhclient: Listening on LPF/eth0/00:1d:92:58:55:f2
Mar  7 16:00:58 XXXXX dhclient: Sending on   LPF/eth0/00:1d:92:58:55:f2
Mar  7 16:00:58 XXXXX dhclient: Sending on   Socket/fallback
Mar  7 16:01:02 XXXXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar  7 16:01:09 XXXXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Mar  7 16:01:24 XXXXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Mar  7 16:01:38 XXXXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Mar  7 16:01:43 XXXXX NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 6278 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  Activation (eth0) failed. 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Mar  7 16:01:44 XXXXX NetworkManager: <info>  (eth0): deactivating device (reason: 0).
```

---

