---
title: "Dlink DWA-125. Cannot set ESSID."
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by RUCorvax on 2012-01-11
Hi,

I need help with configuring Dlink DWA-125 (ralink 5370) on my Ubuntu 11.04 (2.6.38-13-generic).

Here is what I am doing:

#ifconfig ra0 10.100.200.1 netmask 255.255.255.0 up

#iwconfig ra0 mode Ad-Hoc channel auto essid Test

Everyting is fine but ESSID is always empty:
```

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: 46:9E:3C:61:C2:0E   
          Bit Rate=150 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Her is corresponding records from dmesg:
```

[11627.864590] RTMP_TimerListAdd: add timer obj f8810484!
[11627.866383] -->RTUSBVenderReset
[11627.866507] <--RTUSBVenderReset
[11628.353937] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[11628.353950] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[11628.354314] Key1Str is Invalid key length(0) or Type(0)
[11628.354339] Key2Str is Invalid key length(0) or Type(0)
[11628.354364] Key3Str is Invalid key length(0) or Type(0)
[11628.354389] Key4Str is Invalid key length(0) or Type(0)
[11628.354825] 1. Phy Mode = 5
[11628.354827] 2. Phy Mode = 5
[11628.354830] NVM is Efuse and its size =2d[2d0-2fc] 
[11628.400389] phy mode> Error! The chip does not support 5G band 15!
[11628.400577] RTMPSetPhyMode: channel is out of range, use first channel=1 
[11628.404264] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[11628.404271] ESC[31mRT5390_Init: FlgIsHwAntennaDiversitySup --> TrueESC[m
[11628.426638] 3. Phy Mode = 9
[11628.429136] ESC[mAntCfgInit: primary/secondary ant 0/1
[11628.429138] ESC[mESC[31mRT5390SetRxAnt: rt5370G/rt5390R --> switch to mainESC[m
[11628.473525] MCS Set = ff 00 00 00 01
[11628.484098] <==== rt28xx_init, Status=0
[11628.488397] 0x1300 = 00064300
[11637.982103] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[11638.672032] ra0: no IPv6 routers present

```

Don't see where the problem might be here. :(

Thank for your assistance!

---

