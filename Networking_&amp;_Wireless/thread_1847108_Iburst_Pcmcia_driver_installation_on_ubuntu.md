---
title: "Iburst Pcmcia driver installation on ubuntu"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by Firstlaw on 2011-09-20
Hello 
I've searched every where for a solution to this , but all information are either on older systems 
I have a 11.04 ubuntu and I'm trying to install the Iburst USB dongle drivers
i've downloaded the drivers for it from 

[http://sourceforge.net/projects/ibdriver/](http://sourceforge.net/projects/ibdriver/)

the first problem i had was not being able to complie the drivers 
because i dont have pcmcia/cs.h and the rest of the files 
I dont have pcmcia to begin with , i ended up finding a pcmcia folder online which i downloaded and put in the same folder i'm working on and changed the 
#include <pcmcia/cs.h> 
etc...
to #include "cs.h" 
and I did the rest 
in any case 
i've got all the files together but now i get this 
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/onemoon/Desktop/Mobi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/onemoon/Desktop/Mobi/ib-net.o
  CC [M]  /home/onemoon/Desktop/Mobi/ib-pcmcia.o
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_release’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:232:2: error: implicit declaration of function ‘pcmcia_disable_device’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_detach’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:241:40: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_close’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:557:2: error: implicit declaration of function ‘pcmcia_dev_present’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_config_callback’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:583:2: error: implicit declaration of function ‘pcmcia_parse_tuple’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:586:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:587:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_cftable_callback’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:615:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:617:7: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:618:7: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:632:7: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:635:7: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:638:2: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_config’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:650:40: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:660:2: error: implicit declaration of function ‘pcmcia_get_tuple’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:671:2: error: implicit declaration of function ‘pcmcia_loop_tuple’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:676:2: error: implicit declaration of function ‘pcmcia_loop_config’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:682:2: error: implicit declaration of function ‘pcmcia_request_configuration’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:682:48: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:691:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:692:2: error: implicit declaration of function ‘pcmcia_request_window’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:692:47: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_probe’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:744:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:745:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:746:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:747:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:748:6: error: dereferencing pointer to incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: At top level:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:756:32: error: array type has incomplete element type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:757:2: error: implicit declaration of function ‘PCMCIA_DEVICE_MANF_CARD’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:759:2: error: implicit declaration of function ‘PCMCIA_DEVICE_PROD_ID12’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:761:2: error: ‘PCMCIA_DEVICE_NULL’ undeclared here (not in a function)
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:770:15: error: variable ‘ib_pcmcia_driver’ has initializer but incomplete type
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:771:2: error: unknown field ‘owner’ specified in initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:771:2: warning: excess elements in struct initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:771:2: warning: (near initialization for ‘ib_pcmcia_driver’)
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:775:2: error: unknown field ‘probe’ specified in initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:775:2: warning: excess elements in struct initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:775:2: warning: (near initialization for ‘ib_pcmcia_driver’)
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:776:2: error: unknown field ‘remove’ specified in initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:776:2: warning: excess elements in struct initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:776:2: warning: (near initialization for ‘ib_pcmcia_driver’)
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:777:2: error: unknown field ‘id_table’ specified in initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:777:2: warning: excess elements in struct initializer
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:777:2: warning: (near initialization for ‘ib_pcmcia_driver’)
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_init’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:789:2: error: implicit declaration of function ‘pcmcia_register_driver’
/home/onemoon/Desktop/Mobi/ib-pcmcia.c: In function ‘ib_pcmcia_exit’:
/home/onemoon/Desktop/Mobi/ib-pcmcia.c:798:2: error: implicit declaration of function ‘pcmcia_unregister_driver’
make[2]: *** [/home/onemoon/Desktop/Mobi/ib-pcmcia.o] Error 1
make[1]: *** [_module_/home/onemoon/Desktop/Mobi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2


HELP PLEASE!!!!

---

### Post by praseodym on 2011-09-20
Hi,

please show the following outputs:

```
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
```
Did you install the kernel headers and the compilation tools before?

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```

---

### Post by praseodym on 2011-09-20
P.S.: The folder is named "xx-2.6.36", maybe it just doesnt work with kernel 2.6.38?!

---

### Post by Firstlaw on 2011-09-24
Thanks alot for your help praseodym
But i figured it out
My stupid mistake was that i thought my usb modem is pcmcia ... 
I simply edited the Makefile 
and removed the pcmcia.o
its complied the Usb Driver! :D 
and my Iburst terminal started working properly! 
and I used rogue penguin pppoe dialer as other posts mentioned 
and I was connected 
Note: the usb Iburst was called ib0 

Regards

---

### Post by Firstlaw on 2011-09-24
how do i change this thread to solved?
thanks again

---

### Post by DocMSK on 2011-10-23
Hi Firstlaw,

I am also trying to get my USB Iburst modem working. I have Ubuntu 11.10. Would you mind explaining in newbie terms how I can compile the iburst driver?

Many thanks

---

