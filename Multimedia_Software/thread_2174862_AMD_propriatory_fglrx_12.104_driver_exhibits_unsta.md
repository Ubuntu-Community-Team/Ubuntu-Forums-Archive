---
title: "AMD propriatory fglrx 12.104 driver exhibits unstable acceleration?"
date: 2013-09-16
forum: Multimedia Software
---

### Post by Handssolow on 2013-09-16
There seems to a strange behavior when I test the Radeon HD7950 (3GB) using fgl_glxgears. The cube rotates rapidly for about 30 seconds then slows. I'm using Ubuntu 12.04 LTS 64 bit with Phenom x6 1090T. Testing with fgl_glxgears from a fresh reboot yield the following result-

$ fgl_glxgears
Using GLX_SGIX_pbuffer
9016 frames in 5.0 seconds = 1803.200 FPS
8854 frames in 5.0 seconds = 1770.800 FPS
9042 frames in 5.0 seconds = 1808.400 FPS
9013 frames in 5.0 seconds = 1802.600 FPS
4421 frames in 5.0 seconds = 884.200 FPS
2660 frames in 5.0 seconds = 532.000 FPS
2692 frames in 5.0 seconds = 538.400 FPS
2792 frames in 5.0 seconds = 558.400 FPS
2701 frames in 5.0 seconds = 540.200 FPS
2703 frames in 5.0 seconds = 540.600 FPS
2636 frames in 5.0 seconds = 527.200 FPS

Login/logout doesn't renew the 30 seconds of fast cube rotation, only a reboot. Gnome Fallback with or without effects seems it make little different but results are variable. 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104

sudo vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

$ sudo lspci -v
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Device 2316
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fde80000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <




What is the explanation of rapid cube rotation not being sustained for more than about 30 seconds? Is the driver, driver configuration not optimal? Is it an issue with the fgl_glxgears test? Do I need the latest Beta driver? Is it a hardware fault? Is it a 12.04 kernel issue? I've not noticed any error messages in the /var/log files. Where else might I look or enable? I suspect the performance of my HD7950 graphics card is well below what should be available.

---

### Post by Yellow Pasque on 2013-09-17
I would definitely try the lastest beta for a card that new. Instructions are here [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL) 
Just change --buildpkg Ubuntu/raring to --buildpkg Ubuntu/precise

---

### Post by Handssolow on 2013-10-10
Eventually I achieved success by using synaptic to install the experimental driver as reported here-
[http://ubuntuforums.org/showthread.php?t=2178677](http://ubuntuforums.org/showthread.php?t=2178677)

Running jockey-gtk or its Additional Driver GUI are both broken, and I appear to be one of several others with this same problem. It doesn't look like there's an explanation or fix for this in 12.04TLS.

On a brighter note, there is now no slowing of cube rotation after about 30 seconds with fgl_glxgears that I had reported earlier though boot up takes about 1.5 minutes for reasons which are still unclear. What I have learnt for the future is not to press reset too soon, thinking the driver hasn't properly installed.

---

