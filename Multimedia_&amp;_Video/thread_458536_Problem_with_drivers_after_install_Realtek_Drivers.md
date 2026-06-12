---
title: "Problem with drivers after install Realtek Drivers"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by cliffdover88 on 2007-05-29
Hi, i install today the realtek drivers on realtek web, and after reboot all sound devices are disappeared
 

when i try to reinstall everything, after do MAKE in alsa-drivers in the compiling process i get some errors:


/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h:726: error: redefinición de ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: la definición previa de ‘jiffies_to_msecs’ estaba aquí
/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h:745: error: redefinición de ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: la definición previa de ‘msecs_to_jiffies’ estaba aquí
In file included from /home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h:842,
                 from /home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/sound/driver.h:46,
                 from /home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/acore/hwdep.c:22:
include/linux/pci.h:541: error: expected identifier or ‘(’ before numeric constant
In file included from /home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/sound/driver.h:46,
                 from /home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/acore/hwdep.c:22:
/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h: En la función ‘snd_pci_orig_save_state’:
/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h:1083: error: demasiados argumentos para la función ‘pci_save_state’
/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h: En la función ‘snd_pci_orig_restore_state’:
/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/include/adriver.h:1087: error: demasiados argumentos para la función ‘pci_restore_state’
make[3]: *** [/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/acore/hwdep.o] Error 1
make[2]: *** [/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f/acore] Error 2
make[1]: *** [_module_/home/cliffdover88/realtek-linux-audiopack-4.05f/alsa-driver-1.0.12-4.05f] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

(I tried automatic install too, but alsaconf dont find any sound device :S)

Thanks for your responses and sorry for my bad english xD

---

### Post by Blender on 2007-05-29
What sound card is that? Or what mobo?

The realtek drivers are generally broken. And, IIRC, they are pretty much a copy of what's already in the kernel. So just don't use them.

Could you post the output of **dmesg**, **lspci**, and **/sbin/lsmod** (Open Applications->Accessories->Terminal and type the commands there, copying the output of each one).

---

### Post by cliffdover88 on 2007-05-29
problem solved, thanks anyway

---

### Post by Blender on 2007-05-29
Well, it'd be nice if you posted a short summary of how you solved your problem. Might be useful for someone ;)

---

### Post by albox on 2007-05-31
I'm having the same issue while compiling alsa-driver-1.0.13. I'm using the 2.6.20-15-generic kernel. Can you tell me how you solved this ?

Thanks :D

---

### Post by bdig on 2007-07-03
Yeah, I'd appreciate it if you could post a summary of how you solved your problem, because I just borked my sound with Realtek drivers too!

---

