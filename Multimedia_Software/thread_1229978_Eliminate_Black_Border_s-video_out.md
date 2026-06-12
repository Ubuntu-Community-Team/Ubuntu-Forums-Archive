---
title: "Eliminate Black Border s-video out"
date: 2009-08-02
forum: Multimedia Software
---

### Post by rowbird on 2009-08-02
Hi, I was wondering if anyone successfully eliminated the black border when s-video out to flat screen T.V.. I have a 50" plasma, and am worried about burn in of the black border which surrounds the picture. I have tried it on several different computers, and distros including Ubuntu 8.04, 8.1, xubuntu 8.04, and Mepis 8. My Video cards are Laptop: Intel Corporation Mobile 945GM/GMS, 943/940GM, and Desktop: NVidia MX440, with NVidea Driver, and Twinview setup. Any help would be greatly appreciated. Thanks.

---

### Post by rowbird on 2009-08-03
Fixed For NVidia: I installed nvidia-settings and nvtv packages from repos, and increased the TVOverscan to 15 fron 8, on the Plasma. It does not retain the overscan setting, but setting it each time before playing a movie is not a big deal. Without nvtv package there is no Overscan option available. Note: Must run sudo NVidia-settings to keep the settings for next boot, except overscan, which didn't stay put.

---

