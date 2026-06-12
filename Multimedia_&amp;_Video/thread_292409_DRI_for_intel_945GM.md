---
title: "DRI for intel 945GM"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by siliconeagle on 2006-11-03
hi there ,

i am trying to get DRI going on my new laptop and have run it a snag hopefully someone might know something about.

Basically the i915_dri.so seem to be out-of sync with libGL when i run xriinfo i get.
```
robm@robm-laptop:/media/sda6/media/video/jap_com/mpg$ xdriinfo
libGL: XF86DRIGetClientDriverName: 1.4.1 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL: XF86DRIGetClientDriverName: 1.4.1 i915 (screen 0)
Screen 0: i915
libGL error: XF86DRIQueryDirectRenderingCapable returned false
Screen 1: not direct rendering capable.
```

on the DRI troubleshooting ([http://dri.freedesktop.org/wiki/DriTroubleshooting]("http://dri.freedesktop.org/wiki/DriTroubleshooting")) page it says:-
> then your libGL is out of sync with your DRI drivers. Because APIs change, you typically need a libGL from the latest X.Org release to run DRI drivers, and sometimes you need a libGL from X.Org CVS for the latest drivers. Reinstall both your drivers and your libGL from sources from the same date.

so i was just wondering if anyone has done this, or if there are deb packages i should try first before trying to complie. or if there are updated ubuntu packages i could try for libgl1-mesa & libgl1-mesa-dri.

any ideas most welcome - thanks in advance.

---

### Post by siliconeagle on 2006-11-07
actually funnily enough i had to reinstall this box for a different reason, and DRI worked out straight away of the box!! 

So i am not exactly sure what caused it but i think it is this:- there is an upgrade still waiting for xesrver-xorg (ubuntu10)which i have mot installed as i think it is this as ther eis a fix for intel chipset bridging or something in there.

No I just want to get it working on my external montior instead of my laptop one since i do audiovisual work and need to be able to project it. 

has anyone out there managed to set up DRI to run on their external monitor. it seem like it should be fairly easy eith change the screen numbers or use the FlipPrimary flag in the Device Section, but nothing seems to work. 

always the display :0.0 is my laptop monitor when i want it to be my external monitor.

anyone out the have any ideas?

---

### Post by siliconeagle on 2006-11-08
ok i found out you just have to swicth you monitor to external before x starts up and then the prmary monitor is the external one. guess that was pretty obvious really.

---

