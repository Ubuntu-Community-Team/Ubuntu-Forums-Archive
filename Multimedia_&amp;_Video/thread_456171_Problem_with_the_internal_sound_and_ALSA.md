---
title: "Problem with the internal sound and ALSA"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by kblcuk on 2007-05-27
Hi all!

While installing the drivers for the audiocard, and following the instructions on the [ALSA-project website](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0), I've got loads of errors after I start the "make" line:

```

<...>
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[2]: *** [/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/home/kblc/Desktop/alsadrv/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2

```

this occurs after I start "make" in the line ```
"./configure --with-cards=intel8x0 --with-sequencer=yes;make;make install"
```

the ./configure itself also gives quite a strange ending, like this:

```
Hacking autoconf.h...

```

Since I'm quite a newbie to ubuntu (and linux in general - just installed it this morning), I feel quite confused. :(

Tried to google for some answers, but haven't found anything valuable.
Motherboard model is Asus M2NPV-VM, and it has integrated sound. ALSA driver version is 1.0.13, I've tried to install older versions, but still same errors.

I first tried to install the drivers for my E-Mu 0404 usb, but got the same errors... so I tried to install at least the internal soundcard, but still..

Any suggestions?

Thnx in advance.

---

### Post by arijarot on 2007-05-27
This might help [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

