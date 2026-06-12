---
title: "Problem compiling ALSA Driver"
date: 2011-11-17
forum: Multimedia Software
---

### Post by Kivrin on 2011-11-17
Hello all.

My original sound problem was that the sound would go out randomly while I was using my computer, and would only come back after a full restart. 

I followed the instructions from the Comprehensive Sound Guide. When I started tinkering last night, aplay -l and lspic -v detected my sound card, but modprobe didn't bring the sound back, so I reinstalled the ALSA driver. That didn't work either, so I went through and started to compile the driver, which failed. Now aplay -l doesn't detect anything.

ALSA Compilation error:
```
In file included from include/linux/pci.h:58:0,                             
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
 &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:58: fatal error:     
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory   
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-12-generic'       
 &#9474; make[2]: *** [compile] Error 2                                              
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make[1]: *** [build-stamp] Error 2                                          
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make: *** [kdist_image] Error 2  
```

Current result for aplay -l:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****

```

Current result for lsvic -v:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Any help would be appreciated!

---

