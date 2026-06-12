---
title: "nVidia G70 (Geforce 7600GS) rev a1"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Robbyx on 2009-03-13
I am using Ub 8.10 on a Gigabyte S-series MB with the nVidia driver 177.82 to drive two screens from one video card. Sometimes when I drag a window from one screen to another the window repeats on screen as if it was a pack of cards being rifled. Usually that clears but I have to wait. Sometimes the screen freezes. To avoid these problems do I have to buy a new video card?

---

### Post by inobe on 2009-03-13
the newer driver is known to have fixed many issues

>     *  Added support for the following GPUs:
          o GeForce 9300 GE
          o Quadro NVS 420
    * Added support for OpenGL 3.0 for GeForce 8 series and newer GPUs.
    * Fixed a bug that caused VDPAU to display a green screen when using the overlay-based presentation queue with interlaced modes.
    * Fixed a bug that prevented VDPAU from working correctly after X server restarts on some GPUs.
    * Improved VDPAU's handling of mode switches; eliminated a crash in its mode switch recovery code and a hang in the blit-based presentation queue.
    * Fixed a bug that caused VDPAU to crash when using DisplayPort devices.
    * Fixed a potential hang in VDPAU when using the blit-based presentation queue on systems with multiple GPUs not in SLI mode.
    * Implemented missing error checking of layer data in VDPAU's VdpVideoMixerRender function.
    * Improved VDPAU's handling of setups with multiple GPUs, if a subset of the GPUs cannot be supported due to resource limitations.
    * Improved GPU video memory management coordination between the NVIDIA X driver and VDPAU.
    * Fix potential hang in VDPAU when the overlay is already in use.
    * Improved workstation OpenGL performance.
    * Fixed an X driver acceleration bug that resulted in Xid errors on GeForce 6 and 7 series GPUs.
    * Updated the X driver to consider GPUs it does not recognize supported, allowing it to drive some GPUs it previously ignored.
    * Added the ability to run distribution provided pre- and post-installation hooks to 'nvidia-installer'; please see the 'nvidia-installer' manual page for details.
    * Updated the X driver's metamode parser to allow mode names with periods (i.e. '.'s).
    * Fixed a problem in VDPAU that prevented the overlay-based presentation queue from being used on displays connected by component video.
    * Fixed various problems in VDPAU that caused visual corruption when decoding certain MPEG-2 video streams.
    * Fixed a crash in VDPAU caused by certain invalid MPEG-2 streams, in 64-bit drivers for some GPUs.
    * Fixed an X driver performance problem on integrated GPUs.
    * Fixed a stability problem with OpenGL applications using FSAA.
    * Fixed an initialization problem that caused some AGP GPUs to be used in PCI compatibility mode.
    * Fixed a bug that could result in stability problems after changing clock settings via the Coolbits interface.
    * Fixed a problem with hotkey switching on some recent mobile GPUs.
    * Worked around a power management regression in and improved compatibility with recent Linux 2.6 kernels.


[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)


you may want to try that driver before buying another video card

---

### Post by inobe on 2009-03-13
to add if one is curious to how it's installed


scroll down to "Installation of ATI and nVidia Graphics drivers"

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers)


keep this handy [http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

---

### Post by norwoods on 2009-03-13
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then nclick Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by Robbyx on 2009-03-14
> **norwoods said:**
> i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then nclick Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

I followed this advice and now have the latest driver installed. The installation did not work well at first as it did not seem to do anything but eventually I managed to install the repository.


Thanks for everyone's help. I will now see if my problems go away.


Robin

---

### Post by Robbyx on 2009-03-16
My problems have not really gone away, so although there is some improvement I still have problems with the speed of some screen updates. Could I have some suggestions for a card replacement: I view some videos on line and so would like anti aliasing.  I would also like to take some of the load off the cpu (dual core intel).

---

### Post by norwoods on 2009-03-16
i am happy with my nVidia 9600gt.  there have not been a lot of new products announced lately so i expect new products when nVidia gets their 45nm production working right.

---

### Post by Robbyx on 2009-03-17
Instead of buying a new video card would it be better to buy a faster cpu? My current one is an intel 2 core LGA 775.

---

### Post by skymera on 2009-03-17
Intel Core2Duo are relatively fast CPU's.

Your 7600 might be straining over two monitors with effects on.

@> **norwoods said:**
> i am happy with my nVidia 9600gt.  there have not been a lot of new products announced lately so i expect new products when nVidia gets their 45nm production working right.

Norwoods - There have been virtually no new products from Nvidia since the 8 series.

---

### Post by Robbyx on 2009-03-17
> **skymera said:**
> Intel Core2Duo are relatively fast CPU's.

Your 7600 might be straining over two monitors with effects on.

@

Norwoods - There have been virtually no new products from Nvidia since the 8 series.

Is this the same card that you suggest above:

XFX GeForce 9600 GSO 768MB ,580MHZ

I have seen it for about £65 new.

Robin

---

### Post by norwoods on 2009-03-17
> **Robbyx said:**
> Is this the same card that you suggest above:

XFX GeForce 9600 GSO 768MB ,580MHZ

I have seen it for about £65 new.

Robin

not exactly, but close enough.  nvidia rates the graphics performance of a 9600 GSO 512 at 16x and the graphics performance of a 9600 GT at 17x.

---

### Post by Robbyx on 2009-03-17
Thanks for your help. I will go off and buy one.

Robin

---

