---
title: "Unable to get Nvidia driver working after upgrading from Kubuntu 7.04 to 7.10"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by gtmaneki on 2008-02-09
My computer has an older Nvidia GEForce MX200 I purchased in 2001.  I had the binary driver installed and working under Kubuntu 7.04 using tseliot's "Envy" program.  However, once I upgraded to Kubuntu 7.10 I have been unable to get the binary driver working again (possibly because I forgot that I needed to have Envy remove the old driver before I upgraded).

When I use System Settings -> Advanced -> Restricted Drivers -> NVIDIA Accelerated Graphics Driver to set things up, I get the response

```
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-legacy'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb (--unpack):  
subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I also get the same error when I run 
```
sudo apt-get install nvidia-glx
```

When I run
```
sudo apt-get install nvidia-glx-legacy
```
(because I'm not sure if the video card is so old it needs to use the legacy drivers), I get the result
```

Unpacking nvidia-glx-legacy (from .../nvidia-glx-legacy_1.0.7185+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-legacy' clashes with `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-legacy_1.0.7185+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-legacy_1.0.7185+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions as to getting the binary driver working?

Thanks!

---

