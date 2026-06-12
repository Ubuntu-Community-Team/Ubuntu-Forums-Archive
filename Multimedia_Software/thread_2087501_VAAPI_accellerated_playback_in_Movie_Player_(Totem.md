---
title: "VAAPI accellerated playback in Movie Player (Totem) on 12.10?"
date: 2012-11-23
forum: Multimedia Software
---

### Post by cdysthe on 2012-11-23
Hi,

If I install the gstreamer vaapi packages and driver availble for 12.10 will I get accellerated playback in Movie Player (Totem)? I have Intel graphics on my laptop which allows for vaapi accellerated playback. I know you can get vaapi support in mplayer, but I prefer a gstreamer based player like Movie Player (Totem). If there's other steps I need to take to get vaapi support using Movie Player please advice.

---

### Post by BicyclerBoy on 2012-11-24
This package:
libva-intel-vaapi-driver
The VAAPI driver for Intel G45 & HD Graphics family
Without this package none of the other vaapi stuff will work.
There is a cedarview specific driver..

Older h/w transitional package
i965-va-driver

& install/run/test
vainfo.

I would suggest that to get any performance from recent intel GPU then you need xorg-edgers ppa (update all packages, do not pick just one item)

---

### Post by freechelmi on 2013-03-16
> **cdysthe said:**
> Hi,

If I install the gstreamer vaapi packages and driver availble for 12.10 will I get accellerated playback in Movie Player (Totem)? I have Intel graphics on my laptop which allows for vaapi accellerated playback. I know you can get vaapi support in mplayer, but I prefer a gstreamer based player like Movie Player (Totem). If there's other steps I need to take to get vaapi support using Movie Player please advice.

Totem cannot currently support gstreamer-vaapi, the team is working on it, it needs a completely revamp of the way totem use gstreamer

---

### Post by andrew.46 on 2013-03-16
Mind you *official *support for vaapi for MPlayer is still some way off. A safer bet would be vlc...

---

