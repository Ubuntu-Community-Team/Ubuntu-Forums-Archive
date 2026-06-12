---
title: "Recompile of loadable vidio driver"
date: 2010-06-27
forum: Multimedia Software
---

### Post by SailingCyclops on 2010-06-27
Hi:

I have just installed UBUNTU 10.0.4 (32 bit Generic) on a Compaq CQ50 -AMD Athlon 64 X2 1.9GHZ . The install went flalessly, and everything simply worked out of the box. I also Installed the NVIDIA Propriatery graphics driver, and it worked OK. The box has an                                 NVIDIA GeForce 8200M G.    [LEFT][/LEFT]
   
  

When I did a "free" I discovered that UBUBTU was not using all available RAM. After a bit of research I found that to fix this, I needed to change the kernel to a PAE enabled one. So I installed                                 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23. On   reboot the system complained bitterly that it could not start X. With log entry:

                                       (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
    [LEFT](II) Module nvidia: vendor="NVIDIA Corporation"[/LEFT]
    [LEFT]	compiled for 4.0.2, module version = 1.0.0[/LEFT]
    [LEFT]	Module class: X.Org Video Driver[/LEFT]
    [LEFT](EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your[/LEFT]
    [LEFT](EE) NVIDIA:     system's kernel log for additional error messages.[/LEFT]
    [LEFT](II) UnloadModule: "nvidia"[/LEFT]
    [LEFT](II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so[/LEFT]
    [LEFT](EE) Failed to load module "nvidia" (module-specific error, 0)[/LEFT]
    [LEFT](EE) No drivers available.


So, I selected to boot with the "generic" driver and all was well. 


[/LEFT]
                                        I then issued-- nvidia-xconfig command and rebooted again. Same problem, this time I selected to go to shell and did a reboot, thinking that the driver needed to be recompiled for the new kernel, but I got the same result.


Somehow I believe I am loading an NVIDIA driver into a PAE kernel which is compiled for the non-PAE kernel.


I tried to de-Install/Re-Install the propriatery driver while running under the PAE kernel, but the driver still fails to load.


How can I fix this???


TIA




   
  [LEFT][/LEFT]
   
  
    [LEFT][/LEFT]

---

### Post by cchhrriiss121212 on 2010-06-28
Some gpu drivers are not compatible with non-generic kernels. Where did you get this one from?

---

