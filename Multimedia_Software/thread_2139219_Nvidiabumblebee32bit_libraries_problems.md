---
title: "Nvidia/bumblebee/32bit libraries problems"
date: 2013-04-26
forum: Multimedia Software
---

### Post by Mike Loubet on 2013-04-26
Hello,

I just bought a laptop with a Nvidia 640m optimus graphics card (without knowing that optimus is not supported on Linux). After some time I realised that bumblebee was needed to use the Nvidia chip and set it up. Running ```
optirun glxgears
``` suggests that it works, however I have had some difficulties:

When trying to run playonlinux or steam, it says that 32bit opengl libraries are missing. When I try and run a game on playonlinux, it crashes instantly. However, upon checking, it appears that the 32 bit libraries are installed, which leads me to believe that there are some files pointing in the wrong direction or that I didn't install bumblebee correctly (despite following guides).

Before installing, I added the x-updates ppa and after checking muon, it appears I have Nvidia-304-updates and Nvidia-settings-313-updates installed (are they both supposed to be 304 or 313? I don't know which is the correct driver to install or how to do that without breaking bumblebee).

Other than that I have no clues to go on. I have searched the forums and elsewhere but it doesn't seem that they are the same problems and I don't want to start testing possible solutions without knowing what the problem is so I don't break something. I want to use Prime as well since I've read it gives better framerates, but want to get the libraries working first before trying it out.

Any help/suggestions would be appreciated! :)

Running Kubuntu 13.04 64-bit.

**EDIT:**

Running```
optirun nvidia settings
``` gives me an error message:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server..

Does this mean that the proprietary drivers are not properly installed and it is falling back to the nouveau drivers?

---

### Post by Mike Loubet on 2013-04-27
Update:

I have solved the 32bit libraries problem, simply opening playonlinux or steam with the "optirun" command. Opening a game within playonlinux with the optirun command does not work unless playonlinux itself is opened with optirun... Steam doesn't run at all without the command. Fairly simple, should have figured that out.

However, primus does not work, or at least doesn't give any increased framerate as it should. Here is a comparison between primusrun, optirun and the integrated graphics:

```
mike@nFinity:~$ primusrun glxspheresPolygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 640M/PCIe/SSE2
62.099028 frames/sec - 54.363973 Mpixels/sec
60.309315 frames/sec - 52.797186 Mpixels/sec
60.304349 frames/sec - 52.792839 Mpixels/sec
60.306663 frames/sec - 52.794865 Mpixels/sec
60.309644 frames/sec - 52.797475 Mpixels/sec
60.327739 frames/sec - 52.813316 Mpixels/sec
60.287672 frames/sec - 52.778239 Mpixels/sec
mike@nFinity:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 640M/PCIe/SSE2
130.356398 frames/sec - 114.119205 Mpixels/sec
134.688944 frames/sec - 117.912089 Mpixels/sec
133.598009 frames/sec - 116.957041 Mpixels/sec
mike@nFinity:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
61.095588 frames/sec - 53.485521 Mpixels/sec
60.880838 frames/sec - 53.297521 Mpixels/sec
61.148437 frames/sec - 53.531787 Mpixels/sec
60.900633 frames/sec - 53.314851 Mpixels/sec
61.268179 frames/sec - 53.636615 Mpixels/sec



``` 

primusrun gives the same framerates as the integrated graphics... Which suggests it either isn't functioning correctly or is using the open source drivers (?).

Doing glxgears with primusrun throws up some errors:

```
mike@nFinity:~$ primusrun glxgears308 frames in 5.0 seconds = 61.464 FPS
primus: warning: dropping a frame to avoid deadlock
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 546 requests (546 known processed) with 0 events remaining.
primus: warning: dropping a frame to avoid deadlock
primus: warning: timeout waiting for display worker
```

Does anyone know what that means and how to fix it?

---

