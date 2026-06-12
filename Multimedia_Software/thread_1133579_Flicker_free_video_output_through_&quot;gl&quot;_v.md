---
title: "Flicker free video output through &quot;gl&quot; video driver with ATI fglrx in jaunty 9.04"
date: 2009-04-23
forum: Multimedia Software
---

### Post by nkef on 2009-04-23
The driver in ubuntu restricted repository is not final 9.4, which can be downloaded from amd site.

I downloaded tha driver from AMD site and built the packaged for 9.04,
now the package version is :

xorg-driver-fglrx_8.602-0ubuntu1_amd64

and the module release string

ATI Proprietary Linux Driver Release Identifier: 8.602 

In the final release the Redirected Direct Rendering is enabled, so the gl video output is usable alongside with compiz.

I tested the driver with mplayer and i got flicker free with good image quality with gl video output, with vlc i got flicker-free but dithered output.

Has anyone verified the problematic vlc video output with video gl driver +compiz in fglrx in 9.04?

---

### Post by nkef on 2009-04-25
I am uploading the output i get with vlc through gl video output, the distortion is more obvious around the letters.

[IMG]http://img211.imageshack.us/img211/4325/53916042.png[/IMG]

I found no fix for the moment.

---

