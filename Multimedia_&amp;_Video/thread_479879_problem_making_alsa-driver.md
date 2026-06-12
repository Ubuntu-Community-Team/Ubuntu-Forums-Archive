---
title: "problem making alsa-driver"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by Jon.burgin on 2007-06-20
Hi All!
I was following the sound problems guide here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer)
when I got the following error when doing the " Using alsa-source" section:

```

make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2
```

Any ideas on where to go from here?  Sound sure would be nice. 
By the way here is my card info:
```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 300d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1000 [size=256]
        I/O ports at 1400 [size=64]
        Memory at f0200400 (32-bit, non-prefetchable) [size=512]
        Memory at f0200600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```
 
and I was trying to compile in the intel8x0 driver.

Any help at all would be greatly appreciated!
Jon

---

