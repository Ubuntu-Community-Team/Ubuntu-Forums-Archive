---
title: "Sound Blaster Live! - Problems..."
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by SLA_leandrin on 2007-07-07
Hi guys, I've followed the

"Comprehensive Sound Problem Solutions Guide v0.5e"

Wich is excellent... and I've tryied all the different solutions, but I can't get my Sound Blaster Live to work.
I have problems compiling my alsa driver, wich is emu10k1. 

I've downloaded the alsa-source and when I try to compile it I get an error in Make... this is the output:

```
make[1]: se ingresa al directorio `/home/leandro/src/alsa/alsa-driver-1.0.12rc2/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include  -I/usr/src/linux-headers-2.6.20-16-generic/include -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -Wdeclaration-after-statement -Wno-pointer-sign -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /usr/src/linux-headers-2.6.20-16-generic/include/linux/modversions.h   -DEXPORT_SYMTAB -c hwdep.c
cc1: error: /usr/src/linux-headers-2.6.20-16-generic/include/linux/modversions.h: No existe el fichero ó directorio
In file included from /usr/src/linux-headers-2.6.20-16-generic/include/asm/percpu.h:5,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:9,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/asm-generic/percpu.h:8: error: ‘CONFIG_NR_CPUS’ no se declaró aquí (no en una función)
In file included from /usr/src/linux-headers-2.6.20-16-generic/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:9,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ no se declaró aquí (no en una función)
/usr/src/linux-headers-2.6.20-16-generic/include/asm/processor.h:82: error: la alineación solicitada no es una constante
En el fichero incluído de /usr/src/linux-headers-2.6.20-16-generic/include/linux/sched.h:51,
                 de /usr/src/linux-headers-2.6.20-16-generic/include/linux/utsname.h:35,
                 de /usr/src/linux-headers-2.6.20-16-generic/include/asm/elf.h:12,
                 de /usr/src/linux-headers-2.6.20-16-generic/include/linux/elf.h:7,
                 de /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:15,
                 de /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 de /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 de hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:225:31: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:269:46: error: división por cero en #if
In file included from /usr/src/linux-headers-2.6.20-16-generic/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:15,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_to_msecs’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:274: error: (Cada identificador no declarado solamente se reporta una vez
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:274: error: ara cada funcion en la que aparece.)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:280:46: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_to_usecs’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:293:46: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘msecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:306:46: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘usecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘timespec_to_jiffies’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_to_timespec’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘timeval_to_jiffies’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_to_timeval’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:400:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_to_clock_t’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘clock_t_to_jiffies’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:431:6: error: división por cero en #if
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h: En la función ‘jiffies_64_to_clock_t’:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
In file included from /usr/src/linux-headers-2.6.20-16-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/slab.h:14,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/rcupdate.h:41,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/sched.h:72,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:15,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/mmzone.h: En el nivel principal:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/mmzone.h:43: error: la alineación solicitada no es una constante
/usr/src/linux-headers-2.6.20-16-generic/include/linux/mmzone.h:85: error: la alineación solicitada no es una constante
/usr/src/linux-headers-2.6.20-16-generic/include/linux/mmzone.h:282: error: la alineación solicitada no es una constante
In file included from /usr/src/linux-headers-2.6.20-16-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/sched.h:72,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:15,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/linux/rcupdate.h:71: error: la alineación solicitada no es una constante
/usr/src/linux-headers-2.6.20-16-generic/include/linux/rcupdate.h:74: error: la alineación solicitada no es una constante
En el fichero incluído de /usr/src/linux-headers-2.6.20-16-generic/include/linux/module.h:21,
                 de /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:45,
                 de /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 de hwdep.c:22:
/usr/src/linux-headers-2.6.20-16-generic/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 from hwdep.c:22:
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:719: error: redefinición de ‘jiffies_to_msecs’
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:268: error: la definición previa de ‘jiffies_to_msecs’ estaba aquí
En el fichero incluído de /home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/sound/driver.h:46,
                 de hwdep.c:22:
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:721:31: error: división por cero en #if
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: En la función ‘jiffies_to_msecs’:
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:726: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: En el nivel principal:
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:738: error: redefinición de ‘msecs_to_jiffies’
/usr/src/linux-headers-2.6.20-16-generic/include/linux/jiffies.h:290: error: la definición previa de ‘msecs_to_jiffies’ estaba aquí
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:742:31: error: división por cero en #if
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: En la función ‘msecs_to_jiffies’:
/home/leandro/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:747: error: ‘CONFIG_HZ’ no se declaró aquí (primer uso en esta función)
make[1]: *** [hwdep.o] Error 1
make[1]: se sale del directorio `/home/leandro/src/alsa/alsa-driver-1.0.12rc2/acore'
make: *** [compile] Error 1

```

Anyone can help me?? Please!!!???

Cheers!!

---

### Post by SLA_leandrin on 2007-08-14
The problem still here.
I've compiled the alsa-xxx-1.0.14 (driver, lib & utils) for my emu10k1 SBLive!.
However, when I try to insert the module snd-emu10k1 into the kernell I get the following error:

```
FATAL: Error running install command for snd_emu10k1(/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Invalid argument
FATAL: Error running install command for snd_emu10k1 
```

I've tryied "sudo alsaconf" and chosen "emu10k1"... it seems to be working fine but when I ask "sudo lshw -class sound" my SB Live! EMU10k1 remain as "UNCLAIMED"...

Any ideas?
Thanks.

---

