---
title: "USB DVB-T not finding channels"
date: 2011-12-04
forum: Multimedia Software
---

### Post by FlamingSpaz on 2011-12-04
Hello all,

I'm having a problem with my Pinnacle PCTV Hybrid Pro Stick (*320e*). for some reason it won't find any channels. I have installed the v4l firmware v3 but I don't know what to do now. I live in greater London if it helps. I'm running Ubuntu 11.10.

Here's the scan output:

```
spaz@TUXTOP:~$ scan /usr/share/dvb/dvb-t/uk-HemelHempstead -o zap | tee channels.conf
scanning /usr/share/dvb/dvb-t/uk-HemelHempstead
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 690167000 0 3 9 1 0 0 0
initial transponder 746000000 0 2 9 3 0 0 0
initial transponder 786167000 0 2 9 3 0 0 0
initial transponder 777833000 0 3 9 1 0 0 0
initial transponder 802000000 0 3 9 1 0 0 0
initial transponder 826000000 0 3 9 1 0 0 0
>>> tune to: 690167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 690167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 746000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 746000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 786167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 786167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 777833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 777833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 802000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 802000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 826000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 826000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

---

### Post by MartyBuntu on 2011-12-04
You have an antenna hooked up, correct?

---

### Post by BicyclerBoy on 2011-12-04
dmesg | grep dvb
dmesg | greb firmware

---

### Post by FlamingSpaz on 2011-12-04
> **MartyBuntu said:**
> You have an antenna hooked up, correct?

Of course :)

---

### Post by FlamingSpaz on 2011-12-04
> **BicyclerBoy said:**
> dmesg | grep dvb
dmesg | greb firmware

Seems I'm missing xc3028-v27.fw I'll crawl through the net looking for it.


Thanks a bunch man!

---

### Post by BicyclerBoy on 2011-12-05
Don't crawl the web...
Use synaptic:
install linux firmware package (& the non-free firmware package).

Or look in LinuxTV.org for advice or f/w links ..

---

