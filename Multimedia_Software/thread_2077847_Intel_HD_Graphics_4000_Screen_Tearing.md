---
title: "Intel HD Graphics 4000 Screen Tearing"
date: 2012-10-29
forum: Multimedia Software
---

### Post by MikeT23 on 2012-10-29
I have a fairly new HTPC with Intel Ivy Bridge i7 3770t and Intel's HD Graphics 4000 (no separate GPU card). However there is a mild case of screen tearing when the image is changing rapidly - there are horizontal lines where the image is getting split. This happens when playing dvds, TV, YouTube videos etc. When playing video, the System Monitor shows little CPU activity - all 8 threads remain below 20% and average for any thread is well below 10%.

My question is whether I can do anything to optimise the picture (I was hoping that Intel's HD Graphics 4000 would be at least as good as the basic TV when playing a DVD)?

Is anyone else using Intel's HD Graphics 4000 without a separate GPU and if so what's the picture like when video images move fast?

Does anybody have any suggestions?

My system:
Chip: Intel Ivy Bridge i7 3770t
GPU: Intel's Intel's HD Graphics 4000
TV card: BGT3630
Kubuntu: 12.04
Kernel: 3.2.0-26-generic
Me: relative newbie

Other info:
glxinfo:
```
 OpenGL version string: 2.1 Mesa 8.0.4
 OpenGL vendor string: Tungsten Graphics, Inc
 OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 

```

in /var/log/Xorg.0.log:
```
[     4.172] (II) LoadModule: "intel"
[     4.172] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.172] (II) Module intel: vendor="X.Org Foundation"
[     4.172]     compiled for 1.11.3, module version = 2.17.0
[     4.172]     Module class: X.Org Video Driver
[     4.172]     ABI class: X.Org Video Driver, version 11.0

```

lshw -c video:
```
adams@Neptune:~$ lshw -c video
  *-display               
       description: VGA compatible controller
       product: Ivy Bridge Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7000000-f73fffff memory:e0000000-efffffff ioport:f000(size=64)

```

modinfo i915:
```
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     49FEE27E6D7DC1975E781B1
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
...
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           modeset:Use kernel modesetting [KMS] (0=DRM_I915_KMS from .config, 1=on, -1=force vga console preference [default]) (int)
parm:           fbpercrtc:int
parm:           panel_ignore_lid:Override lid status (0=autodetect [default], 1=lid open, -1=lid closed) (int)
parm:           powersave:Enable powersavings, fbc, downclocking, etc. (default: true) (int)
parm:           semaphores:Use semaphores for inter-ring sync (default: -1 (use per-chip defaults)) (int)
parm:           i915_enable_rc6:Enable power-saving render C-state 6 (default: -1 (use per-chip default) (int)
parm:           i915_enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_downclock:Use panel (LVDS/eDP) downclocking for power savings (default: false) (int)
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override selection of SDVO panel mode in the VBT (default: auto) (int)
parm:           reset:Attempt GPU resets (default: true) (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)


```

---

### Post by MikeT23 on 2012-10-29
Update:

I updated Mythtv to 0.26. It was a bit problematic but Mythtv worked after update. 

Then I followed :
[http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI)
to get the VAAPI drivers installed - I believe this is the key. However, if I select VAAPI in the Mythtv it crashes with "mythtv failed to reinitialize video output" and the following in the frontend log file:
```
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:154 (Create) VAAPI: Version: 0.32
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:155 (Create) VAAPI: Driver : Intel i965 driver - 1.0.15
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: MPEG2Simple Entrypoints: VLD 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: MPEG2Main Entrypoints: VLD 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: H264Base Entrypoints: VLD EncSlice (UNSUPPORTED) 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: H264Main Entrypoints: VLD EncSlice (UNSUPPORTED) 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: H264High Entrypoints: VLD EncSlice (UNSUPPORTED) 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: VC1Simple Entrypoints: VLD 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: VC1Main Entrypoints: VLD 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext vaapicontext.cpp:518 (InitProfiles) VAAPI: Profile: VC1Advanced Entrypoints: VLD 
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext videooutbase.cpp:1862 (CalcHueBase) VideoOutput: CalcHueBase(Intel i965 driver - 1.0.15): Unknown adaptor, hue may be wrong.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext videooutbase.cpp:1864 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext mythpainter_ogl.cpp:27 (MythOpenGLPainter) OpenGL painter using existing OpenGL context.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext mythpainter_ogl.cpp:29 (MythOpenGLPainter) OpenGL painter using existing QGLWidget.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: I CoreContext openglvideo.cpp:223 (Init) GLVid: Using raw RGBA input textures.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: E CoreContext vaapicontext.cpp:307 (CreateDisplay) VAAPI: Invalid display
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: E CoreContext videoout_openglvaapi.cpp:145 (CreateVAAPIContext) VidOutGLVAAPI: Failed to create VAAPI context.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: E CoreContext videoout_openglvaapi.cpp:98 (InputChanged) VidOutGLVAAPI: Failed to re-initialise video output.
Oct 29 23:00:51 Neptune mythlogserver: mythfrontend[2549]: E CoreContext mythplayer.cpp:596 (ReinitVideo) Player(0): Failed to Reinitialize Video. Exiting..
```

DVDs and TV in Kaffeine still have screen tearing.

---

### Post by visualus on 2012-11-07
Hi there,


I have a new Thinkpad t430s with the same intel ivy bridge and intel hd  graphic card, running KDE 4.9 with 3.6 kernel.

I had a tearing issue when playing hd movie with high motion (mainly).
hAnyway I found a solution which I hope will solve also your problem:

Generally speaking it's a problem of VSynchronization. Go to System Settings -> Desktop effects -> Advanced -> Vsync (Check!)

I have no idea why it's not enabled by default. Let me know if It helped also in your case.

---

### Post by screaminj3sus on 2012-11-07
No tearing at all here with intel HD4000, using ubuntu 12.10/unity. What version of ubuntu are you using, and importantly what desktop/compositor?

afiak with intel hd3000/4000 you need a compositor that supports page-flipping to have a totally tear free experience.

Intel developers are working on getting a tear-free experience without a compositor running, but they aren't quite there yet.[http://phoronix.com/forums/printthread.php?t=74598&pp=40](http://phoronix.com/forums/printthread.php?t=74598&pp=40)

---

### Post by visualus on 2012-11-08
> **screaminj3sus said:**
> No tearing at all here with intel HD4000, using ubuntu 12.10/unity. What version of ubuntu are you using, and importantly what desktop/compositor?



MikeT23 wrote he's using Kubuntu so probably his desktop environment is KDE, that's why I wrote KDE solution.
AFAIK in Gnome Vsync is enabled by default

---

### Post by MikeT23 on 2012-11-11
Thanks, MythTV is now working with VAAPI and no screen tearing. I made the suggested changes to System Settings -> Desktop effects -> Advanced -> Vsync (I had to first select OpenGL). That didn't change anything but then I found that there is another setting in MythTV: Setup -> Appearance -> Paint Engine -> OpenGL.

---

### Post by MikeT23 on 2012-11-18
Although I get no screen tearing in regular definition I do still get tearing and sudden jumps in HD. I can't find any settings to avoid this.

---

### Post by gogan on 2013-01-27
Hi folks!

I have Vsync checked in KDE and tears are still present, so your tricks doesn't work for me. Any ideas are welcome

Cheers

```


i7-3610qm

3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

kwin 4.4.9.2-0ubuntu2.1

description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by smurphy on 2013-02-12
I do actually go into "Suspend to Ram" mode once, wake it back up - and all tearing is gone. Weird stuff.

---

### Post by borjaxvalencia on 2013-04-11
My solution has been, after a long time searching, uncheck the checkbox "Suspend desktop effects for fullscreen windows" in KDE Systen Settings -> Desktop Effects -> Advanced. My configuration there is OpenGL and QT--Native, even it's fine with any configuration...All the videos in full screen.
I'm using vanilla kernel 3.8.6 on Kubuntu 12.10 (with 3.6, using opengl composition was not smooth, but now it is)
Finnally everything is working great on my asus ux31a.

---

