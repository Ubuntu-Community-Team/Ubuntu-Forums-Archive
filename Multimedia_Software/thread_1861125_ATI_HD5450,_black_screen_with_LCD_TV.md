---
title: "ATI HD5450, black screen with LCD TV"
date: 2011-10-15
forum: Multimedia Software
---

### Post by sonicb00m on 2011-10-15
I am connecting to an LCD TV through the HDMI which is working perfectly well as long as the TV is turned on before boot. If the tv isn't on then X doesn't detect it and a black screen is present. If I kill X then it reloads with the picture.

Obviously X is at fault here and an apparent fix for Nvidia cards is to put

Option "UseDisplayDevice" "DFP"

in xorg.conf but this doesn't have any effect for me.

---

