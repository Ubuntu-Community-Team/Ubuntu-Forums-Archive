---
title: "Sound issue at X server workload"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Teloid on 2008-04-30
Hello, after upgrade from Dapper to Hardy I have strange sound issue with my M-Audio Audiophile 2496. At 6.06 it works properly with alsa, but after upgrade on any Xorg load(CPU load) sound slowdown and crack. At CPU load initialized not by Xorg sound work fine. 
I don't now why, but after upgrade from dapper Xgl replaces Xorg, and at that configuration sound work very bad at any window drawing, I remove package xserver-xgl, and X server back to Xorg, but sound problem doesn't disappear(but better then with Xgl). 3D acceleraion works, and compiz works, but I turned it to "No effects" at configuration menu.
I tried to reinstall  and reconfigure alsa, but that didn't help.

P.S. I upgrade Dapper with do-release-upgrade tool, because GUI tools failed to upgrade.
P.P.S I have nvidia 6600, nvidia drivers at 100 series and 1,3 Ghz CPU.

---

