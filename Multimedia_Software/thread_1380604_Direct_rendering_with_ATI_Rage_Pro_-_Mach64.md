---
title: "Direct rendering with ATI Rage Pro - Mach64"
date: 2010-01-13
forum: Multimedia Software
---

### Post by cga2000 on 2010-01-13
A few years ago with XFree86 4.* it was possible to enable direct rendering with
an ATI mach64.                                                                         
 
I noticed that on a vanilla Ubuntu 9.10, glxinfo displays the following:                                                                                                                    
"Direct Rendering: Yes"                                                                        
 
Unfortunately, since I was running at my laptop's 1400x1050 native resolution with a depth of 24 at the time, and the card only has 8M of memory, I knew right away that this was not possible. 
                                                                    
I switched to 1024x768@16, which I know is within the card's limitations, and      
took a look the Xorg log and saw that DRI was still not enabled, due apparently to the absence                                                                                                                     on my system of kernel module 
mach64'.                                                                                                                    

[drm] failed to load kernel module "mach64"                                                                                                                   (EE) [drm] drmOpen failed.                                                                                                                         (EE) MACH64(0): [dri] DRIScreenInit Failed

I looked around and found a couple of well-documented posts that informed me that the source of the mach64 module was no longer part of the drm/ tree but 
that it had been moved to the kernel source.                                                                                                                         
I downloaded my kernel's source from the Ubuntu repos, hoping this was just going to be a matter of compiling the module and running a modprobe, but I found not traceof a mach64.c in the linux../drivers/gpu/drm/ directory.                                                                                                                    

The last time I was able to enable DRI with this card, I was running debian sarge with a 2.4 kernel, and must have failed to get this to work three or four 
times since.   

There supposedly is a security issue with the implementation of DRI for this card, although I have never seen any information as to what kind of risk is                      involved, and whether it might affect me.                                                          

I did find a site s/o had volunteered and made available a few binary versions of this module, but apart from the fact that I would not insmod code of unknown 
origin into my system's kernel, his .deb's are for older versions of the linux                                                                                                                           kernel.

Does anyone know the story behind this and why something as simple as this  should have posed problems for so long? 

Is there a chance this direct rendering on a Mach64 will become possible again in the foreseeable future?                                                                                                                       

Thanks,                                                                                                                      
CJ

---

