---
title: "Probs with compilling r8168 driver"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by WooRus on 2009-01-20
Hello guys. First sorry for my bad english.
Second i have some probs when i trying compile driver from Network card realtek 8168.

When i try it i all time got message like this 
```

woo@Gameaction1:~/work/r8168-8.009.00$ make clean
make -C src/ clean
make[1]: Entering directory `/home/woo/work/r8168-8.009.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/woo/work/r8168-8.009.00/src'
woo@Gameaction1:~/work/r8168-8.009.00$ make modules
make -C src/ modules
make[1]: Entering directory `/home/woo/work/r8168-8.009.00/src'
make -C /lib/modules/2.6.27-9-server/build SUBDIRS=/home/woo/work/r8168-8.009.00/src modules
make[2]: Entering directory `/lib/modules/2.6.27-9-server/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.27-9-server/build'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/woo/work/r8168-8.009.00/src'
make: *** [modules] Error 2
woo@Gameaction1:~/work/r8168-8.009.00$

```
i already download all what nedded for compilling. Source Headers esentialle etc .... Can some one halp me a bit with this trouble ? 
Perf: Quad core MB:Gigabyte P45-DS3L Ubuntu server 8.10 x64
TY

---

### Post by stonebit on 2009-04-06
I had the same issue. This fixed it for me:
[http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168)

I just downloaded the tar and ran: 
tar xjf r8168_scripts.tar.bz2 && cd r8168_scripts && sudo ./switchmods;
like the page says. It fixed everything.

The page also shows you how to build the driver from the source (which also worked for me). 

Here is the source:
http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP

---

