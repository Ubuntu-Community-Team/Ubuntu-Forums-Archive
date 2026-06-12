---
title: "TechniSat SkyStar HD2 tuning failed"
date: 2013-12-10
forum: Multimedia Software
---

### Post by scarabol on 2013-12-10
Hi,

i try to get my TechniSat SkyStar HD2 to work.

scan fails:
```

root@dvb3:~# scan -n /usr/share/dvb/dvb-s/Astra-19.2E
scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12552000 V 22000000 5
>>> tune to: 12552:v:0:22000
DVB-S IF freq is 1952000
WARNING: >>> tuning failed!!!
>>> tune to: 12552:v:0:22000 (tuning failed)
DVB-S IF freq is 1952000
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

w_scan results in a long, but empty list:
```
root@dvb3:~# w_scan -fs -s S19E2 -G -a 0 >> astra1.conf
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for 19.2 east Astra 1F/1G/1H/1KR/1L
scan type SATELLITE, channellist 67
output format gstreamer
output charset 'UTF-8', use -C <charset> to override
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'STB0899 Multistandard' supports
INVERSION_AUTO
DVB-S
DVB-S2
FREQ (0.95GHz ... 2.15GHz)
SRATE (5.000MSym/s ... 45.000MSym/s)
using LNB "UNIVERSAL"
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
trying 'S2 f = 10729 kHz V SR = 22000  2/3 0,35  8PSK'
(time: 00:01) (time: 00:03) 
.... an so on

```

At least the card is detected by the system and shown as /dev/dvb/adapter0/
```
root@dvb3:~# ls /dev/dvb/adapter0
demux0  dvr0  frontend0  net0
```

Also lspci -v looks good:
```
01:08.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
    Subsystem: Device 1ae4:0003
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at e0001000 (32-bit, prefetchable) [size=4K]
    Kernel driver in use: Mantis
```

Im using Kernel 3.11.0-12-generic under Ubuntu 13.10 and i tried the latest driver from [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)

Any other hints or help appreciated!

Regards
Scarabol

---

### Post by viderbit on 2013-12-11
Hello,
I have the exact same problem like you. My TechniSat SkyStar HD2 refuse to play any S2 transponder channel with 8PSK and 3/4 FEC on Hellas Sat 2.
Tvheadend report that the signal is below 10%, but I can watch every DVB-S channel without any problem and also I can watch all DVB-S2 channels on my sat receiver, so the problem is in the PCI card or drivers.
I have the same drivers like you - latest git version from linuxtv. So please - if anyone can help with this issue, we will be much appreciated!

Wiki info about the card: [B][TechniSat SkyStar HD2 aka Azurewave AD SP400 CI (VP-1041)]("http://www.linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_(VP-1041)").

[/B]

---

