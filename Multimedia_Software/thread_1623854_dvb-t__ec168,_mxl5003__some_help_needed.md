---
title: "dvb-t : ec168, mxl5003 : some help needed"
date: 2010-11-17
forum: Multimedia Software
---

### Post by then_dude on 2010-11-17
hello everybody,

i'm new here, and i'm trying to get up and running my ubuntu 10.04; i have migrated to ubuntu, cause if i don't do it now, i will never do it. ....

a lot of things are already working, but the dvb-t usb dongle isn't

it is an obscure model : an ec168 and an mxl5003 chipset. 

i have looked around and done a lot of things that i have read, but it isn't working; 
so here i am, the problem might also be that i have tempered with the system so badly that maybe some things go wrong or strange. 

anyway

i have followed this link


[https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942]("https://www.dealextreme.com/forums/Default.dx/sku.8325%7Ethreadid.278942")
[http://ubuntuforums.org/showthread.php?t=1233308&page=2](http://ubuntuforums.org/showthread.php?t=1233308&page=2)

this is wat is stated there (in the first link)

I did this on a Ubuntu system (9.04 x86_64) 

First install Mercurial: 

**sudo apt-get install mercurial** 

Then get the source for the driver and the v4l and dvb-system with mercurial: 

**hg clone [http://linuxtv.org/hg/~anttip/ec168/]("http://linuxtv.org/hg/%7Eanttip/ec168/")** 

When it completes downloading, go into the folder **~/ec168/** and run **make**. 

Hopefully the compiling goes well, then you will have a lot of modules in the **~/ec168/v4l/** subfolder. 

Then you have to download the firmware from [http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw](http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw) 

( This file can also be found on your driver CD, called EC168BDA.bin. This has to be renamed to dvb-usb-ec168.fw ) 

Put this file in **/lib/firmware/** 

Then load the following modules from the **~/ec168-2/v4l/** folder: 

**sudo insmod dvb-core.ko** 
**sudo insmod dvb-usb.ko** 
**sudo insmod ec100.ko** 
**sudo insmod mxl5005s.ko** 
**sudo insmod dvb-usb-ec168.ko** 

[COLOR=Red]**WHAT NOW FOLLOWS are the commandos and the probems I encounter**[/COLOR]

**sudo apt-get install mercurial**  : OK, everything went fine

**hg clone [http://linuxtv.org/hg/~anttip/ec168/]("http://linuxtv.org/hg/%7Eanttip/ec168/")**  : OK, worked for me

 **~/ec168/** and run **make**.  : NOT OKEE

a)i get an error in the firedtv1394

i have read on this forum  that i must "disable" the firedtv in the .config file

b)MAKE : the compiler start to compile but gives an error (i run it twice, second time to get  the error message)[INDENT]make -C /home/filip/ec168/v4l 
make[1]: Entering directory `/home/filip/ec168/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/filip/ec168/v4l/firmware'
make[2]: Leaving directory `/home/filip/ec168/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/filip/ec168/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/filip/ec168/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-25-generic/build
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/home/filip/ec168/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/filip/ec168/v4l/ir-sysfs.o
/home/filip/ec168/v4l/ir-sysfs.c: In function 'ir_register_class':
/home/filip/ec168/v4l/ir-sysfs.c:268: error: 'ir_raw_dev_type' undeclared (first use in this function)
/home/filip/ec168/v4l/ir-sysfs.c:268: error: (Each undeclared identifier is reported only once
/home/filip/ec168/v4l/ir-sysfs.c:268: error: for each function it appears in.)
make[3]: *** [/home/filip/ec168/v4l/ir-sysfs.o] Error 1
make[2]: *** [_module_/home/filip/ec168/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/filip/ec168/v4l'
make: *** [all] Error 2
[/INDENT]so this is it people, this is as far as i get

thanks

---

### Post by tpruvot on 2010-12-04
For Ubuntu 10.10 HowTo, Please read :

[http://tanguy.wdscript.fr/?q=EC168/](http://tanguy.wdscript.fr/?q=EC168/)

---

### Post by then_dude on 2010-12-12
hello everyone,

i got some problems,

my usb dvb-t was running, but then i uninstalled all the previous kernels that i didn't use anymore, and gone was my tv, 

1) is this normal ? 

so i am back fiddling with the system, and it seems that i cannot get it up and running. 
i have 10.04 so not the 10.10.  still i was looking at the link, and i expect it to work too. 

the problem i have is : how do i get  **Direct Firmware Utility - dfu-ec168 ** and what to do with it, 

thanks a lot

---

### Post by Dooa on 2011-02-10
Hey Dude, I had similar problems. You are going to face to issues
1) FIREDTV error
2)ir-sysfs.c Error

Follow this link word to word and let us know how you went. (Link is in French)

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10231466](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10231466)

---

### Post by Unkuiri on 2011-03-25
Hi, now the command: "hg clone http://linuxtv.org/hg/~anttip/ec168/" is not working for me, it shows:
"abortado: requisito '<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">' não suportado!"

Before it worked very well for me for many kernel's, now I can't do that anymore...:(...in the tanguy site ([http://tanguy.wdscript.fr/EC168](http://tanguy.wdscript.fr/EC168)) he says:"Antti has merged driver in v4l-dvb master. . It is also merged to the kernel 2.6.33 which will be released about one month from that day."

Now the question is how can we install it in lucid that only uses kernel 2.6.32-30?

Thanks in advance

---

### Post by Cortex83 on 2011-10-06
Hello,

I have posted a solution here : [http://doc.ubuntu-fr.org/ec168](http://doc.ubuntu-fr.org/ec168)
It's in French but you can get the commands and try it.
Do not hesitate to ask for more information if you need some.

Sylvain

---

