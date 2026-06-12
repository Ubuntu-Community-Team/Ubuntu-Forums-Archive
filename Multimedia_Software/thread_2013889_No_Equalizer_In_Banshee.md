---
title: "No Equalizer In Banshee"
date: 2012-07-01
forum: Multimedia Software
---

### Post by Precipitous on 2012-07-01
I am running a fresh install of Banshee 2.4.1 in a fresh install of Ubuntu 12.04, and have all of the community extensions installed.  When I go to the View menu the Equalizer selection is greyed out.  Attempting to launch it by using the keyboard shortcut Ctl+E fails too... 

If I launch Banshee via the terminal by running: banshee --debug I see the following (excerpt):

[1 Debug 09:18:23.962] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 09:18:24.139] Player state change: NotReady -> Ready
[1 Debug 09:18:24.145] Loaded equalizer presets: 0.000269
[1 Debug 09:18:24.155] Selected equalizer: Rock

Does anyone know what is going on? Or at the very least, where "Rock" is being selected as the default setting? I can not find it anywhere in any of the configuration files.

---

### Post by shmibs on 2012-09-07
i can confirm that this issue is present in more than one place. i'm also running 12.04, and have installed from the banshee-team ppa, and am having the exact same issue as above.

---

