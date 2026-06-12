---
title: "nforce2 no sound/ALSA drivers fail to compile"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Tango_Down on 2007-11-22
I have no sound on my nforce2 IEC985 with fiesty. I tried to follow the "Comprehensive sound guide" sticky  but the alsa source will not compile 
 make[3]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'     &#9618;      
      &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                    &#9618;      
      &#9474; In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     &#9618;      
      &#9474; /usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error:               &#9618;      
      &#9474; linux/config.h: No such file or directory     In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,         
      &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     &#9618;      
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition    &#9618;      
      &#9474; of 'jiffies_to_msecs'                                                      &#9618;      
      &#9474; include/linux/jiffies.h:268: error: previous definition of                 &#9618;      
      &#9474; 'jiffies_to_msecs' was here                                                &#9618;      
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition    &#9618;      
      &#9474; of 'msecs_to_jiffies'                                                      &#9618;      
      &#9474; include/linux/jiffies.h:290: error: previous definition of                 &#9618;      
      &#9474; 'msecs_to_jiffies' was here                                                &#9618;      
      &#9474; In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,  &#9618;      
      &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     &#9618;      
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                       
      &#9474; 'snd_pci_orig_save_state':                                                 &#9618;      
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many  arguments to function 'pci_save_state'                                            
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#9618;      
      &#9474; 'snd_pci_orig_restore_state':                                              &#9618;      
      &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       &#9618;      
      &#9474; arguments to function 'pci_restore_state'                                  &#9618;      
      &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1       &#9618;      
      &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618;      
      &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618;      
      &#9474; make[3]: *** [modules] Error 2                                             &#9618;      
      &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'      &#9618;      
      &#9474; make[2]: *** [compile] Error 2                                             &#9618;      
      &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;      
      &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;      
      &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                         
      &#9474; make: *** [kdist_image] Error 2    
Other people have had this same error before, but noone gave any response. It would seem that I might have to just go back to windows on this machine. I know that there are millions of these sound cards out there, so somebody has to have figured out a workaround. Any help would be much appreciated.

---

### Post by Tango_Down on 2007-11-22
Bump. Anybody? Should I try and update to Gusty to see if anything changes?

---

