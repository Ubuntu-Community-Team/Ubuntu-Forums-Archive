---
title: "mISDN on 9.04"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by mcfirstlast on 2009-05-20
Hi
 
I'm having trouble getting a supported USB ISDN TA running in 9.04, using 2.6.28-11-generic.
It seems the kernel config for mISDN is missing the USB drivers, and a modprobe for hfcsusb results in module not found error.
 
This page: [http://www.misdn.org/index.php/MISDN_v2_Installation](http://www.misdn.org/index.php/MISDN_v2_Installation) shows a listing of the mISDN components in the kernel config.  When I run:
 
```
make menuconfig
``` 
 
and go to the Device Drivers->ISDN Support->Modular ISDN Driver->
 
There is only HFC PCI and multiport cards listed under ***mISDN Hardware Drivers***, whereas this page [http://www.misdn.org/index.php/MISDN_v2_Installation](http://www.misdn.org/index.php/MISDN_v2_Installation) shows the USB drivers that I need.
 
I tried to compile current snapshot mISDN but resulted in these errors:
 
```

[EMAIL="root@laptop:/home/user/Desktop/mISDN"]root@laptop:/home/user/Desktop/mISDN[/EMAIL]# make
echo 1_2_0 > VERSION ; \
export LINUX=/lib/modules/2.6.28-11-generic/build; ./makelib.sh test_old_misdn
cp /home/user/Desktop/mISDN/drivers/isdn/hardware/mISDN/Makefile.v2.6 /home/user/Desktop/mISDN/drivers/isdn/hardware/mISDN/Makefile
cp /home/user/Desktop/mISDN/drivers/isdn/mISDN/Makefile.v2.6 /home/user/Desktop/mISDN/drivers/isdn/mISDN/Makefile
export MINCLUDES=/home/user/Desktop/mISDN/include ; export MISDNVERSION=1_2_0; make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/user/Desktop/mISDN/drivers/isdn/mISDN modules CONFIG_MISDN_DSP=m  CONFIG_MISDN_MEMDEBUG=y  CONFIG_MISDN_HFCMULTI=m  CONFIG_MISDN_HFCPCI=m CONFIG_MISDN_HFCUSB=m CONFIG_MISDN_XHFC=m CONFIG_MISDN_L1OIP=m  CONFIG_MISDN_L1LOOP=m CONFIG_MISDN=m  
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.o
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c: In function ‘channel_dctrl’:
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c:973: error: ‘MISDN_CTRL_GETPEER’ undeclared (first use in this function)
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c:973: error: (Each undeclared identifier is reported only once
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c:973: error: for each function it appears in.)
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c: In function ‘init_card’:
/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.c:1450: error: too many arguments to function ‘mISDN_register_device’
make[2]: *** [/home/user/Desktop/mISDN/drivers/isdn/mISDN/l1oip_core.o] Error 1
make[1]: *** [_module_/home/user/Desktop/mISDN/drivers/isdn/mISDN] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

```
 
 
Has anyone got a USB ISDN TA working?
 
Why does the 2.6.28-11 kernel not have the USB device drivers?
 
Thanks for listening

---

