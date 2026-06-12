---
title: "Problem getting rtl8185 wireless pci card to work"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-06-30
I have a pci wireless card manufactured by Belkin with the rtl8185 chip.

It can be seen with```
lspci -v
```which returns > 01:09.0 Ethernet controller: Belkin F5D7000 v7000 Wireless G Desktop Card [Realtek RTL8185] (rev 20)
    Subsystem: Belkin F5D7000 v7000 Wireless G Desktop Card [Realtek RTL8185]
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at 9000 [size=256]
    Memory at e4004000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: rtl8180
    Kernel modules: rtl8180I read that the rtl8180 driver module was flaky and that a new driver from Realtek fixes the problem. I downloaded rtl8185_linux_26.1031.1207.2009.release.tar.gz and navigated to the un tarred folder, ran make and got > denise@ubuntu-denise:~/Desktop/rtl8185$ make
make: *** /lib/modules/2.6.38-10-generic-pae/build: No such file or directory. Stop.
make: *** [all] Error 2I created a folder called build and then ran make again and got> denise@ubuntu-denise:~/Desktop/rtl8185$ make
make[1]: Entering directory `/lib/modules/2.6.38-10-generic-pae/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-10-generic-pae/build'
make: *** [all] Error 2I must be getting really rusty, any help gratefully received please.

---

### Post by Bucky Ball on 2011-06-30
You need:

```
sudo su
make
make install
```

;)

Have you plugged in a cable, gotten your updates and checked System>Administration>Additional Drivers?

---

### Post by bwallum on 2011-06-30
Still getting 'no rule to make target 'modules'' error...
> 
[EMAIL="root@ubuntu-denise:/home/denise/Desktop/rtl8185_linux_26.1031.1207.2009.releas"]root@ubuntu-denise:/home/denise/Desktop/rtl8185_linux_26.1031.1207.2009.releas[/EMAIL]e/rtl8185# make
make -C /lib/modules/2.6.38-10-generic-pae/build M=/home/denise/Desktop/rtl8185_linux_26.1031.1207.2009.release/rtl8185 CC=gcc modules
make[1]: Entering directory `/lib/modules/2.6.38-10-generic-pae/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-10-generic-pae/build'
make: *** [modules] Error 2

---

