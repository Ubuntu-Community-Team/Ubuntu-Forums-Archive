---
title: "How to install driver for Broadcom Wireless Adapter"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by maryp on 2011-11-29
I have installed the Ubuntu 11.10 on my Dell Inspiron E1505.  There is no driver for my wireless adapter provided by Ubuntu, so I downloaded a driver from Broadcom: 802.11 Linux STA Driver.  When I run make, I get the following:
 
[SIZE=3][FONT=Calibri]sudo make[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wireless Extension is the only possible API for this kernel version Using Wireless Extension API[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  LD      /lib/modules/3.0.0-12-generic/hybrid_wl/built-in.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  CC [M]  /lib/modules/3.0.0-12-generic/hybrid_wl/src/shared/linux_osl.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  CC [M]  /lib/modules/3.0.0-12-generic/hybrid_wl/src/wl/sys/wl_linux.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  CC [M]  /lib/modules/3.0.0-12-generic/hybrid_wl/src/wl/sys/wl_iw.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  CC [M]  /lib/modules/3.0.0-12-generic/hybrid_wl/src/wl/sys/wl_cfg80211.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]  LD [M]  /lib/modules/3.0.0-12-generic/hybrid_wl/wl.o[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]ld: Relocatable linking with relocations from format elf32-i386 (/lib/modules/3.0.0-12-generic/hybrid_wl/lib/wlc_hybrid.o_shipped) to format elf64-x86-64 (/lib/modules/3.0.0-12-generic/hybrid_wl/wl.o) is not supported[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make[2]: *** [/lib/modules/3.0.0-12-generic/hybrid_wl/wl.o] Error 1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make[1]: *** [_module_/lib/modules/3.0.0-12-generic/hybrid_wl] Error 2[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make: *** [all] Error 2[/FONT][/SIZE]
 
What am I doing wrong?

---

### Post by jonobr on 2011-11-29
I believe I saw this in other posts about Broadcom

I think you need to tell make your using 64 bit 

```
make TARGET=x86_64-elf
```

Ill do some digging , see if I can find it

---

### Post by maryp on 2011-11-29
I downloaded the 32 bit version because that is what the PC is.  Not sure why it thinks it is a 64 bit.

---

### Post by madvinegar on 2011-11-30
Put your PC/laptop on ethernet to get internet and go to synaptic package manager and mark for installation the drivers "b43-fwcutter" and "firmware-b43-installer".

That's it.

PS: Do NOT activate "Broadcom STA wireless driver" from "additional drivers". If you have done so, de-activate it.

---

