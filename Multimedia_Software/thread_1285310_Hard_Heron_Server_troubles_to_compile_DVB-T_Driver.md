---
title: "Hard Heron Server troubles to compile DVB-T Driver"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Tweek19 on 2009-10-07
Hello Everybody!

I got a very big problem, i bought a Terratec Cinergy T Stick and would use it on my Hardy heron Server. On my Jaunty Client everything went fine, no troubles to compile the driver. But on the hardy server it won't work.

I followed the instructions from this page (Method A)
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_A](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_A)

On Jaunty it works but why not on Hardy Heron?

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-server'
  CC [M]  /home/server/Download/Downstream/terratec_af9035-a_m/af9035.o
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:33: warning: data definition has no type or storage class
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:33: warning: type defaults to ?int? in declaration of ?DVB_DEFINE_MOD_OPT_ADAPTER_NR?
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:33: warning: parameter names (without types) in function declaration
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c: In function ?af9035_usb_probe?:
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:871: error: ?adapter_nr? undeclared (first use in this function)
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:871: error: (Each undeclared identifier is reported only once
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:871: error: for each function it appears in.)
/home/server/Download/Downstream/terratec_af9035-a_m/af9035.c:871: error: too many arguments to function ?dvb_usb_device_init?
make[2]: *** [/home/server/Download/Downstream/terratec_af9035-a_m/af9035.o] Error 1
make[1]: *** [_module_/home/server/Download/Downstream/terratec_af9035-a_m] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-server'
make: *** [default] Error 2
```

Thats the error i get on make.

I really hope anybody can help me that would be great!
Thank you very mutch!

Best regards

---

### Post by Jose Catre-Vandis on 2009-10-07
You may need to install build essential (inc. gcc) and headers to ensure you can "make"

---

### Post by Tweek19 on 2009-10-08
Hello!

Thanks for your answer, but i already have installed the build essential inkl. gcc. I also have installed the linux headers.

Maybe there are some troubles in the makefile?

Here is it:

```
# (C) 2009 Andrea Mennucc <mennucc1@debian.org>
# License: GPL

#### CONFIGURE THE FOLLOWING LINES
#the precompiled kernel headers
KDIR = /usr/src/linux-headers-2.6.30-1-686
#the unpacked kernel source
KSRC = /usr/src/linux-source-2.6.30
#where the modules will be installed
KINSTALL = /lib/modules/linux-2.6.30-1-686/misc
#### END OF CONFIGURABLE LINES

EXTRA_CFLAGS = -DDETACHED_TERRATEC_MODULES -I$(KDIR)/drivers/media/dvb/dvb-usb/ -I$(KDIR)/drivers/media/dvb/dvb-core/  -I$(KDIR)/drivers/media/dvb/frontends/  -I$(KSRC)/drivers/media/dvb/dvb-usb/ -I$(KSRC)/drivers/media/dvb/dvb-core/  -I$(KSRC)/drivers/media/dvb/frontends/

module= af9033 tua9001 dvb-usb-af9035
dvb-usb-af9035-objs = af9035.o
obj-m +=  tua9001.o dvb-usb-af9035.o af9033.o

default:
	make -C $(KDIR) SUBDIRS=$(PWD) modules

install:
	cp af9033.ko dvb-usb-af9035.ko tua9001.ko $(KINSTALL)
	depmod -a

clean::
	-rm -f  *.o  *.ko *.mod.c .*.o.cmd  .*.o.d  .*.ko.cmd Module.symvers Module.markers modules.order
	-rm -rf .tmp_versions

```

Best regards

---

### Post by Jose Catre-Vandis on 2009-10-08
Are you able to run 
```
./configure
```

????

This might tell you what is not there?

---

### Post by Tweek19 on 2009-10-08
Thanks for your answer, but i already found another way to solve this problem. I used a patched source so it was no problem to compile :)

Thanks anyway

---

