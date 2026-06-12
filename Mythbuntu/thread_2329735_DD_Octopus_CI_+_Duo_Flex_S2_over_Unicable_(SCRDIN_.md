---
title: "DD Octopus CI + Duo Flex S2 over Unicable (SCR/DIN EN 50494) = no lock/channels"
date: 2016-07-04
forum: Mythbuntu
---

### Post by manuel_acs on 2016-07-04
Hallo,

have troubles to create a channels.conf for MythTv

SetUp:
Mythbuntu 16.04 (clean install) as Secondary Backend + Frontend role
on HTPC with Asus board with AMD E-450 
+ Digital Devices Octopus CI (with ddbridge driver from DD) 
+ 2x Duo Flex S2 (integrated driver from ubuntu) 
on 4-Way Splitter over 1 cable (Unicable/SCR/DIN EN 50494) to Multiswitch/LNB with Astra19E2
--> bridge and both cards will be found and 6 frontends are under /dev/dvb/adapter0-3 + 4&5 from the CI...
(Master Backend on my Homeserver with Proxmox VE as KVM Guest)

In MythTv when i make a full scan tuned on 1 transponder (10744000) --> time out
... googled around ... initial scan in Myth is a mess ... --> use external scan tool
--> w_scan and dvbv5-scan supports unicable

when i use w_scan with:
```
w_scan -f s -s S19E2 -c AT -G > /home/manuel/channels.conf -l ENHANCED -vvvv -u 1:1178:A -a 0
```

(sorry - did not found the spoiler)
> w_scan -f s -s S19E2 -c AT -G -l ENHANCED -vvvv -u 1:1178:A -a 0 
w_scan version 20141122 (compiled for DVB API 5.10)
using settings for 19.2 east Astra 1F/1G/1H/1KR/1L
SCR: slot=1, userfreq=1178MHz, satpos=A, pin=-1
scan type SATELLITE, channellist 67
output format gstreamer
output charset 'UTF-8', use -C <charset> to override
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.10
frontend 'STV090x Multistandard' supports
INVERSION_AUTO
DVB-S
DVB-S2
FREQ (0.95GHz ... 2.15GHz)
SRATE (1.000MSym/s ... 45.000MSym/s)
using LNB "ENHANCED"
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
   check STV090x Multistandard:
           DSS
           DVB-S2
           DVB-S
trying 'S2 f = 10729 kHz V SR = 22000  2/3 0,35  8PSK  (0:0:0)'
(time: 00:00.012) 
        (1.960sec): SC (0x3)
        (1.960sec) signal
        (4.264sec):  (0x0)
        (6.084sec): SC (0x3)
trying 'S  f = 10744 kHz H SR = 22000  5/6 0,35  QPSK  (0:0:0)'
(time: 00:06.259) 
        (1.228sec): SC (0x3)
        (1.228sec) signal
        (1.280sec):  (0x0)
        (1.332sec): SC (0x3)
        (2.440sec):  (0x0)
        (5.956sec): SC (0x3)
trying 'S  f = 10759 kHz V SR = 22000  5/6 0,35  QPSK  (0:0:0)'
(time: 00:14.071) 
        (1.284sec): SC (0x3)
        (1.284sec) signal
        (1.336sec):  (0x0)
        (2.444sec): SC (0x3)
        (2.496sec):  (0x0)
trying 'S2 f = 10773 kHz H SR = 22000  3/4 0,20  8PSK  (0:0:0)'
(time: 00:20.803) 
        (1.040sec): SC (0x3)
        (1.040sec) signal
        (1.092sec):  (0x0)
        (1.456sec): SC (0x3)
        (2.032sec):  (0x0)
        (4.736sec): SC (0x3)
....
....
....
trying 'S2 f = 12725 kHz H SR = 30000 AUTO 0,AUTO  8PSK  (0:0:0)'
(time: 09:21.467) 
        (1.332sec): SC (0x3)
        (1.332sec) signal
        (1.384sec):  (0x0)
        (1.644sec): SC (0x3)
        (2.700sec):  (0x0)
trying 'S  f = 12729 kHz V SR = 22000  5/6 0,35  QPSK  (0:0:0)'
(time: 09:26.523) 
        (1.772sec): SC (0x3)
        (1.772sec) signal
        (2.312sec):  (0x0)
        (4.292sec): SC (0x3)
        (4.344sec):  (0x0)
        (4.500sec): SC (0x3)
        (4.552sec):  (0x0)

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!


when i use dvbv5-scan with:
```
dvbv5-scan -CAT -U1383 -I dvbv5 Astra192 -lENHANCED -w1 -a0
```

> Using LNBf ENHANCED
        Astra
        10700 to 11700 MHz
        Single LO, IF = 9750 MHz
Device STV090x Multistandard (/dev/dvb/adapter0/frontend0) capabilities:
     CAN_2G_MODULATION
     CAN_FEC_AUTO
     CAN_INVERSION_AUTO
     CAN_QPSK
DVB API Version 5.10, Current v5 delivery system: DVBS
Supported delivery systems:
    [DVBS]
     DVBS2
     DSS
Cannot calc frequency shift. Either bandwidth/symbol-rate is unavailable (yet).
Scanning frequency #1 10744000
DEBUG    LNA is ON
DiSEqC VOLTAGE: 18
DiSEqC TONE: OFF
FREQUENCY = 10744000
INVERSION = AUTO
SYMBOL_RATE = 22000000
INNER_FEC = 5/6
POLARIZATION = HORIZONTAL
DELIVERY_SYSTEM = DVBS
Status:
BER: 8388608, Strength: 65436, SNR: 0, UCB: 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for POST BER = 8388608
Status:
BER: 8388608, Strength: 65436, SNR: 0, UCB: 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for POST BER = 8388608
Status:
BER: 8388608, Strength: 65436, SNR: 0, UCB: 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for STATUS = 0
DEBUG    Stats for POST BER = 8388608
Status:
....
....
....
Status:
    CARRIER
    SIGNAL
BER: 8388608, Strength: 65436, SNR: 0, UCB: 0
DEBUG    Stats for STATUS = 3
DEBUG    Stats for STATUS = 3
DEBUG    Stats for STATUS = 3
DEBUG    Stats for POST BER = 8388608
Status:
    CARRIER
    SIGNAL
BER: 8388608, Strength: 65436, SNR: 0, UCB: 0
DEBUG    Stats for STATUS = 3
DEBUG    Stats for STATUS = 3
DEBUG    Stats for STATUS = 3
DEBUG    Stats for POST BER = 8388608
....
....
....
DiSEqC VOLTAGE: OFF

it seems, both finding something (SC (0x3) signal/CARRIER SIGNAL) but will not lock.
have  testet both with all UB (userbands) 1178, 1280, 1383, 1484... SAT  position A/B, different LNB (STANDARD, UNIVERSAL, ENHANCED)... aso...  without switch, other cable and switch from my working SAT-Receiver  (AZBox Premium - ready to use mini Linux with VDR) with dual tuner.

on  my AZBox i just select the Tuner (A/B) Astra 19E2, unicable, fill in  one of the 4 UB, check Power to LNB, select first transponder 10729 kHz  from the list, select NIT, TV+Radio, encryptet and not encryptet, press  search and find all ~1360 channels in ~15 min.

i would be gratefull for any hints or kick in the right direction :)

thanks
Manuel

---

