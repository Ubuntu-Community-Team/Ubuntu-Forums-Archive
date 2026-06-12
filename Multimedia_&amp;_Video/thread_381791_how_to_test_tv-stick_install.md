---
title: "how to test tv-stick install?"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by pixelstuff on 2007-03-11
I followed guides to install firmware and everything to make my tv stick work  but now I am stuck with how to test if it works. Other users and the guides, at this point, do:
scan -u /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip > channels.conf
If I get it right then, using a template like uk-Mendip, a channels.conf is created and I could put that into the .xine folder? But there is no file in the dvb-t folder for my region, the closest city is in another country. But when I try I get

```
 scan -u /usr/share/doc/dvb-utils/examples/scan/dvb-t/cz-Praha > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/cz-Praha
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 506000000 0 2 9 3 1 2 0
initial transponder 674000000 0 2 9 3 1 2 0
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Where can I go from here?
Thank you!

---

### Post by hackeron on 2007-07-04
having the same problem, did you get this working??

---

### Post by pixelstuff on 2007-07-05
no, never got it working in xine. but  xawtv would find the channels automatically and something there helped me to get a channel info that KDetv needed but never had any sound! can't tell you much more because since the feisty update xawtv crashes my Xorg and I stopped looking for a solution :(

---

