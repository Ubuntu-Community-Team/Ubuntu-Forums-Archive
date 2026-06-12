---
title: "Wired Connection Carrier On/Off Repeatedly"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by BFDill on 2012-06-01
I just upgraded to 12.04 via network from what was a fresh 11.10 install from CD.

My on-board gigabit Ethernet connection is now experiencing a 25% packet loss (gauged via remote ping from Mac on local network segment).

I tried three different Ethernet cables and three different ports on the same switch.  I have not tried a different switch since no other devices are having problems with the same port.

I have tried this command from a different [thread]("http://ubuntuforums.org/showthread.php?t=1978608"):
```
sudo pkill -9 NetworkManager
```That thread also references:
>  Removing NetworkManager and configuring trough pppoeconf solved the problemI'm not sure how to do that or what the implications would be, so I wanted to ask here first since I don't know what to do...

Does anyone have any pointers with respect to what to check/try next?

Thanks,
Ben

My syslog looks like this:
```
Jun  1 13:23:21 fileserver NetworkManager[2775]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  1 13:23:21 fileserver kernel: [ 3312.535120] atl1 0000:02:00.0: eth1 link is down
Jun  1 13:23:23 fileserver NetworkManager[2775]: <info> (eth1): carrier now ON (device state 100)
Jun  1 13:23:23 fileserver kernel: [ 3314.628180] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
Jun  1 13:23:59 fileserver NetworkManager[2775]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  1 13:23:59 fileserver kernel: [ 3350.456066] atl1 0000:02:00.0: eth1 link is down
Jun  1 13:24:01 fileserver NetworkManager[2775]: <info> (eth1): carrier now ON (device state 100)
Jun  1 13:24:01 fileserver kernel: [ 3352.525389] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
Jun  1 13:24:20 fileserver NetworkManager[2775]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  1 13:24:20 fileserver kernel: [ 3370.732157] atl1 0000:02:00.0: eth1 link is down
Jun  1 13:24:22 fileserver NetworkManager[2775]: <info> (eth1): carrier now ON (device state 100)
Jun  1 13:24:22 fileserver kernel: [ 3372.965455] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
Jun  1 13:24:51 fileserver NetworkManager[2775]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  1 13:24:51 fileserver kernel: [ 3402.165688] atl1 0000:02:00.0: eth1 link is down
Jun  1 13:24:53 fileserver NetworkManager[2775]: <info> (eth1): carrier now ON (device state 100)
Jun  1 13:24:53 fileserver kernel: [ 3404.278229] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
```My dmesg looks like this:
```
[ 3121.352959] atl1 0000:02:00.0: eth1 link is down
[ 3123.658534] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3125.213936] atl1 0000:02:00.0: eth1 link is down
[ 3127.752835] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3150.829192] atl1 0000:02:00.0: eth1 link is down
[ 3153.036862] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3204.139573] atl1 0000:02:00.0: eth1 link is down
[ 3206.307706] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3232.123738] atl1 0000:02:00.0: eth1 link is down
[ 3234.173279] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3267.171281] atl1 0000:02:00.0: eth1 link is down
[ 3269.234355] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
[ 3312.535120] atl1 0000:02:00.0: eth1 link is down
[ 3314.628180] atl1 0000:02:00.0: eth1 link is up 1000 Mbps full duplex
```lspci output:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port C)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation NV44 [GeForce 6200 LE] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. Attansic L1 Gigabit Ethernet (rev b0)
03:05.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
03:06.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
04:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
```

---

### Post by praseodym on 2012-06-01
Hi,

"pppoeconf" only works with pure modem, not with a router. Do you have one?

Try removing the package "resolvconf". Install **ethtool** and check:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
sudo ethtool eth0
sudo ethtool eth1
ifconfig -a
```

---

### Post by jolurove on 2012-06-02
I've been having the same issue since I installed 12.04. I'm about to give up finding a solution for this. :(

---

### Post by praseodym on 2012-06-02
@jolurove:

Do you use a router? If no:

```
sudo service network-manager stop
sudo pppoeconf
```

---

### Post by jolurove on 2012-06-03
> **praseodym said:**
> @jolurove:

Do you use a router? If no:

```
sudo service network-manager stop
sudo pppoeconf
```

I do have a router.. sadly :(

---

### Post by praseodym on 2012-06-03
In this case, add the Login/PW of your ISP in the router interface. For this, connect via cable and type in the router IP into the browser. Create a PPPoE connection with your data. Then remove any connections in "cable" and "DSL" in Ubuntu and reboot. After that, please show the outputs of the commands from #2

---

