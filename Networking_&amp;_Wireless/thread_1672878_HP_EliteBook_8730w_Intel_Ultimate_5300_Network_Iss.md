---
title: "HP EliteBook 8730w/ Intel Ultimate 5300 Network Issue"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by Brendor on 2011-01-21
Hello, Ive installed Ubuntu recently but none of my attempts to get  the  wifi network working were successfull. It establishes connection but  the indicator shows no signal and I cant connect to any website, I tried  pinging external IPs etc. None of these worked.

lspci -nn | grep 'Wireless Brand'Does not show anything.

I could find 03:00:0 Network Controller: Intel Corporation Ultimate N WiFi Link 5300

 lsmod | grep "wlan_module_name"Doesnt show anything.

Restarting network says only:
* Reconfiguring network interfaces...

Kernel boot messages:
```
[  100.353572] wlan0: Trigger new scan to find an IBSS to join
[  101.397337] ip_tables: (C) 2000-2006 Netfilter Core Team
[  101.418733] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  101.419360] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  101.419363] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[  101.419365] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  103.950047] wlan0: Trigger new scan to find an IBSS to join
[  109.040027] wlan0: Creating new IBSS network, BSSID fa:c0:f9:1c:25:cf
[  109.072196] iwlagn 0000:03:00.0: Unable to find TIM Element in beacon
[  109.072491] iwlagn 0000:03:00.0: Unable to find TIM Element in beacon
[  110.480013] wlan0: no IPv6 routers present
[  139.043824] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  204.080052] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  269.121297] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  334.080055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  399.040079] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  464.087467] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  500.080074] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  536.160069] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  572.080071] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  634.430047] mac80211-phy0: failed to remove key (0, ff:ff:ff:ff:ff:ff) from hardware (-16)
[  634.825269] iwlagn 0000:03:00.0: PCI INT A disabled
[  640.828362] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  640.828366] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  640.828471] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  640.828504] iwlagn 0000:03:00.0: setting latency timer to 64
[  640.828617] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[  640.850800] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  640.850939] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[  640.854412] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[  640.855300] phy1: Selected rate control algorithm 'iwl-agn-rs'
[  641.057268] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  641.625404] wlan0: Trigger new scan to find an IBSS to join
[  647.021297] wlan0: Trigger new scan to find an IBSS to join
[  650.214648] wlan0: Creating new IBSS network, BSSID 7e:c0:c6:13:e3:d9
[  650.280934] iwlagn 0000:03:00.0: Unable to find TIM Element in beacon
[  650.291029] iwlagn 0000:03:00.0: Unable to find TIM Element in beacon
[  652.150039] wlan0: no IPv6 routers present
[  681.040082] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  717.120082] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  753.120076] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  789.120053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  825.120026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  861.040030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  896.960031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  933.120075] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  968.960076] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1034.092570] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1070.000074] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1106.000038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1142.080069] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1178.080095] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1214.080047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1250.000092] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1315.040079] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1351.040099] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1387.040053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1423.120056] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1459.040037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1495.043796] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1531.040032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1567.040094] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1603.040042] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1668.000049] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1704.003769] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1740.003342] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1776.002552] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1812.080070] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1848.000077] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1884.000074] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1949.120020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1984.960073] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2021.130051] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2057.120071] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2092.960055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2129.120055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2165.120090] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2201.040080] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2236.960048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2273.120072] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2308.960051] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2374.080024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2410.003824] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2446.080067] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:25:b3:71:b0:d2
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=1.0.2-k4 firmware=1.8-3 latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:45 memory:db300000-db31ffff memory:db324000-db324fff ioport:80e0(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:5d:7d:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwlagn  driverversion=2.6.35-22-generic firmware=8.24.2.12 ip=10.42.43.1  latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:db100000-db101fff
```

Kernel info:
2.6.35-22-generic x86_64

The network Im trying to connect to is hidden, so I have to input SSID manually, I doubt this causes the problem.

---

### Post by chili555 on 2011-01-21
This part suggests your card is trying to join an ad-hoc network, that is, computer to computer, instead of an infrastucture, that is, computer to router:> wlan0: Creating new **IBSS** network, BSSID fa:c0:f9:1c:25:cfIs the behavior improved if you do in a terminal:```
sudo iwconfig wlan0 mode managed
```

---

### Post by Brendor on 2011-01-26
Thanks, Ive already solved the problem by looking up the debian forums as my friend adviced. However, this is my second computer I install ubuntu to and I had network problems with both of them :(

Edit: adding a link if anyone has the same problem with these intel wifis
[http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)

---

