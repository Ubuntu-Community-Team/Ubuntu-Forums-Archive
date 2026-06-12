---
title: "No sound with TT premium dvb-c"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by KingCobra on 2006-12-05
I've recently converted from windows to Ubuntu Dapper, and I'm very impressed with it so far, but when I tried to install my Tecnotrend premium C2300 dvb-c card, although I can tune it and get a picture, I just can't get any audio from the card output.
It all works in windows, so I know the hardware is OK.
I'm using the dvb-ttpci-01.fw v2622 in /lib/firmware/2.6.15-27-386, which fails to load properly at start up, but if I  **sudo rmmod dvb_ttpci** to remove it and then  **sudo modprobe dvb_ttpci** to reload it, it appears to work ok ( apart from the sound)
I've tried dvbtune and vdr, both have the same problem.

Anyone got any ideas please ????

---

