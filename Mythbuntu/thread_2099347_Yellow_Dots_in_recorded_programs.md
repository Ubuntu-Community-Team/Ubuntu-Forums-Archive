---
title: "Yellow Dots in recorded programs"
date: 2012-12-29
forum: Mythbuntu
---

### Post by drifting on 2012-12-29
Since my upgrade from 11.* and upgrade from .24 to .26 I have seen quite a few yellow dots in recorded items. A quick read up says that they are failed recordings. However mine seem to be all there, but have had a few with the off drop in audio, followed by a sort of loud click. This seems to only happen on DVB-S recordings. But is really random, as I have many other recording from the same cards that are fine.

Did notice this in the logs, but a quick google did not bring up anything recent about the issue:-

Dec 29 13:05:06 vs mythlogserver: mythbackend[16858]: E DVBRead mpeg/mpegstreamdata.cpp:817 (ProcessPAT) ProcessPAT: Program not found in PAT. Rescan your transports.
Dec 29 13:05:06 vs mythlogserver: mythbackend[16858]: E DVBRead mpeg/mpegstreamdata.cpp:423 (CreatePATSingleProgram) Desired program #10351 not found in PAT.#012#011#011#011Cannot create single program PAT.

Anyone an idea ?

Paul

---

