---
title: "Problems with rt2870 outside of gnome"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by UMP on 2010-03-27
Hi all,

I'm using a rt2870 usb wireless dongle. The first thing I do after installing ubuntu is to blacklist rt2800usb and then, after a reboot, use the Network Manger GUI tool to set up my home Wifi network. This always works perfectly.

I've re-tasked that hardware to be my media center running XBMC. Unfortunately, XBMC seems to have no net connection (it runs instead of gnome, not on top of it). Googling I came to the conclusion that I'd have to set up /etc/Wireless/RT2870STA/RT2870STA.dat and sure enough after doing so iwconfig displays my wireless details correctly. Unfortunately it still doesn't seem to work though.

The interesting thing is that, if I refresh my routers admin console wireless page during startup I will see the mac address of my wireless dongle appear there briefly and disappear again. Similarly, iwconfig/iwpriv suggest they can clearly see the access point.

I've spent the last week making minor changes to the config file and trying pretty much everything Google suggests to no effect so I'm hoping you might have some ideas that I can try.

For what it's worth, it's a DWA-140 dongle which is listed as supported 'out of the box' on [the compatibility pages]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") though I suspect those pages don't differentiate between working, and working via gnome/desktop tools.

Thanks in advance for any and all help!

The router is set up in b/g/n mixed mode with WPA/WPA2 + AES/TKIP on channel 1.

```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=0
CountryRegionABand=7
CountryCode=IE
ChannelGeography=1
SSID=<correct ssid>
NetworkType=Infra
WirelessMode=7
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
AuthMode=WPA2PSK
EncrypType=TKIP
WPA2PSK=<key>
DefaultKeyID=1
Key1Type=0
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

``````

iwconfig ra0
ra0       RT2870 Wireless  ESSID:"<correct ssid>"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <correct AP address>
          Bit Rate=130 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=89/100  Signal level:-56 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

iwpriv ra0 get_site_survey
ra0       get_site_survey:
Ch  SSID             BSSID                 Enc     Auth      Siganl(%)  W-Mode  NT
1   <correct ssid>   <correct AP address>  AES     WPA2PSK   91         11b/g/n In

``````

sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:24:01:14:68:91
Sending on   LPF/ra0/00:24:01:14:68:91
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

``````

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         DslRouter       0.0.0.0         UG    0      0        0 eth0

```* I tried manually adding ra0 entries here but it didn't help any.

---

### Post by UMP on 2010-03-29
bump.

Any suggestions at all, even an alternative dongle that will do what I need, would be greatly appreciated.

---

### Post by chili555 on 2010-03-29
I gather that the problem is that XMBC has no type of network manager. I think you might have better luck if you set up /etc/network/interfaces and /etc/wpa_supplicant.conf.

Here is how to create /etc/wpa_supplicant.conf: [http://wiki.archlinux.org/index.php/WPA_supplicant#Classic_method:_wpa_supplicant.conf](http://wiki.archlinux.org/index.php/WPA_supplicant#Classic_method:_wpa_supplicant.conf)

The corresponding /etc/network/interfaces would look like this example:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
 

#auto eth0
iface eth0 inet dhcpIt should start on boot. Let us know how it goes.

---

### Post by UMP on 2010-03-30
I'd already run through 2 'howto' wpa supplicant guides without any luck but I gave your link a try... and it works! Well, I can get onto the network, get conf via DHCP and ping Google. I'm happy enough for now and will pick up the rest after work.

Thanks a lot Chilli!

(incidentally, the lines that were different from my previous config were proto, pairwise and group, in case that helps any future readers)

---

