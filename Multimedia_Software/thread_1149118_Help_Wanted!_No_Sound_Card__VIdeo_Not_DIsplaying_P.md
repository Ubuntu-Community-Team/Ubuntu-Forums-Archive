---
title: "Help Wanted! No Sound Card / VIdeo Not DIsplaying Properly."
date: 2009-05-04
forum: Multimedia Software
---

### Post by Reyes1986 on 2009-05-04
I have just switched from Windows to Ubuntu and I cannot play any sound whatsoever. 

My soundcard: Sound Blaster X-FI.

Comments: I have been looking all over the place and still cannot figure out how to enable this! IT shows that it's detected, however I get this
> make -C /lib/modules/2.6.24-24-generic/build M=/home/home/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/home/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
IS there anyway I can just open up a program and let it do its job? It's so hard using commands that I am not familiar with (again, this is my first time with Ubuntu). I have searched EVERYWHERE and still cannot configure my soundcard. Is there a noob guide out there?!

2nd Problem:

My videocard = nVidia XFX Geforce GT 7950 512 MB

Comments = My monitor can reach up to 65Hz but the maximum is 51Hz on my display, also it seems that the colors are not True 32Bit

Can somebody please help me, I'm tired of Windows, I want to start using LInux!:guitar:

EDIT: If this helps, it says this too:

> 
05:04.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs X-Fi XtremeMusic
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at bce0 [size=32]
    Memory at fb600000 (64-bit, non-prefetchable) [size=2M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>


---

### Post by Reyes1986 on 2009-05-05
bump anybody?

---

