---
title: "VDPAU fails in mythbuntu 10.04 ? bug"
date: 2010-03-30
forum: Mythbuntu
---

### Post by odror on 2010-03-30
OS: 2.6.32-18-generic #27-Ubuntu SMP Fri Mar 26 19:51:10 UTC 2010 i686
Nvidia driver (supplied by ubuntu 10.04): 195.36.15
Nvidia card : 9600 GT

Whenever I play a recording (from hdvpr, H,264 format) It fails toplay it.

Mythfrontend print the following error:

[HTML][/HTML]

> 2010-03-30 09:38:06.019 VDPAU Error: Error at mythrender_vdpau.cpp:1447 (#1, Unknown)
2010-03-30 09:38:06.019 VDPAU Error: Failed to create VDPAU device.
2010-03-30 09:38:06.019 VDPAU Error: No VDPAU device
2010-03-30 09:38:06.019 Failed to create VDPAU render device.
2010-03-30 09:38:06.019 VidOutVDPAU Error: Failed to initialise VDPAU
2010-03-30 09:38:06.020 VideoOutput, Error: Not compiled with any useable video output method.
2010-03-30 09:38:06.020 NVP(0), Error: Couldn't create VideoOutput instance. Exiting.


Is this an ubuntu bug? is there a work around or a fix?

thanks

---

### Post by nickrout on 2010-04-01
Are you sure nvidia driver is running?

---

### Post by padukes on 2010-06-09
I have the same error - did you ever find a solution to this?

-P

---

### Post by nickrout on 2010-06-09
Are you sure nvidia driver is running?

---

### Post by padukes on 2010-06-09
Hi nickrout,  yes I believe it's running.  I can run "nvidia-settings" and it shows the driver and the version.

-P

---

### Post by nickrout on 2010-06-09
And how much video ram? You SHOULD have 512M, although 256M may work in some situations.

Have you been through the instructions here:

[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

Also the mailing list archive has a lot of likely threads:

[http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=forum_1&search_string=vdpau+NVP%280%29%2C+Error%3A+Couldn%27t+create+VideoOutput+instance.+Exiting&search_type=AND](http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=forum_1&search_string=vdpau+NVP%280%29%2C+Error%3A+Couldn%27t+create+VideoOutput+instance.+Exiting&search_type=AND)

---

### Post by padukes on 2010-06-09
Thanks Nicrout.  I have 512MB of video ram and everything worked perfectly in karmic. It wasn't until I upgraded to Lucid today that it stopped working.  I'll check out the myth mailing list, but do you have any other ideas?

Thanks!
P

---

### Post by nickrout on 2010-06-09
Yes, try the autobuilds, lucid does not ship with 0.23, only 0.23RC

---

### Post by odror on 2010-06-10
In my case the problem was solved when I changed video card. Either the support for VDPAU in the 8600 is not good or I had a defective card.

-Oz

---

### Post by padukes on 2010-06-10
Hey,

My problem was that /usr/lib/libvdpau_nvidia.so was pointing to the wrong lib.  I had to point it to /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.

I figured it out by running the following in the shell:

```
export VDPAU_NVIDIA_DEBUG=3
export VDPAU_TRACE=1

vdpauinfo

```

This printed out some extra error messages about /usr/lib/libvdpau_nvidia.so which caused me to check out the link.

Thanks!
P

---

