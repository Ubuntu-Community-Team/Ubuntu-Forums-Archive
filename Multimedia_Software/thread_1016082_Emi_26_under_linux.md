---
title: "Emi 26 under linux"
date: 2008-12-19
forum: Multimedia Software
---

### Post by phonky on 2008-12-19
I have a Emagic emi 26 usb audio interface, which I own for some time now already.

I wanted to use it with my laptop as my sound center, connected to some active loudspeakers.

However, the driver doesn't get loaded. It seems under /lib/firmware/2.6.27-9-generic/ there is a folder emi26 with the appropriate firmware, and under /lib/modules/2.6.27-9-generic/kernel/drivers/usb/misc/emi26.ko it seems a module is ready.

When I enter "lsusb" after the interface is plugged in into a usb connector, the terminal hangs, no Ctrl-C helps! Even kill -9 pid as root does not kill the process! The same happens to "modprobe snd_usb_audio".

I tried on another laptop with arch linux running - no difference. 

Does anybody have an idea where to start...???

Thanks a lot

---

