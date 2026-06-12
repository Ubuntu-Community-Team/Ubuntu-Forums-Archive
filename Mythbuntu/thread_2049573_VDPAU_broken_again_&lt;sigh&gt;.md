---
title: "VDPAU broken again &lt;sigh&gt;"
date: 2012-08-28
forum: Mythbuntu
---

### Post by seanos on 2012-08-28
After today's update VDPAU no longer works (Failed to intialize video output).  "High Quality" playback works, but I know I'm better off using VDPAU.

```
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythrender_vdpau.cpp:389 (Create) VDPAU: No VDPAU device
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythrender_vdpau.cpp:405 (Create) VDPAU: Failed to create VDPAU render device.
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext videoout_vdpau.cpp:147 (InitRender) VidOutVDPAU: Failed to initialise VDPAU
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext videooutbase.cpp:301 (Create) VideoOutput: Not compiled with any useable video output method.
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythplayer.cpp:482 (InitVideo) Player(3): Couldn't create VideoOutput instance. Exiting..
Aug 29 10:50:09 urania mythfrontend[6296]: E CoreContext mythplayer.cpp:2675 (StartPlaying) Player(3): Unable to initialize video.
```

NVIDIA drivers have been updated since the last Myth update so maybe that's part of the problem?  I'm not sure where to begin with this.

VDPAU appears to be usable by VLC and MPlayer.

Ubuntu Natty 11.04
Myth 0.25.2-16-gd519276
NVIDIA 304.37
GeForce GT 430

---

### Post by BicyclerBoy on 2012-08-31
VLC does not support VDPAU directly..it can use va-api.
There is a vdpau backend for vaapi package.
mplayer does not use vdpau unless you invoke with
-vo vdpau (sets renderer)
-vc ffmpegvdpau (set vdpau codec h/w)

Try
glxinfo | grep OpenGL
grep -i vdpau /var/log/Xorg.0.log
vdpauinfo

---

