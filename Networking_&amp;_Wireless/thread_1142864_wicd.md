---
title: "wicd"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by patanjali on 2009-04-29
Hi,

Using Hardy on Tosh A30 laptop.  2.6GHz and 756MB RAM.  Linksys PC card wireless adaptor using Broadcom BCM4318 chipset (sigh, yes I know!).

I've got a problem with my wireless connection. I had it working with the default network manager but kept losing the IP address using DHCP. So I installed wicd thinking that would solve the problem.  wicd worked until the first time I rebooted, and it hasn't worked since.  So now I am using a laptop with a wired connection.  How crappy is that?

If anyone can help, I would be really grateful.  Below are some outputs from terminal.

TIA

p

wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:14:78:0B
                    ESSID:"Tiscali14780B"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported

jack@phoenix:~$ dmesg | grep -e wlan -e ndis
[   50.248702] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   50.346391] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[   50.355405] ndiswrapper: using IRQ 16
[   50.708393] wlan0: ethernet device 00:18:39:c0:fc:b5 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   50.708436] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   50.708519] usbcore: registered new interface driver ndiswrapper
[   60.037027] ndiswrapper: device wlan0 removed
[   60.038281] usbcore: deregistering interface driver ndiswrapper
[   60.118891] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   60.152538] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[   60.162982] ndiswrapper: using IRQ 16
[  115.964105] wlan0: ethernet device 00:18:39:c0:fc:b5 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[  115.965320] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  115.966363] usbcore: registered new interface driver ndiswrapper
[ 1307.700948] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2740.851537] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2742.474746] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2762.384585] wlan0: no IPv6 routers present
[ 2992.646694] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2994.144480] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3013.811676] wlan0: no IPv6 routers present
[ 3200.042348] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3509.844713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3510.069104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3566.129416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3566.491458] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4686.595413] ndiswrapper: device wlan0 removed
[ 4686.597223] usbcore: deregistering interface driver ndiswrapper
[ 4687.495765] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 4687.749663] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[ 4687.809597] ndiswrapper: using IRQ 16
[ 4688.699911] wlan0: ethernet device 00:18:39:c0:fc:b5 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[ 4688.700000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 4688.700175] usbcore: registered new interface driver ndiswrapper
[ 4688.936564] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.555436] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1839.377934] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1959.323004] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1961.058594] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1981.806308] wlan0: no IPv6 routers present

:confused::confused::confused::confused::confused::confused:

---

### Post by patanjali on 2009-04-29
Guys,

jack@phoenix:~$ ndiswraqpper -l
bash: ndiswraqpper: command not found
jack@phoenix:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: ssb)
p

---

### Post by dmizer on 2009-04-29
Please post the output of:
```
lshw -C network
```

When posting the output from terminal, please use the bbc ```
 tag as follows:
[COLOR="Red"][noparse][code][/noparse][/COLOR]terminal output here[COLOR="Red"][noparse]
```[/noparse][/COLOR]

---

### Post by Trafficflow on 2009-04-29
I am relatively new at this but I had the identical problem.I was using a Netgear adapter Wg111t and it was not supported. I went to do Wg1112v. Wicd worked once also. I went to the Synaptic
I think and did a remove. I found the network manager and did a reload. It reconized the adapter and configured everything. Even the se urity that was set up as WAP2! I has been working ever since. Hope this helps.

---

### Post by patanjali on 2009-04-30
> **dmizer said:**
> Please post the output of:
```
lshw -C network
```

When posting the output from terminal, please use the bbc ```
 tag as follows:
[COLOR="Red"][noparse][code][/noparse][/COLOR]terminal output here[COLOR="Red"][noparse]
```[/noparse][/COLOR]

dmizer,  

here is the output you request.

```
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:ce:ee:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.6 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:39:c0:fc:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+ASUS,02/11/2005, 3.100.64.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

---

### Post by patanjali on 2009-04-30
When I try and enable the interface through System/Metwork Settings iget the error message "Could not parse the XML output from the network configuration backend."

p  :(

---

### Post by dmizer on 2009-04-30
Here's a thread where someone got connected with your card: [http://ubuntuforums.org/showthread.php?t=830090](http://ubuntuforums.org/showthread.php?t=830090)

---

