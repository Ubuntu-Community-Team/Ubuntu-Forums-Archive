---
title: "AVLD error install"
date: 2008-11-06
forum: Multimedia Software
---

### Post by vhs95 on 2008-11-06
Help in AVLD install

[http://allonlinux.free.fr/Projets/AVLD/](http://allonlinux.free.fr/Projets/AVLD/)


make && make install Fail in Ubuntu Intrepid 8.10 64bits (in ubuntu 8.04 64 works fine)


root@vhs-desktop:/home/vhs/Escritorio/avld_0.1.3# make && make install
make -C /lib/modules/2.6.27-7-generic/build M=/home/vhs/Escritorio/avld_0.1.3 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.27-7-generic'
CC [M] /home/vhs/Escritorio/avld_0.1.3/video_device.o
/home/vhs/Escritorio/avld_0.1.3/video_device.c: En la función ‘v4l_mmap’:
/home/vhs/Escritorio/avld_0.1.3/video_device.c:377: error: declaración implícita de la función ‘vmalloc_to_pfn’
/home/vhs/Escritorio/avld_0.1.3/video_device.c:377: aviso: conversión a puntero desde un entero de tamaño diferente
/home/vhs/Escritorio/avld_0.1.3/video_device.c:379: error: declaración implícita de la función ‘remap_pfn_range’
/home/vhs/Escritorio/avld_0.1.3/video_device.c:379: aviso: conversión de puntero a entero de tamaño diferente
/home/vhs/Escritorio/avld_0.1.3/video_device.c:379: error: ‘PAGE_SHARED’ no se declaró aquí (primer uso en esta función)
/home/vhs/Escritorio/avld_0.1.3/video_device.c:379: error: (Cada identificador no declarado solamente se reporta una vez
/home/vhs/Escritorio/avld_0.1.3/video_device.c:379: error: para cada funcion en la que aparece.)
/home/vhs/Escritorio/avld_0.1.3/video_device.c: En el nivel principal:
/home/vhs/Escritorio/avld_0.1.3/video_device.c:529: aviso: inicialización desde un tipo de puntero incompatible
/home/vhs/Escritorio/avld_0.1.3/video_device.c:531: aviso: inicialización desde un tipo de puntero incompatible
/home/vhs/Escritorio/avld_0.1.3/video_device.c:537: error: se especificó el campo desconocido ‘type’ en el inicializador
make[2]: *** [/home/vhs/Escritorio/avld_0.1.3/video_device.o] Error 1
make[1]: *** [_module_/home/vhs/Escritorio/avld_0.1.3] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

---

