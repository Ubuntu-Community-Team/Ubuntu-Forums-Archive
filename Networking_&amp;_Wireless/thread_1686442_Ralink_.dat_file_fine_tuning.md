---
title: "Ralink .dat file fine tuning"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by ilna on 2011-02-12
Hi!

Ralink's drivers for wireless adapters [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) go with .dat-file to configure default properties of used WiFi adapter (at my case - RT2870.dat). Example is below.

I'd want to fine tune adapters (I have two of them) to get maximum performance for streams **between two WiFi clients connected to my router** (JWNR2000 at my case).

At the moment I have changed WirelessMode=6 to force 802.11n mode (and it does work). Speed between WiFi-clients is about 3MB/s now. **I want more :) How to??**

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=RU
ChannelGeography=1
SSID=<myAP>
NetworkType=Infra
WirelessMode=6
Channel=11
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
EncrypType=AES
WPAPSK=<myKey>
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
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
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
PSP_XLINK_MODE=0

```

---

### Post by ilna on 2011-02-12
Can not believe there isn't wireless guru in Ubuntu community.. :o Does nobody care? :frown:

---

