---
title: "How to find network device in Ubuntu?"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by anoopajay87 on 2011-11-14
Hi...I'm using Linux server ed., 11.04 ver
Just I want to find Intel NIC card on PCI bus.
I used the code by using the command: [B]vi loadbal1.c
[/B]
```
/*Program to detect nerwork driver*/
#define REALTEK_VENDER_ID 0x10EC
#define REALTEK_DEVICE_ID 0x8139
#include<linux/kernel.h>
#include<linux/module.h>
#include<linux/stddef.h>
#include<linux/pci.h>

int init_module(void)
     {
        struct pci_dev *pdev;
        pdev = pci_find_device(REALTEK_VENDER_ID, REALTEK_DEVICE_ID, NULL);
        if(!pdev)
           printk("<1>Device not found\n");
        else
           printk("<1>Device found\n");
        return 0;
     }

```
**After that I created Makefile using the command : vi Makefile**
obj-m = loadbal1.o
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

**When I compiled using make the error is shown as:**
san@ubuntuServer:~$ make
make -C /lib/modules/2.6.38-8-generic-pae/build M=/home/santhosh modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /home/santhosh/loadbal1.o
/home/santhosh/loadbal1.c: In function ‘init_module’:
/home/santhosh/loadbal1.c:12:9: error: implicit declaration of function ‘pci_find_device’
/home/santhosh/loadbal1.c:12:14: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/santhosh/loadbal1.o] Error 1
make[1]: *** [_module_/home/santhosh] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [all] Error 2
 
**Even I was encountered a problem when I used gcc compiler:**
san@ubuntuServer:~$ gcc loadbal1.c
loadbal1.c:7:25: fatal error: linux/module.h: No such file or directory
compilation terminated.

Can someone please suggest on this.

Many thanks..

---

