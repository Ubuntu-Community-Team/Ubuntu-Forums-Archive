---
title: "[SOLVED] Hauppauge 1600 -- installing drivers"
date: 2008-11-05
forum: Multimedia Software
---

### Post by scott_g on 2008-11-05
Hi,

I'm running Ubuntu 8.04, on kernel version 2.6.24-21-generic, and am trying to install the drivers for a Hauppauge 1600 TV-tuner.  I've done it before, but seem to be running into problems this time.  I know I can upgrade to Intrepid for the card to be supported automatically, but I don't really want to.

I've been following the guide here: [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

And have gotten to step 1. b.  When I type 'make', I get the following error:

```

make -C /home/scott/v4l-dvb/v4l 
make[1]: Entering directory `/home/scott/v4l-dvb/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.24-21-generic/build
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/scott/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/scott/v4l-dvb/v4l/bttv-gpio.o
/home/scott/v4l-dvb/v4l/bttv-gpio.c: In function 'bttv_sub_add_device':
/home/scott/v4l-dvb/v4l/bttv-gpio.c:94: error: implicit declaration of function 'dev_set_name'
make[3]: *** [/home/scott/v4l-dvb/v4l/bttv-gpio.o] Error 1
make[2]: *** [_module_/home/scott/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/scott/v4l-dvb/v4l'
make: *** [all] Error 2

```

Has anyone seen this before or know what to do?

Thanks in advance,
Scott

---

### Post by qwertzqwertz on 2008-11-06
as simple workaround, if you NOT want to use the BTTV Modules just comment out the line: /home/scott/v4l-dvb/v4l/bttv-gpio.c:94

it works for me :)

you also should able to modify the makefile for not compile the unused modules

---

### Post by qwertzqwertz on 2008-11-06
STOP

isnt work :)

The Problem comes from /linux/device.h

iam searching for the bug...

---

### Post by jumper4000 on 2008-11-06
> **qwertzqwertz said:**
> as simple workaround, if you NOT want to use the BTTV Modules just comment out the line: /home/scott/v4l-dvb/v4l/bttv-gpio.c:94

it works for me :)

you also should able to modify the makefile for not compile the unused modules

I'm having the same exact problem. where exactly do I comment out this line?

thanks

---

### Post by jumper4000 on 2008-11-06
I ended up doing a "make -i" and it seem to have worked :)

---

### Post by qwertzqwertz on 2008-11-06
Problem solved.

actually you should use the [http://linuxtv.org/hg/v4l-dvb/rev/f367470bb25f](http://linuxtv.org/hg/v4l-dvb/rev/f367470bb25f) as you repo.


Newer kernels have a function called dev_set_name() in device.h
so the feisty kernel 2.6.24 NOT

and the great initiative of v4l to be actual removes the complety compatibility to the old device.h...

so just use a older source from the repo.


greets

---

### Post by scott_g on 2008-11-06
Yep; I actually solved this problem this morning, but didn't get around to posting until now...  I ended up using an older version, as qwertzqwertz suggested, by using the following command:

```

hg clone -r 9488 http://linuxtv.org/hg/v4l-dvb

```

To download the sources.  Everything works now...  

What does the -i flag do anyways?  Does that make the newer version work?  

Thanks for the help.
Scott

---

### Post by qwertzqwertz on 2008-11-06
-i does just ignore errors.

so, i think its compile fine but you will get no device and some errors in messages :)

---

