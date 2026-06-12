---
title: "Drivers for Polar Irda usb adapter?"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by NilsErik on 2009-06-20
I'm trying to install the Polar Irda usb adapter (it's usb 1.1 based on the MCS7780 chipset) on my computer running Ubuntu 9.04, the Jaunty Jackalope (32-bit). The kernel is 2.6.28-13-generic.

The drivers following the usb would not compile :(
> diablito@NilsErik-Laptop:~/Skrivebord/Linux$ sudo make
[sudo] password for diablito: 
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/diablito/Skrivebord/Linux modules;
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/diablito/Skrivebord/Linux/mcs7780.o
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:81: error: expected ‘)’ before string constant
/home/diablito/Skrivebord/Linux/mcs7780.c:145: error: unknown field ‘owner’ specified in initializer[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c:145: warning: initialization from incompatible pointer type
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_probe’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:279: error: implicit declaration of function ‘SET_MODULE_OWNER’[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_disconnect’:
/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: (Each undeclared identifier is reported only once
/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: for each function it appears in.)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_rx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1099: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1104: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_async_bump’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1228: error: ‘struct sk_buff’ has no member named ‘mac’[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_tx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1276: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1280: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
make[2]: *** [/home/diablito/Skrivediablito@NilsErik-Laptop:~/Skrivebord/Linux$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/diablito/Skrivebord/Linux modules;
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/diablito/Skrivebord/Linux/mcs7780.o
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:81: error: expected ‘)’ before string constant
/home/diablito/Skrivebord/Linux/mcs7780.c:145: error: unknown field ‘owner’ specified in initializer
[/COLOR]/home/diablito/Skrivebord/Linux/mcs7780.c:145: warning: initialization from incompatible pointer type
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_probe’:
/home/diablito/Skrivebord/Linux/mcdiablito@NilsErik-Laptop:~/Skrivebord/Linux$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/diablito/Skrivebord/Linux modules;
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/diablito/Skrivebord/Linux/mcs7780.o
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:81: error: expected ‘)’ before string constant
/home/diablito/Skrivebord/Linux/mcs7780.c:145: error: unknown field ‘owner’ specified in initializer
/h[/COLOR]ome/diablito/Skrivebord/Linux/mcs7780.c:145: warning: initialization from incompatible pointer type
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_probe’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:279: error: implicit declaration of function ‘SET_MODULE_OWNER’
/[/COLOR]home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_disconnect’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: (Each undeclared identifier is reported only once
/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: for each function it appears in.)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_rx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1099: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1104: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_async_bump’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1228: error: ‘struct sk_buff’ has no member named ‘mac’[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_tx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1276: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1280: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
[COLOR=DarkRed]make[2]: *** [/home/diablito/Skrivebord/Linux/mcs7780.o] Error 1
make[1]: *** [_module_/home/diablito/Skrivebord/Linux] Error 2[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2s7780.c:279: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_disconnect’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: (Each undeclared identifier is reported only once
/home/diablito/Skrivebord/Linux/mcs7780.c:355: error: for each function it appears in.)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_rx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1099: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1104: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_async_bump’:
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1228: error: ‘struct sk_buff’ has no member named ‘mac’[/COLOR]
/home/diablito/Skrivebord/Linux/mcs7780.c: In function ‘mcs7780_tx_submit’:
/home/diablito/Skrivebord/Linux/mcs7780.c:1276: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
[COLOR=DarkRed]/home/diablito/Skrivebord/Linux/mcs7780.c:1280: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
make[2]: *** [/home/diablito/Skrivebord/Linux/mcs7780.o] Error 1
make[1]: *** [_module_/home/diablito/Skrivebord/Linux] Error 2[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
[COLOR=DarkRed]make: *** [default] Error 2bord/Linux/mcs7780.o] Error 1
make[1]: *** [_module_/home/diablito/Skrivebord/Linux] Error 2[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
[COLOR=DarkRed]make: *** [default] Error 2[/COLOR]
I can see the usb on my pc:> 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=DarkRed]Bus 007 Device 011: ID 9710:7780 MosChip Semiconductor MS7780 4Mbps Fast IRDA Adapter[/COLOR]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBut without any drivers I can't get it to work...
I'm not an advanced Linux/Ubuntu user - any tips&tricks?

Thx :)

---

### Post by enriqg9 on 2009-07-16
i have the same problem, i can't find any working drivers for the STIr42xx, and also i can't make it work on my VirualBox Windows XP under Ubuntu Jaunty Jackalope 64-bits.

---

