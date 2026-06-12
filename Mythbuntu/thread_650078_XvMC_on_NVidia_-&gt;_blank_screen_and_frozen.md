---
title: "XvMC on NVidia -&gt; blank screen and frozen"
date: 2007-12-25
forum: Mythbuntu
---

### Post by gtr33m on 2007-12-25
Hi,

I've installed Mythbuntu from the 7.04 CD and recently upgraded to 7.10 from the update manager

My system is an AMD Athlon 3000 with a NVidia 7300GT AGP video card.

NVidia drivers installed using Envy, version 169.07 which I believe are the latest.

I've checked /etc/X11/XvMCConfig and it contains only

libXvMCNVIDIA_dynamic.so.1

The problem I am having is that when switch TV Settings -> Playback -> Preferred MPEG2 Decoder: from libmpeg2 to Standard XvMC then try to watch Live TV, all I get is a brief showing of the OSD in the original colours, then a blank screen and mythtv is frozen.  Only way I know to get out of it is to reset the system.

Extra audio buffering is on and Enable OpenGL vertical sync for timing is off (result the same if on).

Can anyone point me in the right direction.  I'm a relative newbie, but can post setup files if it helps.

Thanks,

Mark

---

