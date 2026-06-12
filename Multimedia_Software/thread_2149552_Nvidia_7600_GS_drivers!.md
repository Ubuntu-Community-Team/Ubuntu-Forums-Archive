---
title: "Nvidia 7600 GS drivers!"
date: 2013-05-29
forum: Multimedia Software
---

### Post by TheHammer101 on 2013-05-29
I have an AGP 8x Nvidia 7600 GS installed in my system. I cannot seem to get Nvidia drivers to work correctly with it.
```
lshw -c video
  *-display
       description: VGA compatible controller
       product: G73 [GeForce 7600 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:16 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:fd000000-fd01ffff
```

I have output going to a Audio+DVI>HDMI converter, and then to a monitor. It works fine in 1920x1080 with nouveau drivers, but I want to use XBMC. The problem is that XBMC is slow as anything when I do get it to work. The other times it doesn't work it demands OpenGL support. So I install the nvidia drivers through the "Additional Drivers" or through an Nvidia provided .run file, and as soon as I reboot my monitor tells me "OUT OF RANGE". What can I do to force my resolution, or how can I make it display correctly???

---

### Post by TheHammer101 on 2013-06-01
Update:
So, here's the strangest thing I may have ever seen. When I have just the DVI connector hooked up to the DVI+Audio>HDMI converter it will only tell me it's "OUT OF RANGE" on the monitor. When I plug in a VGA monitor at the same time BOTH monitors work, no problem! So is there a way to fool Ubuntu, or the Nvidia 304 experimental drivers I'm using currently that there's a monitor plugged into the VGA port? What is going on here? How can I help someone help me figure this out, and find a workaround..

---

