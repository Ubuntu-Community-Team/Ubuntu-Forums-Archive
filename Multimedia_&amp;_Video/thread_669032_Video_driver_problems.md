---
title: "Video driver problems"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by KevinC442 on 2008-01-16
I restarted X and it went into low-graphics mode. I uninstalled fglrx and reinstalled. When I go to restricted drivers, it says it's enabled but not being used. fglrxinfo commands shows this:
display: :0.0  screen: 0
OpenGL venhttps://help.ubuntu.com/community/BinaryDriverHowto/ATIdor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

I followed the guide to install fglrx here:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

It says if Mesa shows up any where in fglrxinfo there is a problem. I followed the troubleshooting guide but nothing worked. What do I do to fix this? Right now I'm getting very very low fps.

---

### Post by overdrank on 2008-01-16
> **KevinC442 said:**
> I restarted X and it went into low-graphics mode. I uninstalled fglrx and reinstalled. When I go to restricted drivers, it says it's enabled but not being used. fglrxinfo commands shows this:
display: :0.0  screen: 0
OpenGL venhttps://help.ubuntu.com/community/BinaryDriverHowto/ATIdor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

I followed the guide to install fglrx here:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

It says if Mesa shows up any where in fglrxinfo there is a problem. I followed the troubleshooting guide but nothing worked. What do I do to fix this? Right now I'm getting very very low fps.

HI and in the past if the driver is enabled and not in use the I disable the driver reboot then enable the the drivers again and this usually corrects the issue.

---

