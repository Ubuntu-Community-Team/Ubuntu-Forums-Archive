---
title: "cannot connect to wireless network shown"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by rudedcam on 2011-07-29
this is a brand new installation of 10.04 on a desktop. it's a dual boot with XP and the connection works on that side.

i'm thrown off balance by the complexity of the situation... at least it is to me ;). 
i am able to see my wireless connection (along with my neighbor's). i enter the WPA password when prompted and for the next 5 minutes, it tries to connect with no success at the end.
a big of help would be so much appreciated.

```
francis@gandhi:~$ sudo lshw -c network
  *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan0
       version: 01
       serial: 00:1e:2a:46:cc:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:f6800000-f680ffff
  *-network:1
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:be:f2:20
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:5 ioport:a800(size=256) memory:f6000000-f60000ff
```
```
francis@gandhi:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0a.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
```
```
francis@gandhi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:">\x05\xF1\xEC\xD9g3\xB7\x99P\xA3\xE3\x14\xD3\xD94\xF7^\xA0\xF2\x10\xA8\xF6\x05\x94\x01\xBE\xB4\xBCDx\xFA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
```
francis@gandhi:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:50:BA:BE:F2:20

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1E:2A:46:CC:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR:         Infra, 00:26:F2:43:48:3E, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA
    BELL937:         Infra, 3C:EA:4F:B8:94:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WEP
    Max:             Infra, 00:22:6B:4C:F6:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2

```
```
francis@gandhi:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan0
       version: 01
       serial: 00:1e:2a:46:cc:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:f6800000-f680ffff
  *-network:1
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:be:f2:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:5 ioport:a800(size=256) memory:f6000000-f60000ff
```

---

### Post by thefasterblueone on 2011-07-29
Change your encryption to open or WEP to test if it works.

---

### Post by rudedcam on 2011-07-29
> **thefasterblueone said:**
> Change your encryption to open or WEP to test if it works.
i have tried that already a few days ago. if i recall right, the password did not fit or at least the connection didn't go through. plus, i am certain that it is a "WPA & WPA2 personal" because i connect my laptop on that wireless connection regularly using this security protocol.

---

