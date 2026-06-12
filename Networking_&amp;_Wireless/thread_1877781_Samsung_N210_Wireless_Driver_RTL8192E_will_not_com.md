---
title: "Samsung N210 Wireless Driver RTL8192E will not compile on 11.10"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by jonnohudski on 2011-11-08
Hello again, REALTEK have sent me their recent Linux driver for their 8192E wireless network card.

I have been trying to compile it all day and have had no luck.

Firstly it was reporting that autoconf.h was missing, so i managed to link it to what i assume is the correct location (../generated/autoconf.h).

Secondly, it reported that modversions.h was missing. I couldn't find any mention of this problem in google, apart from 1 mention that suggested just touching it. So i did.

Now when I try to make the driver, i get the following

root@terri-N150-N210-N220:/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010# make
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2

So, loking at the forums, chilli555 suggests trying 

KBUILD_NOPEDANTIC=1 make all

so did and got the following, which to me seems to be saying that it didn't build anything.

make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'

But, being an optimist, I tried 

KBUILD_NOPEDANTIC=1 make install

which gave the following errors.

make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Entering directory `/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192'
install -p -m 644 r8192e_pci.o  /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
install: cannot stat `r8192e_pci.o': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192'
make: *** [install] Error 2

Now, I am a noob, so, please dont castigate me for my naivity. But can someone help?

My original problem is that my wireless keeps dropping out, and even when connected reports 1MB connection speed to my BT homehub 2 router.

Any help will be reallly appreciated.

---

### Post by pdc on 2011-11-09
I sense you are asking for help;

but your thread has been labelled SOLVED.......

........this may deter potential rescuers from coming to your help

---

