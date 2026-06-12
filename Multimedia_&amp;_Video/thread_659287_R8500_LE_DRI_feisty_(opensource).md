---
title: "R8500 LE DRI feisty (opensource)"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Jabone on 2008-01-05
Hey

I have problem with DRI with my Radeon 8500 LE. I tried to use fglrx but it would not install ati installer complains about bad substitue but that's not this case...

I've problem with dri with my config. Every time I enable dri system freezes when trying to load gdm. Screen gots scrambled or goes in stand by state. Radeon module is loaded and everything is okay according to Xorg and GDM. 

I've compailed drm and dri/mesa from git and still get this problem. I tried to compile the xorg-driver-ati too, but it needs xserver-1.3 which is not in feisty? 

Have you guys got this working and can you give me instructions how to get dri and opengl to work with this card.

Thanks

- Jabone

---

### Post by Jabone on 2008-01-05
I noticed that I hadn't compiled radeon module, only drm. I tried compiling radeon module from git, but ended up with error message:



> ~/drm/linux-core$ make
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.20-16-generic"
  CC [M]  /home/kalakale/drm/linux-core/drm_compat.o
/home/kalakale/drm/linux-core/drm_compat.c: In function ‘drm_bo_vm_fault’:
/home/kalakale/drm/linux-core/drm_compat.c:235: error: ‘struct drm_bo_mem_reg’ has no member named ‘mask’
make[2]: *** [/drm/linux-core/drm_compat.o] Virhe 1
make[1]: *** [_module_/drm/linux-core] Virhe 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.20-16-generic"
make: *** [modules] Virhe 2


---

### Post by acoustibop on 2008-01-05
The Radeon 8500 is not supported by current fglrx drivers, Jabone.  The last driver that suppoted it was the 8.28.8 one, which is about 1 1/2 years old.  Get it from the [ATI driver site]("http://ati.amd.com/support/driver.html") - just select Linux x86 or Linux x86_64 as appropriate, Radeon, ATI Radeon 8500 series and click GO.

---

### Post by Jabone on 2008-01-06
Hi! 
I'm trying to use the opensource drivers. Couldn't get the 8.28.8 drivers to install becouse of "Bad substitute or something" 

Radeon opensource driver has support for 8500 but I couldn't get opengl to work. With dri enabled systems locks up and only option is to reboot.

---

