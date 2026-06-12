---
title: "How activate Hw-acceleration?"
date: 2012-05-15
forum: Multimedia Software
---

### Post by Azyx on 2012-05-15
How do I activate Video Acceleration on a Nvidia GT 520? I have the propretary driver 295.49 (Current in 10.04LTS)

I suppose that the AV is not active because vainfo give:
```
Azyx@Intel:~$ vainfo
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```
Should I activate something in (Nvidia X Server Settings)nvidia-settings, or do I need to install OR uninstall other packages?

---

### Post by BicyclerBoy on 2012-05-15
To get VA-API working you need a VDPAU backend for VAAPI..
Called vdpau-va-library or similar.

You might want to check out splitted-desktop systems website for any later versions of vaapi.

VAAPI is a subset of the capabilities of VDPAU.
i.e. better to use native vdpau support in mplayer & mythtv etc if you can..

---

### Post by Azyx on 2012-05-15
> **BicyclerBoy said:**
> To get VA-API working you need a VDPAU backend for VAAPI..
Called vdpau-va-library or similar.

You might want to check out splitted-desktop systems website for any later versions of vaapi.

VAAPI is a subset of the capabilities of VDPAU.
i.e. better to use native vdpau support in mplayer & mythtv etc if you can..

Thanx. Do you mean this site? [http://www.splitted-desktop.com/en/sds.html](http://www.splitted-desktop.com/en/sds.html)  ?

Why is it better to use native vdpau in media-players? Is it better than '[COLOR="Red"]vdpau-va-driver[/COLOR]' under section [COLOR="red"]X11[/COLOR] in Synaptic. Do you know what is i965-va-driver is? Says something that is was originally for Intel but not anymore. 

/Cheers

---

### Post by raptir on 2012-05-15
VDPAU is Nvidia's hardware acceleration package. VA-API was created by Intel, but is open so you can use it with a back end for Nvidia or ATI cards.

Vdpau is probably more powerful, plus you'd be using the native capabilities instead of a wrapper. Vaapi support is fairly new as is (few media players support it well) while vdpau is well supported in mplayer. Try gnome-mplayer with vdpau.

---

### Post by BicyclerBoy on 2012-05-15
VA-API is not as full featured as VDPAU.

VDPAU is an open standard published/used by nVidia..so anyone can implement the VDPAU API.
The nVidia h/w works well with VDPAU unsurprisingly.

Probably because intel driver is open source & well supported by intel, VA-API was choosen to be the universal open source video API.

i965-va is the VAAPI driver for intel GPU 965 chipset graphics (& HD2000/3000 I think).

Link to libva packages..(just for edification):
[http://www.splitted-desktop.com/static/libva/](http://www.splitted-desktop.com/static/libva/)

---

