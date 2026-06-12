---
title: "Sound Blaster Audigy 1 - no audio"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by 4dplane on 2007-11-22
Hi,

I have followed the instructions from the "Comprehensive Sound Problem Solutions Guide" and I have not been able to get things to work. 

I was able to get through many of the steps but in "ALSA driver Compilation" I did the "Using alsa-source" step and it failed. Here is the end of the error message:

                      â arguments to function âpci_save_stateâ                                     â
                      â /usr/src/modules/alsa-driver/include/adriver.h: In function                â
                      â âsnd_pci_orig_restore_stateâ:                                              â
                      â /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       â
                      â arguments to function âpci_restore_stateâ                                  â
                      â make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1          â
                      â make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  â
                      â make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                â
                      â make[3]: *** [modules] Error 2                                             â
                      â make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'      â
                      â make[2]: *** [compile] Error 2                                             â
                      â make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  â
                      â make[1]: *** [build-stamp] Error 2                                         â
                      â make[1]: Leaving directory `/usr/src/modules/alsa-driver'
                      â make: *** [kdist_image] Error 2  

The sound card is a old 16bit sound blaster audigy, linux 2.6.20-15

Thanks,
4dplane

---

### Post by 4dplane on 2007-11-22
Here are the errors from the dpkg install.

---

