---
title: "PiTiVi - &quot;Could not initiate the video output plugins&quot; at startup"
date: 2013-05-10
forum: Multimedia Software
---

### Post by nanuqcz on 2013-05-10
Hi, 
I installed PiTiVi video editor. But when I start it, only error is shown: 
```
Could not initiate the video output plugins

Make sure you have at least one valid video output sink available (xvimagesink or ximagesink).
```

I searched for "xvimagesink" and "ximagesink" keyword in Synaptics, bot nothing found. 

Please help me.

---

### Post by nanuqcz on 2013-05-11
Fixed with install [COLOR=#000000][FONT=Verdana]gstreamer-plugins version 1.0. 

But when I load video to PiTiVi, preview window is always black, I can only hear the sound, when I start imported video in PiTiVi. 

Please help. [/FONT][/COLOR]

---

### Post by TheodoreWard on 2013-06-02
> **nanuqcz said:**
> Hi, 
I installed PiTiVi video editor. But when I start it, only error is shown: 
```
Could not initiate the video output plugins

Make sure you have at least one valid video output sink available (xvimagesink or ximagesink).
```

I searched for "xvimagesink" and "ximagesink" keyword in Synaptics, bot nothing found. 

Please help me.

It's probably due to upgrading from 12.10 to 13.04 but I had to install ges0.10-tools to get pitivi to start.

---

