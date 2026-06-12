---
title: "Trying to compile compat-wireless-2.6.31-rc7 on karmic"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by psychok7 on 2009-10-29
hey there..im trying to compile compat-wireless-2.6.31-rc7 on karmic because im having trouble connectiong to wpa networks(it constantly falls).
but i get an error message: 

khan@Karmic:~/Desktop/compat-wireless-2.6.31-rc7$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-14-generic/build M=/home/khan/Desktop/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/khan/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/built-in.o
make[3]: *** No rule to make target `/home/khan/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/khan/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/khan/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/khan/Desktop/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2


I read somewhere i should do a make mrpoper, but when i do it gives me another error : 
khan@Karmic:/usr/src/linux-headers-2.6.31-14$ make mrproper
/usr/src/linux-headers-2.6.31-14/ubuntu/aufs/Makefile:2: ubuntu/aufs/magic.mk: No such file or directory
make[2]: *** No rule to make target `ubuntu/aufs/magic.mk'.  Stop.
make[1]: *** [ubuntu/aufs] Error 2
make: *** [_clean_ubuntu] Error 2

Can anyone help me out?

---

