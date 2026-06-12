---
title: "compiling router's firmware"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by boosta on 2009-08-06
hi everybody,
i'm new here, and i'm a newbie since my knowledges and skills are still limited.
i wanted to do something but i realized, by doing, that i'm not able to bring it to a positive result.

i wanted to compile these router's firmware in order to run it on a x86 (Windows or Linux);
the router is a D-Link DI-524, it runs a Linux-based software on MIPS processor.

i don't need the compiling of the entire firmware, but ONLY this executable called "**rgbin**" (aqnd a few related ones), which can be found in these archive's paths:
.\di524\userland\target\usr\sbin\rgbin
.\di524\progs.priv\rgbin\Makefile
.\di524\progs.priv\rgbin\rgbin

here's btw the source code archive:
[ftp://ftp.dlink.co.uk/GPL/DI-524_E1_GPL.tgz](ftp://ftp.dlink.co.uk/GPL/DI-524_E1_GPL.tgz)
or
[ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz](ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz)

i hope someone can lend me a hand in doing that.
i'd be very thankful.
Regards!

PS: i read this (old) news:
[http://digg.com/linux_unix/DLINK_Sweden_providing_a_LINUX_port_for_the_DI_524_ROUTER](http://digg.com/linux_unix/DLINK_Sweden_providing_a_LINUX_port_for_the_DI_524_ROUTER)
but i wasn't able to find it on dlink.se site (also asked the support: vacation!)
maybe this? ...not sure
[ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz](ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz)

PS:
...Besides, i got a **config.bin** file, which i wanted to decrypt
it's MIPS binary: could it be disassembled and decoded ?

---

### Post by chili555 on 2009-08-07
> i don't need the compiling of the entire firmwareI'm afraid you do. Here are the steps I took.

1. Download and extract the GPL.tgz. (Right click, select "extract here.")
2. Open a terminal and:```
sudo apt-get install build-essential bison flex
cd di524
./toolchain.sh
source ./toolchain_path
make
```I got a few warnings and even errors, but 'make' ran fine and the files you need were created.

---

### Post by boosta on 2009-08-12
with Chili's help, we could state that the needed files (rgbin, rgdb...) don't seem to work :(

anybody have some ideas why? 
and how to solve the problem?

thanks

PS:
could this stuff play some role? 
[http://sourceware.org/gdb/papers/linux/](http://sourceware.org/gdb/papers/linux/)
[http://sourceware.org/gdb/papers/multi-arch/howto.html](http://sourceware.org/gdb/papers/multi-arch/howto.html)
from [http://www.gnu.org/software/gdb/documentation/](http://www.gnu.org/software/gdb/documentation/)

---

