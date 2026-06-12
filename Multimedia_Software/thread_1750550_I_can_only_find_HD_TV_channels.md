---
title: "I can only find HD TV channels"
date: 2011-05-05
forum: Multimedia Software
---

### Post by calande on 2011-05-05
Hello,

I just upgraded to Natty, and I use DVB-T television, so I scanned for channels but I found only HD channels:

```
$ scan /usr/share/dvb/dvb-t/fr-Nantes -o zap |tee channels.conf
scanning /usr/share/dvb/dvb-t/fr-Nantes
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 498000000 0 2 9 3 1 0 0
initial transponder 506000000 0 2 9 3 1 0 0
initial transponder 522000000 0 2 9 3 1 0 0
initial transponder 530000000 0 2 9 3 1 0 0
initial transponder 658000000 0 2 9 3 1 0 0
initial transponder 802000000 0 2 9 3 1 0 0
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 530000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 530000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
Network Name 'F'
0x0000 0x0501: pmt_pid 0x006e MR5 -- TF1 HD (running)
0x0000 0x0502: pmt_pid 0x00d2 MR5 -- France 2 HD (running)
0x0000 0x0503: pmt_pid 0x0136 MR5 -- M6HD (running)
>>> tune to: 802000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 802000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: -10:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1519: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: -10:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1519: ERROR: Setting frontend parameters failed: 22 Invalid argument
dumping lists (3 services)
Done.
TF1 HD:658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:120:0:1281
France 2 HD:658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:220:0:1282
M6HD:658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:320:0:1283
```

Could you help me please? :)
Thanks,

---

### Post by calande on 2011-05-08
Any idea? :)

---

### Post by xc3RnbFO8P on 2011-05-08
.

---

### Post by calande on 2011-05-08
Thanks. Oh, but, I'm scanning multiplexers, digital signal, not analog channels...

---

### Post by xc3RnbFO8P on 2011-05-08
Sorry

---

