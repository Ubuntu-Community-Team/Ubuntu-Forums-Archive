---
title: "beryl, nvida, and no sound"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by spartan777 on 2007-02-05
I installed the latest nvidia drivers (1.0-9746) and the latest version of Beryl (1.9999.1). everything goes swimmingnly, except that when I have beryl begin at startup, I have no sound. things are fine if I start in metacity, and then turn on beryl, or just stay in metacity. how do I fix this? I have an Audigy 2 soundcard, use regular ubuntu (no fancy kernels), and have an Nvidia 6800gt.

---

### Post by spartan777 on 2007-02-05
I solved the problem, it had noting to do with beryl. I looked in sound properties, and for some reason, ubuntu would choose my onboard sound (which is disabled in the BIOS) randomly on some startups, and my soundcard on the others.

---

