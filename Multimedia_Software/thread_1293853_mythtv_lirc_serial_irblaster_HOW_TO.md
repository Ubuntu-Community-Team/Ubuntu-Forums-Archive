---
title: "mythtv lirc serial irblaster HOW TO"
date: 2009-10-17
forum: Multimedia Software
---

### Post by gslauen on 2009-10-17
I am trying to get a store bought serial irblaster to change channels on a motorola cable box. I seem to have a problem just getting the myth-ledxmit to run I get errors when it is compiling.

make[5]: *** [/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev/ledxmit_dev.o] Error 1
make[4]: *** [_module_/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[3]: *** [ledxmit_dev.o] Error 2
make[3]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP'
make: *** [all] Error 2
I can supply the whole output if you need it.

I am really hoping you can help me with this. I am no linux guru but I have mangaged to get my system up and running for sometime now.
I don't understand the errors.

When I try to run sudo make install I get these errors

make[5]: *** [/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev/ledxmit_dev.o] Error 1
make[4]: *** [_module_/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[3]: *** [ledxmit_dev.o] Error 2
make[3]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers/ledxmit_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/greg/myth-ledxmit/myth-ledxmit.WIP'
make: *** [all] Error 2

this is my tty output
dmesg | grep ttyS[ 45.823811] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 45.825608] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
and I am using

Distributor ID: Ubuntu
Description: Ubuntu 8.04.3 LTS
Release: 8.04
Codename: hardy
If there is any info you need to help me resolve this I would be happy to pass this along.

Has anyone been able to get this working?

Any ideas?

Thanks so much
Greg [email]gbs@blaze.ca[/email]

---

