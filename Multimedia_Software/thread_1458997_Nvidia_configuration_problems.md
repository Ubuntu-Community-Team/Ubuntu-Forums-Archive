---
title: "Nvidia configuration problems"
date: 2010-04-20
forum: Multimedia Software
---

### Post by mysterian077 on 2010-04-20
I have an Nvidia Graphics card, and until recently I was having problems getting the resolution to stick after restarting the X Server. What I ended up doing was running
```
sudo nvidia-xconfig
``` from a terminal to generate a working xorg.conf file, then I could use the Nvidia settings applet to configure the display and save my settings to the configuration file so that they would load when the server was started. Works great!

Just figured I'd share my experiences. If this is not the correct forum for this topic, please correct it's placement.

---

