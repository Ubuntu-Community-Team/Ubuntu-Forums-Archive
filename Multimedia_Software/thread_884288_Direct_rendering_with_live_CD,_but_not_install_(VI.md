---
title: "Direct rendering with live CD, but not install (VIA)"
date: 2008-08-08
forum: Multimedia Software
---

### Post by frank754 on 2008-08-08
I have a Sylvania G Netbook and I'm using the latest 7/23/08 iso of a special Sylvania GOS, which is a version of Ubuntu 8.04 with a 2.6.24.3 kernel. I runs the Gnome desktop but the appearance is custom tweaked.

When I boot up with the live CD, glxinfo says yes to direct rendering, but once installed to the hard drive it says no. The video card is a VIA CX700.
The udev version is the latest, 117-8
The xorg.conf file is identical in both cases.
The only difference I see is in the output seen in the Xorg.0.log
Here is the snippet when using the live CD and when direct rendering works:
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "via" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.

Once installed, up to this point the log is virtually identical, but
it does not proceed to perform drmOpenByBusid (see above):

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via"
(EE) [drm] drmOpen failed.
(EE) VIA(0): [dri] DRIScreenInit failed. Disabling DRI.

What would cause it to act 2 different ways depending on whether it's installed or not? I suspect something is not making the device nodes correctly, or is not starting correctly, or has a mis-linked library or permission problem, only once installed.

Also the Synaptics touchpad driver gets killed at the end too, in the good version (running from the live CD) it has these lines:

(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found

but once installed it does not have the second line "auto-dev sets....."
and then I get /dev/input/event* device nodes missing, and unloads the driver.

I've tried to figure out this dual problem that seems somehow related, but it's been 2 days to no avail.
Thanks in advance for any insights on this.

---

