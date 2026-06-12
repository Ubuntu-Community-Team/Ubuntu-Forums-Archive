---
title: "Hardwire NIC slow and disconnect"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by max1e6 on 2012-01-17
Realtek 8111 NIC - Wired network
Ubuntu Lucid x64, kernel 2.6.32-37-generic
(This is a Win7 duel boot and the problem occurs at power up and boot to Lucid.)

Connection slow and drops frequently.

r8169 driver is the default module that is loaded

Available info indicates that the r8169 driver causes this problem and recommends installing the r8168 driver from Reaktek.
   Download: LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)
   Extract
   Run ./autorun.sh


I get:
rmmod r8169
Build the module and install
make[2]: *** No rule to make target `r8168/r8168-8.027.00/src'.  Stop.
make[1]: *** [clean] Error 2
make: *** [clean] Error 2

Realtek knows that this may happen and has a Q&A entry:

After &#8220;make clean modules&#8221;, the error message is show as below. That mean you don&#8217;t load kernel source. Please install kernel source first.

rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags.tmp_veions
make -C /lib/modules/2.6.11.4-21.7-smp/build SUBDIRS=/root/r1000_v1.05/src/src modules
make[1]: Entering directory /usr/sec/linux2.6.11.4.4-21.7-obj/x86-64/smp
make[1]:**no rule to make target 'modules'.stop
make[1]: leaving directory /usr/sec/linux2.6.11.4.4-21.7-obj/x86-64/smp
make :**[modules]Error 2


I get this exact output with make clean modules.


So I did this.

sudo apt-get install linux-source
sudo apt-get build-dep linux


Still have problem. What to do?

---

### Post by max1e6 on 2012-01-17
OK

There is a second school of thought on the solution; disable the Wake-on-lan power setting for the NIC in Windows. I did this and, so far so good. Perhaps, if this doesn't work out, I just have to cold start when I switch OSs.


I am still not sure why I had the make problem with the r8168 driver. Perhaps it's NFG for my kernel. After all, so far, it appears to be OK when I don't restart from Win7.

---

