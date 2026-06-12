---
title: "LIRC in Feisty Fawn."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by medeshago on 2007-04-29
I followed this guide:

[http://ubuntuforums.org/showthread.php?t=288229&highlight=lirc](http://ubuntuforums.org/showthread.php?t=288229&highlight=lirc)

I've tried this with the remote from a flyvideo 2000 card in Feisty Fawn.

The proble is that i get this with "make":

make[5]: *** [/usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1/drivers/lirc_gpio] Error 2
make[4]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/usr/src/lirc-0.8.1'
make: *** [all] Error 2

and i get this if i try to continue with "make install":

medeshago@nosotros:/usr/src/lirc-0.8.1$ sudo make install
Making install in drivers
make[1]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers'
Making install in lirc_dev
make[2]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[3]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
test -c /dev/lirc || (/bin/bash ../../mkinstalldirs /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash ../../mkinstalldirs /lib/modules/2.6.20-15-generic/misc
 /usr/bin/install -c -m 644 lirc_dev.ko /lib/modules/2.6.20-15-generic/misc/lirc_dev.ko
/sbin/depmod -a
make[3]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
Making install in lirc_gpio
make[2]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[2]: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/usr/src/lirc-0.8.1/drivers'
make: *** [install-recursive] Error 1


That's it. I can't get it to work.

---

