---
title: "ATI x1300 support in Ubuntu 12.04"
date: 2013-01-23
forum: Multimedia Software
---

### Post by shapster94 on 2013-01-23
I am aiming to play TF2 on my system using this graphics card. Whenever I attempt to launch the game I get an error saying that either I need new OpenGL drivers or to get a new card. I have tried installing the ati drivers off their website but get this error:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-25-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro

Could someone please either explain why this happens or better still help me find a solution?

---

### Post by Yellow Pasque on 2013-01-23
For a card that old, the open-source radeon driver is the only option, so please don't try to download/install proprietary drivers from AMD. See if the mesa driver supports the grep GL_EXT_texture_sRGB_decode for r300-r500 cards:
```
sudo apt-get install mesa-utils
glxinfo
```

Really, you're better off getting a newer/better card if you want to play Steam games in Linux (nvidia gtx650Ti or gtx660 is ideal).

---

