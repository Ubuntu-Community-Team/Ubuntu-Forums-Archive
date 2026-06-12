---
title: "Myth, Ubuntu 18.04 Tuner cards not working"
date: 2019-08-06
forum: Multimedia Software
---

### Post by drifting on 2019-08-06
This has been working great, just updated the Ubuntu and now for some reason all my cards are detected as the same? Huh?

[ 7.613301] SAA716x Budget 0000:02:00.0: DVB: registering adapter 2 frontend 0 (TurboSight TBS 6280 DVB-T/T2/C)...
[ 7.650023] SAA716x Budget 0000:02:00.0: DVB: registering adapter 3 frontend 0 (TurboSight TBS 6280 DVB-T/T2/C)...
[ 8.407940] SAA716x Budget 0000:03:00.0: DVB: registering adapter 0 frontend 0 (TurboSight TBS 6982SE DVB-S/S2)...
[ 8.736630] SAA716x Budget 0000:03:00.0: DVB: registering adapter 1 frontend 0 (TurboSight TBS 6982SE DVB-S/S2)...

Should be like this :-


[ 3.816541] TBSECP3 driver 0000:30:00.0: DVB: registering adapter 0 frontend 0 (TurboSight TBS 6281SE DVB-T/T2/C )...
[ 3.914592] SAA716x Budget 0000:20:00.0: DVB: registering adapter 2 frontend 0 (TurboSight TBS 6982SE DVB-S/S2)...
[ 3.984506] TBSECP3 driver 0000:30:00.0: DVB: registering adapter 1 frontend 0 (TurboSight TBS 6281SE DVB-T/T2/C )...
[ 4.224809] SAA716x Budget 0000:20:00.0: DVB: registering adapter 3 frontend 0 (TurboSight TBS 6982SE DVB-S/S2)...

What on earth is going on? Any help really appreciated. Same compiled driver as before, mystified.

Paul.

---

### Post by drifting on 2019-08-06
Oh my, so sorry I am a complete idiot. Just found out my Grandson changed the tuner, he throught he was being helpful as the last one died.
So different question, how on earth to I get the other to stay stable now? as they all use the SAA716x ?

---

