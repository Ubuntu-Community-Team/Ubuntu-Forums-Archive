---
title: "Flash extremely slow after upgrade to 14.04"
date: 2014-04-19
forum: Multimedia Software
---

### Post by piovisqui2 on 2014-04-19
Hi folks. 

I upgraded from 12.04 to 14.04. Installed pepper flash for chromium and the adboe flash for Firefox. Both are slow, videos play at 10fps, no matter the resolution. I  tried replacing "mozilla-flashplugin-square-nonfree" with "adobe-flash-properties-kde", no result. I upgrade fglrx to the latest Beta from AMD, no result.

The X server is always as the top process  on CPU  usage, according to htop. I tried replacing LightDM with KDM, no result.

I play Steam Dota 2 and have decent 60fps. FULL HD videos play well.


By the way, I use Kubuntu.

Tech info:
```

lspci -vv | grep VGA
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] (prog-if 00 [VGA controller])

 dpkg -l | grep fglrx
ii  fglrx                                                       2:13.350-0ubuntu1                              amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                              2:13.350-0ubuntu1                              amd64        Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-dev                                                   2:13.350-0ubuntu1                              amd64        Video driver for the AMD graphics accelerators (devel files)
ii  xvba-va-driver                                              0.7.8-1ubuntu3                                 amd64        XvBA-based backend for VA API (AMD fglrx implementation)

dpkg -l | grep pepper
ii  pepperflashplugin-nonfree                                   1.3ubuntu1                                     amd64        Pepper Flash Player - browser plugin


dpkg -l | grep flashplug
ii  adobe-flashplugin                                           11.2.202.350-0trusty1                          amd64        Adobe Flash Player plugin version 11
ii  pepperflashplugin-nonfree                                   1.3ubuntu1                                     amd64        Pepper Flash Player - browser plugin


glxgears 
28963 frames in 5.0 seconds = 5792.485 FPS



```

Any ideas on how to solve or debug this?

---

