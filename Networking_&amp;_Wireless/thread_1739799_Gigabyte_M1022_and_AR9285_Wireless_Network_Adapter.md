---
title: "Gigabyte M1022 and AR9285 Wireless Network Adapter"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by cbcoza on 2011-04-26
I had U10.10 installed prior to running U10.10 Desktop, and the wlan worked flawlessly on that.
My understanding is that the packages are the same and so this should be installed with Desktop, however it will not action the final connection.

The wlan is finding networks and prompts for the Key when connecting, but it never actually connects.

> sudo lshw -C network gives the following:

>  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:78:56:6b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:4000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9003ffff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:49:95:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:96100000-9610ffffThe above seems to show the driver correctly.

I have disabled N in the intel-5300*.conf file under modprobe, rebooted but the same results.


Syslog shows the following as below:

> Apr 26 17:04:44 ubuntu-net kernel: [ 1494.018388] wlan0: authenticated
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.018443] wlan0: associate with 00:1c:10:b7:e6:97 (try 1)
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020845] wlan0: RX AssocResp from 00:1c:10:b7:e6:97 (capab=0x411 status=0 aid=4)
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020856] wlan0: associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: Associated with 00:1c:10:b7:e6:97
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: CTRL-EVENT-CONNECTED - Connection to 00:1c:10:b7:e6:97 completed (reauth) [id=0 id_str=]
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MAW'.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> dhclient started with pid 1750
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 17:04:44 ubuntu-net dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 17:04:44 ubuntu-net dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 17:04:44 ubuntu-net dhclient: All rights reserved.
Apr 26 17:04:44 ubuntu-net dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 17:04:44 ubuntu-net dhclient: 
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 17:04:44 ubuntu-net dhclient: Listening on LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   Socket/fallback
Apr 26 17:04:44 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
gareth@ubuntu-net:~$ sudo tail -n25 /var/log/syslog
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.018443] wlan0: associate with 00:1c:10:b7:e6:97 (try 1)
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020845] wlan0: RX AssocResp from 00:1c:10:b7:e6:97 (capab=0x411 status=0 aid=4)
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020856] wlan0: associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: Associated with 00:1c:10:b7:e6:97
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: CTRL-EVENT-CONNECTED - Connection to 00:1c:10:b7:e6:97 completed (reauth) [id=0 id_str=]
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MAW'.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> dhclient started with pid 1750
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 17:04:44 ubuntu-net dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 17:04:44 ubuntu-net dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 17:04:44 ubuntu-net dhclient: All rights reserved.
Apr 26 17:04:44 ubuntu-net dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 17:04:44 ubuntu-net dhclient: 
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 17:04:44 ubuntu-net dhclient: Listening on LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   Socket/fallback
Apr 26 17:04:44 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 26 17:04:47 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
gareth@ubuntu-net:~$ sudo tail -n25 /var/log/syslog
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020845] wlan0: RX AssocResp from 00:1c:10:b7:e6:97 (capab=0x411 status=0 aid=4)
Apr 26 17:04:44 ubuntu-net kernel: [ 1494.020856] wlan0: associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: Associated with 00:1c:10:b7:e6:97
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 26 17:04:44 ubuntu-net wpa_supplicant[904]: CTRL-EVENT-CONNECTED - Connection to 00:1c:10:b7:e6:97 completed (reauth) [id=0 id_str=]
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MAW'.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> dhclient started with pid 1750
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 17:04:44 ubuntu-net dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 17:04:44 ubuntu-net dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 17:04:44 ubuntu-net dhclient: All rights reserved.
Apr 26 17:04:44 ubuntu-net dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 17:04:44 ubuntu-net dhclient: 
Apr 26 17:04:44 ubuntu-net NetworkManager[790]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 17:04:44 ubuntu-net dhclient: Listening on LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   LPF/wlan0/00:25:d3:49:95:6c
Apr 26 17:04:44 ubuntu-net dhclient: Sending on   Socket/fallback
Apr 26 17:04:44 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 26 17:04:47 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 26 17:04:55 ubuntu-net dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11--
Thanks
Gareth

---

### Post by cbcoza on 2011-04-27
Something must be funky with the Work linksys unit. Working 100% at home on a Globesurfer.

---

