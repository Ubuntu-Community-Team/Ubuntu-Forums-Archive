---
title: "Ubuntu 14.04, intel graphic, vdpau, gecko-mediaplayer and apple trailers"
date: 2014-05-14
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2014-05-14
My laptop is Dell Latitude E5510, graphic card intel Ironlake

```
*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:8080(size=8)


```

I use the libvdpau-va-gl driver to get vdpau decoding for mplayer since gecko-mediaplayer uses mplayer backend and mplayer doesn't do vaapi. Other than occasional freezing this combo works quite well in general. 

However in Ubuntu 14.04 gecko-mediamplayer no longer works with Apple trailers if vdpau is enabled in gnome-mplayer. It would just show a blackbox where the video should be but the audio would play. Disable vdpau then it works. I have tried different versions of mplayer (mplayer from repo, mplayer2 from repo, mplayer svn self compiled) and different versions of libvdpau-va-gl (Trusty's repo's version 2.1.x and webupd8's vesrion 3.4.1). None work

But this combination (libvdpau-va-gl + gecko-mediaplayer + Apple trailers) works perfectly in 13.10,--same version of libvdpau-va-gl from webupd8. Not sure how to debug this and who to file bug against.

---

### Post by monkeybrain20122 on 2014-05-18
I have contacted the developer of libvdpau-va-gl. Turned out it is the culprit. It is now fixed in the beta. 

Edited: just compiled from git master and it works now.

---

