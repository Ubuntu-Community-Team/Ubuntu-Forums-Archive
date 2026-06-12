---
title: "Please help me to build driver for my ethernet"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by ras123 on 2013-05-23
Hi,
I have a TP-Link TF3200 network card in PCI slot, it is not working, so I think because of no driver for the same in my Ubuntu 12.04. Got the source from manufacture's website, but I couldn't compile it. 
> sundance_main.c:192:26: fatal error: linux/module.h: No such file or directory
compilation terminated.
But it is in my computer "/usr/src/linux-headers-3.2.0-39-generic-pae" directory. I attached the source with this, so kindly help me to compile it, Or any prebuilt driver available?

[ATTACH]242946[/ATTACH]

Thanking You,
Ras

---

### Post by linuxtechguy on 2013-05-23
[http://ubuntuforums.org/showthread.php?t=1695654](http://ubuntuforums.org/showthread.php?t=1695654)

---

### Post by sanderj on 2013-05-23
If you live-boot Ubuntu 13.04 from CD/USB-stick, does the network card work correctly?

---

### Post by ras123 on 2013-06-08
Sorry for the delay. I am using Ubuntu 12.04, yes it is worked with 13.04 booted from USB stick. But I wouldn't like to upgrade now. I think the problem will solve by the unistalling and installing the driver, how to do this?
Ras

---

### Post by open-nandra on 2013-06-08
Hi,

hmm driver code + Makefile is pretty old. With following Makefile (pls update KROOT path) you will be able to start compilation but it failed (tested on 13.04):
```

 obj-m += sundance.o

sundance-y := mii.o sundance_main.o


KROOT = /lib/modules/3.8.0-22-generic/build/


all:
    @$(MAKE) -C $(KROOT) M=$(PWD) modules
clean:
    rm -rf   Module.symvers modules.order *.o *.ko



```

---

### Post by ras123 on 2013-06-09
But now I believe that the driver is included with 13.04 and may also with 12.04, because it is working with Ubuntu 13.04 when booted from USB drive. But I like to continue with 12.04, and may be the problem is because of the previously configured LAN card (which was damaged), so how to remove/purge the previous driver/config etc. and re-install the sundance driver?

---

### Post by open-nandra on 2013-06-11
Can you try that: [http://xaie.wordpress.com/2011/10/07/tp-link-tf-3200-on-debian/](http://xaie.wordpress.com/2011/10/07/tp-link-tf-3200-on-debian/)

Also on my 12.04 I have sundance.ko module available.

---

### Post by ras123 on 2013-06-12
I formatted and upgraded to 13.04, now solved

---

