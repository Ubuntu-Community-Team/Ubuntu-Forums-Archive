---
title: "CNet CWP-854 with rt2561 chipset not working."
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by haaglin on 2006-02-24
Hi. 

Does anybody got a wlan card with rt2561 chipset working? I just bought this card, and according to this site: [http://ralink.rapla.net/](http://ralink.rapla.net/) , my card has a rt2500 chipset,and breezy supports rt2500. But something must have changed, so now it has the rt2561 chipset, and i have no idea on how to get this working. Can someone help me?

---

### Post by crazycarl on 2006-04-07
I'm having the exact same problem.  so far I have tried using ndiswrapper using the rt61.inf and rt61.sys files that i pulled out of my windows directory after installing the card.  ndiswrapper installed them successfully but the card doesn't show up. i'm going to try a few more things, although i'm a linux newb and there are limits to what i know how to do.
if anyone has any input on our problems, would be appreciated.

---

### Post by crazycarl on 2006-04-07
ok I did a little research and the only rt 2561 driver I could find is the source from the ralink website.  so i downloaded and extracted it but when running the makefile i get an error 

> carl@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.0.3.0_200512230/Module$ make all
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/home/carl/Desktop/RT61_Linux_STA_Drv1.0.3.0_200512230/Module modules
make: *** /lib/modules/2.6.12-10-k7/build: No such file or directory.  Stop.
make: *** [all] Error 2

here is the part of the readme doc that explains how to compile the drivers:

> =======================================================================
Build Instructions:
====================

1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
    or
   $cp Makefile.RTL865x ./Makefile  #  big endian platform

3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt2561.bin /etc/Wireless/RT61STA/        # copy firmware
   $cp rt2561s.bin /etc/Wireless/RT61STA/
   $cp rt2661.bin /etc/Wireless/RT61STA/

6>  $dos2unix rt61sta.dat
    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat
    # !!!check if it is a binary file before loading !!!

7> $load
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up


Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version


here is the text of the makefile:
> # Comment/uncomment the following line to enable/disable debugging

WFLAGS = -DAGGREGATION_SUPPORT -DWMM_SUPPORT -Wall -Wstrict-prototypes -Wno-trigraphs
#WFLAGS += -DRALINK_ATE
#WFLAGS += -DSINGLE_ADHOC_LINKUP
#CFLAGS += -DDBG
CFLAGS+= $(WFLAGS)


obj-m := rt61.o

rt61-objs := rtmp_main.o mlme.o connect.o sync.o assoc.o auth.o auth_rsp.o rtmp_data.o rtmp_init.o sanity.o rtmp_wep.o rtmp_info.o eeprom.o rtmp_tkip.o wpa.o md5.o


all:
        make -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) modules
clean:
        rm -f *.o *~ .*.cmd *.ko *.mod.c

#make command :   make -C path/to/src SUBDIRS=$PWD modules
#example :        make -C /usr/src/linux-2.6.3-4mdk SUBDIRS=$PWD modules


can anyone help me?
thank you.  (maybe i should have posted this in the newbie forum, heh :P )

---

### Post by elhumano on 2006-05-03
There are some new drivers, the old ones ver. 1.0.3.0 did not work for me y have them in Dapper F6 maybe its time tu upgrade to ver. 1.0.4.0


[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

---

