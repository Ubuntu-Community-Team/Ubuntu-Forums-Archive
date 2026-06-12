---
title: "troubles with EEE-901: rt2860 wlan. connection disruption"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by juliank on 2010-10-31
hi guys,

I'm owner of an Asus EEE 901. It has a Ralink RT2860 wireless chipset and worked fine for the last Ubuntu releases.
Now, I've got some problems with my wireless connection on Maverick.

'Everything' works fine so far. This means, I see all networks and can connect to them. But all networks have a quality of 100%, which is impossible. My own access point is 2 levels below and had a quality about 50% when I ran Lucid.
The Signal levels of all wireless networks is about -180dBm.

This sounds that bad, but there is another effect which annoys me much more:
The connection at home is very slow and sometimes it takes some seconds until the netbook recieves or sends data. (WPA2)
The problem gets worse when I'm at my university. They provide WEP-network with a VNP connection to the internet. It's very lucky to get a stable connection, because the connection gets lost in short intervals (but sometimes it works for hours). The wireless networks works fine at notebooks from my colleagues.

I get this error sometimes, when the wireless connection is established an I try to connect to vpn:
```
vpnc-connect: expected xauth packet; rejected:  (ISAKMP_N_UNEQUAL_PAYLOAD_LENGTHS)(30)
```

I'm not sure, but I think there could be a correlation between the strange signal strength and the connection problems!?

Some data from my netbook:
Ubuntu 10.10 Maverick Meerkat
Kernel 2.6.35-22-generic

**lspci -nn | grep -i net**
```
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
04:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
```

**iwconfig**
```
wlan0     IEEE 802.11bgn  ESSID:"myHOMENETWORK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: myMACADDRESS 
          Bit Rate=24 Mb/s   Tx-Power=3 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-188 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**modinfo rt2860sta**
```
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     1CC5B0F527E33CC4AF73D2B
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*    ##this line a few times
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```

**lsmod** (without unnecessary data, hopefully)
```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
rt2860sta             504366  0 
rt2800pci               8565  0 
rt2800lib              28897  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
rt2x00lib              27275  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
mac80211              231541  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci
led_class               2633  2 rt2x00lib,eeepc_laptop
```


Does someone have a clue on this?

---

### Post by Der Ritter on 2010-10-31
> **juliank said:**
> 


```
vpnc-connect: expected xauth packet; rejected:  (ISAKMP_N_UNEQUAL_PAYLOAD_LENGTHS)(30)
```

This was apparently a known problem with vpnc. Unfortunately it appears that the bug never was fixed as shortly after the developer said he would be fixing it in the next version he quit working on vpnc, so there is no next version.

[This workaround](http://osdir.com/ml/network.vpnc.devel/2008-07/msg00041.html) was suggested for someone who had the same issue. But if that doesn't work, are you sure there isn't another, actively maintained program you can use?

But in any case you are right that the signal strength is wacky. -188 dBm approximately corresponds to 158.5 yoctowatts, or 1.585*(10^-22) watts. That, according to Wikipedia, is less than the power of the Galileo space probe's signal when it was received at Earth. (Galileo's mission was to study Jupiter -- the signal was being sent over hundreds of millions of kilometres!) Obviously there is no way the signal could be that weak. But I don't think that would cause problems with the connection...?

---

### Post by juliank on 2010-10-31
Thank you for your reply.

The error of vpnc appears rarely and I think it could correspond to the strange wlan strength?!
Most of the time vpnc works fine. I've found no other working vpn client so far. The connection to the VPN from my university requires some extra settings, which other clients don't provide.
(IPSec secret ..., Application Version Cisco Systems VPN Client 4.8.0:Linux)

I don't think that the odd signal strength causes the connection problems, but it could be an indication that something is wrong with my wlan driver?!

---

