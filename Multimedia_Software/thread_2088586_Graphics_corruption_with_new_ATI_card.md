---
title: "Graphics corruption with new ATI card"
date: 2012-11-27
forum: Multimedia Software
---

### Post by worldviking on 2012-11-27
I recently switched from an nvidia to ATI graphics card and have lately been seeing sporadic graphics corruption. Everything will work fine for a while, sometimes 6-8 hours, then I'll randomly start getting stuff like this: 

[http://i.imgur.com/pacn2h.jpg](http://i.imgur.com/pacn2h.jpg) (you're looking at the top menu bar)

Eventually (5-10 minutes) the computer either freezes or moves to something like this: 

[http://imgur.com/a/TZvHs](http://imgur.com/a/TZvHs) (whole screen)

both of which require a hard restart to resolve. 

I've tried both the stock ATI drivers (12.10 and 12.11 beta) and fglrx as listed in the additional drivers menu, and all seem to have this problem. My video card is a Sapphire HD 7870. 

Thinking it might have been caused by old nvidia drivers, I formatted and reinstalled 12.10, then 12.04. I've only been using Unity 3D so far, but I'd love a solution other than "use Unity2d" =/

Any advice?

```

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7800 Series
OpenGL version string: 4.2.11627 Compatibility Profile Context
``````
> sudo lshw -C display; lsb_release -a; uname -a
  *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:42 memory:c0000000-cfffffff memory:efe80000-efebffff ioport:ee00(size=256) memory:efe00000-efe1ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
Linux hostname 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by pakguru on 2012-11-27
Hi,
Since your card seems to work OK for up to 8 hours it seems to suggest that the problem is not with the drivers but may be due to a stability problem with your hardware (...possibly overheating somewhere??).
I would be tempted to check out your cooling fans and case ventilation.
Also, check your PSU supply, which is advisable to be at least 500 Watts.
As a really long shot, check your RAM, I once had a dodgy RAM stick that caused all kinds of stability issues with a graphics card.

Good Luck

Pakguru

---

### Post by worldviking on 2012-11-28
Good suggestions. The PSU is 650W so it should be ok, and ventilation seems fine. I haven't had a chance to check the memory. 

I  guess the reason I think it's more likely to be a driver issue is  because of the scene corruption. I guess I didn't highlight it in my  original post, but it's always just a fraction of the scene that has  artifacts. Until the entire scene is covered with them the OS is still  usable. It's only things like buttons or UI elements with mouseovers  (Nautilius is particularly bad) or the menu bar that seem to have  trouble. The card also seems to do well in Windows, and there I  typically use it for more graphics-intensive things, like games.

---

