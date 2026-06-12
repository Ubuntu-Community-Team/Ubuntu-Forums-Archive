---
title: "Configuring AR0 interface on ubuntu server"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by graflaszlo on 2010-01-20
Hi all,

I have an HP server LH3 with two wired ethernet cards and a Linksys wireless PCI network card, model WMP600N. I want to join my private network by requesting IP addresses from a DHCP server. The wired interfaces always get an IP address but the wireless no.

My router has the following settings:

Wireless Radio : Enabled
WISH : Active
MAC Address : 00:22:B0:B3:E9:4C
Network Name (SSID) : mysid
Channel : 1 
Security Mode : WPA/WPA2 - Personal
Wi-Fi Protected Setup : Enabled/Configured

These are my command and they outputs:

# lspci
02:02.0 Network controller: RaLink RT2800 802.11n PCI

# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:22:B0:B3:E9:4C
          Link Quality=10/100  Signal level:-49 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# lsmod
Module                  Size  Used by
ieee80211_crypt_wep    11776  0
ieee80211_crypt        13444  1 ieee80211_crypt_wep
lp                     17156  0
parport                42220  1 lp
osst                   59292  0
rt2860sta             523352  0
st                     44700  0
psmouse                61972  0
pcspkr                 10496  0
serio_raw              13316  0
i2c_piix4              18576  0
shpchp                 40340  0
e100                   42124  0
mii                    13440  1 e100
aic7xxx               134488  0
i2o_core               47772  0
scsi_transport_spi     29824  1 aic7xxx
megaraid               49992  3
fbcon                  45856  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13696  1 fbcon
softcursor              9984  1 bitblit

# lshw -C network
  *-network:0 DISABLED
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: ra0
       version: 00
       serial: 00:1e:e5:eb:0f:87
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network:1
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 05
       serial: 00:90:27:87:67:7e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.1.190 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:2
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:90:27:87:45:17
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

# iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
ra0       Interface doesn't support scanning : Network is down

# lsb_release -d
Description:    Ubuntu 9.04

# uname -mr
2.6.28-11-server i686

# modprobe rt2860sta
---- has no output

#more /etc/Wireless/RT2860STA/RT2860STA.dat
Default
CountryRegion=9
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=mysid
NetworkType=Infra
WirelessMode=
Channel=1
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2
EncrypType=WEP
WPAPSK=086e18176b67beb73d2d2fcf432ef098e35636b6932ee82acb3f68e58cd245fa
DefaultKeyID=1
Key1Type=01
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4

Please help me!!!!
---
graflaszlo

---

