---
title: "Display has lines through everything after installing NVIDIA driver"
date: 2011-01-14
forum: Multimedia Software
---

### Post by chriseid on 2011-01-14
Im running Ubuntu 10.10 on an Nvidia ION gpu. I've installed the latest driver using the built in driver tool and by downloading from nvidia. Both times this has been the result at every resolution:

[http://img695.imageshack.us/i/img2011011400037.jpg/](http://img695.imageshack.us/i/img2011011400037.jpg/)

[http://img683.imageshack.us/i/img2011011400038.jpg/](http://img683.imageshack.us/i/img2011011400038.jpg/)

Does anyone know what I can do?

Thank you for your help. Im lost at this point.

---

### Post by BicyclerBoy on 2011-01-14
I would go back to a previous driver version.
Install an old one from Ubuntu repos.

What version did you install ?

Check the forums for ION stuff on forums like nv.forums mythtv xbmc..
Maybe be an ION regression..

I would also recommend non-experts to not use the nvidia installer process. You do not need to.
The nvidia method requires you to have kernel headers & run from console log on.
You have to rerun the installer after every kernel update.

Search for 3rd party ppa with latest nvidia driver.
These are often associated with mythtv xbmc nvidia mplayer etc

[http://www.nvnews.net/vbulletin/showthread.php?t=157888](http://www.nvnews.net/vbulletin/showthread.php?t=157888)

Read one of the mythtv developers recommending version 256.

I have found 260.19.29 on GT240 to be excellent.

---

### Post by chriseid on 2011-01-15
Thanks a lot for the link. Im going to downgrade now. Hopefully that works.

---

### Post by BicyclerBoy on 2011-01-15
That link may not have downgrades except by version forcing..

I meant downgrading by "upgrading" to ubuntu repos nvidia driver.. 


Some ION mobos need more system RAM (2 sticks) to get enough GPU video RAM.
Some of the old ones have slower FSB.
Recommended 512MB for 1080 vdpau.

Also try increasing vdpaubuffersize in playback profile vdpau etc. Search web for values etc.

Don't try to use vdpauhqscaling etc.
Don't try to use vdpau high quality (max PQ 2x VA de-interlacing)

---

