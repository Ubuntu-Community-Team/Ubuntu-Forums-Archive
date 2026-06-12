---
title: "Tried updating ATI Drivers"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Waffles385 on 2008-03-07
I tried to update my ATI drivers from the version that comes with 1.10 to the new 8.3 drivers, but now when I run fglrxinfo I get this as my output:

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)


I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and I thought it went okay until the verification. When I rebooted, fglrxinfo kept said I was using Mesa, so I checked the Restricted Drivers. It said In Use, but I put a check in Enabled and rebooted. It now has the check and says In Use but fglrxinfo still says Mesa. Any advice?

---

### Post by db0 on 2008-03-08
I can confirm I've got the exact same problem :(

My xorg.log does not returns any errors

---

