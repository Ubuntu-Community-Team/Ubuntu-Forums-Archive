---
title: "Enabling Wireless with RaLink in Zotac HD-ND22"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by lonemangx on 2011-03-10
I just want to setup adhoc network using the wireless card that came with the box but I'm having a hard time getting it up. I have gone through a lot of posts about wireless troubleshooting but nothing has solved it. Left clicking the network manager tray icon always says wireless network is disconnected. "Enable Wireless" is checked.

Some info:
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````
sudo lshw -C network
[sudo] password for roboteknik: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:2b:b8:e1
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=112.xxx.xxx.xx latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:fae7c000-fae7cfff ioport:d080(size=8) memory:fae7e400-fae7e4ff memory:fae7e000-fae7e00f
  *-network DISABLED
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 74:f0:6d:29:26:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff
``````
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Device or resource busy
```I think having it ENABLED is the problem here.

---

### Post by chili555 on 2011-03-10
> I think having it ENABLED is the problem here.I think the right driver for the right device is the problem. Please post:```
lspci -nn | grep -i RaLink
lsmod | grep rt2
```Also, your wired ethernet is connected; Network Manager will deny a wireless connection if wired is available.

---

### Post by lonemangx on 2011-03-10
Here's some output:
```
lspci -nn | grep -i RaLink
04:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
``````
lsmod | grep rt2
rt2860sta             904536  0 
rt2800pci              10233  0 
rt2800lib              32002  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              267099  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
```> Also, your wired ethernet is connected; Network Manager will deny a wireless connection if wired is available.     So I cannot share my internet connection through wireless?

---

### Post by chili555 on 2011-03-10
> So I cannot share my internet connection through wireless?You certainly can; Network Manager is designed to disallow two connections to the internet, not one to the internet and one to another computer (ad-hoc).> rt2860sta             904536  0 
rt2800pci              10233  0 
rt2800lib              32002  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              267099  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pciWow! That is a whole lot of drivers for just one card. Let's banish a few and see if your card doesn't come to life. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot. Is your wireless working now?

---

### Post by lonemangx on 2011-03-10
Wow! Thanks a lot. It's already fixed. I noticed that wlan0 is gone replaced by ra0.

---

