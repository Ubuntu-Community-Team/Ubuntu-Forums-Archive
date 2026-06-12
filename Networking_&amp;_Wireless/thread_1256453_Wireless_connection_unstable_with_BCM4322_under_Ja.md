---
title: "Wireless connection unstable with BCM4322 under Jaunty"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Caranud on 2009-09-02
Hi all !

Happy owner of a netbook (MSI Wind U100X), I had some problem with my Wifi connection… The original Wireless card I had was a Realtek RTL8187SE which suffers from a lack of range ([here]("http://forums.msiwind.net/hacks-and-mods/improving-range-change-the-card-t11344.html") for more info). 

I then decided to change for a better Wifi card, a Dell 1510 Wireless Card by what I have read on forums. It seems to work well (proprietary driver Broadcom STA, wl.ko loaded) when I recently reinstalled my OS (Ubuntu 9.04 Jaunty, installed on ) but after some minutes the connection randomly disconnect and then immediately reconnect. This unstable connection is the only thing that doesn’t work on my computer…

Could you please help me ?


Note : I know that the Realtek card is now more supported but it still have the range problem and doesn’t seem to be more stable.

---

### Post by Caranud on 2009-09-02
1) Machine brand : MSI Wind U100X

2) ```
$lspci -nn | grep 'Wireless'
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```

3) ```
iwconfig eth1
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:166
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

```

4) ```
lsmod | grep wl
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```


5) ```
dmesg | grep wl
[   10.472870] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.479960] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.479977] wl 0000:02:00.0: setting latency timer to 64
```

6) ```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:92:59:31:a6
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:5a:a1:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.2 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:eb:78:9e:e5:f9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

7)```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:197  Noise level:166
          Rx invalid nwid:0  invalid crypt:13  invalid misc:0

pan0      no wireless extensions.
``````
cat  /etc/network/interfaces
auto lo
iface lo inet loopback
```

8) ```
lsb_release -d
Description:    Ubuntu 9.04

```

9) ```
uname -mr
2.6.28-15-generic i686

```

```
iwlist scan
eth1      Interface doesn't support scanning.

```

```
nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1D:92:59:31:A6

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto ALICE-0E61CD] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:1F:3A:5A:A1:F4

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ALICE-0E61CD:   Infra, 00:16:38:0E:61:D8, Freq 2452 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Livebox-9740:    Infra, 00:18:E7:64:E8:24, Freq 2437 MHz, Rate 0 Mb/s, Strength 80 WPA

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

```
sudo /etc/init.d/networking restart
[sudo] password for acasse: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
```

---

