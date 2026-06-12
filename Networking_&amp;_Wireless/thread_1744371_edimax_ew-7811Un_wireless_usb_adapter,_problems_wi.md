---
title: "edimax ew-7811Un wireless usb adapter, problems with linux drivers and ndiswrapper"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by pooper on 2011-04-30
Hi all

I'm using the latest ubuntu 11.04 (64bit) and as title suggests I've got an EDIMAX EW-7811Un wireless USB adapter, which states on the box it is compatible with Linux, but I can't get it to work!:mad:

It comes with a cd which has the drivers on for linux windows and mac. 

firstly I tried installing it with the linux drivers and all I got was errors thrown at me in terminal.

Then I tried using the ndiswrapper and this worked to an extent such that in the ndiswrapper GUI it recognised the device was plugged in (or not, as I tried just to confirm).. However I could not find the device in ubuntu or any wireless networks. 

I tried the guide on here about ndiswrapper and saw a patch was required for 10.10 however when I tried this on mine all I got from terminal was more errors. 

Any one on here with the solution to installing this adapter on 11.04 please help!!!

---

### Post by MooPi on 2011-04-30
I have the stated device working on my Ubuntu 10.10 machine and know it works. This is a native driver and not using a wrapper.
Make certain you have installed build-essential. From terminal
```
sudo apt-get install build-essential
```
The driver is located here as rtl8192CU:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772")
You will need to extract from the archive and once extracted you will need to extract the driver located inside as well. From the driver folder open a terminal and type:
```
make
sudo make install
sudo modprobe 8192cu
```
You can also add the module to /etc/modules
```
gksudo gedit /etc/modules
```
Add to the end of the file 8192cu
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
8192cu
```
Proof and save and hopefully you have a working wireless
I'm not familiar with how to disable ndiswrapper but think it is a necessary step to use the native driver
I just looked at the downloaded folder from Realtek and there is an included shell sript to install the driver. Maybe an easier alternative could be..... Open a terminal in the extracted archive and type, 
```
sudo sh install.sh
```
Looks to do the entire setup.

---

### Post by pooper on 2011-04-30
hi MooPi 

I tried this and here's what terminal comes out with..

> make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.38-8-generic/build M=/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_cmd.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_security.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_debug.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_io.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_query.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_set.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/ieee80211.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme_ext.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_wlan_util.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_pwrctrl.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_rf.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_recv.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_sta_mgt.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_xmit.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/efuse/rtl8712_efuse.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/led/rtl8192c_led.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/hal_init.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c_d_hal_init.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.o
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.c: In function ‘SetFwRsvdPagePkt’:
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.c:2045:3: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.c: In function ‘set_FwJoinBssReport_cmd’:
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.c:2124:2: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c: In function ‘_rtw_mutex_init’:
/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:305:2: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2


any ideas? thanks

---

### Post by chili555 on 2011-04-30
> home/michael/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:305:2: error: implicit declaration of function ‘init_MUTEX’Please see here: [http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/](http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/)

Please open os_dep/osdep_service.c with a text editor and look around line 305. Find init_MUTEX and change it to sema_init. Use the search function in your text editor to make sure there are no other instances of init_MUTEX; if there are, change them, too. Be very careful about spacing, indentation, spelling, etc. Proofread, save and close.

Then do:```
make clean
make
sudo make install
```Post back any other errors.

---

### Post by pooper on 2011-04-30
ok so I've edited osdep_service.c only found one instance of init_MUTEX which looks like this after editing> #ifdef PLATFORM_LINUX

	init_MUTEX(sema_init);

and here's what terminal says

```
linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size
  CC [M]  /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.o
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:20:0:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:21:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_da&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:21:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c: In function &#8216;dump_xframe&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:1216:20: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:1216:20: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.c:1216:14: warning: cast to pointer from integer of different size
  CC [M]  /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.o
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c:20:0:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c:21:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_da&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c:21:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c: In function &#8216;init_recv_priv&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c:66:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.c:149:15: warning: cast from pointer to integer of different size
  CC [M]  /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.o
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:21:0:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:22:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_da&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:22:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;rtl8192c_createbss_hdl&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:221:27: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;rtl8192c_join_cmd_hdl&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:349:26: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;ConstructBeacon&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1490:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1490:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1490:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1490:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;ConstructPSPoll&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1588:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1588:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;ConstructNullFunctionData&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1642:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1642:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1642:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1642:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c: In function &#8216;ConstructProbeRsp&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1676:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1676:2: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1676:2: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.c:1676:2: warning: cast to pointer from integer of different size
  CC [M]  /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:23:0:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:24:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_da&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size
In file included from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:24:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c: In function &#8216;_rwlock_init&#8217;:
/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:291:2: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2

```

a lot of errors...

---

### Post by pooper on 2011-04-30
this is due to me running 64bit and this code written for 32 bit ?
because it can't handle the size integers???

---

### Post by chili555 on 2011-04-30
> /home/michael/Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:291:2: error: implicit declaration of function ‘init_MUTEX’You got a lot of warnings, but only (so far) one error.

Look at line 291. Are there more changes required?

It may well be a 64-bit issue. Can you locate the Windows **XP** .inf and .sys files for 64-bit so you can try ndiswrapper?

---

### Post by pooper on 2011-04-30
line 291 > init_MUTEX(prwlock);

I tried ndiswrapper with the windows driver. It recognised the device but that's about all it did it didn't seem to integrate with ubuntu I couldn't get any wireless. I read on another post that ubuntu 10.10 ndiswrapper needed patching, but I also tried that and it wouldn't work in terminal.

I might just download 32bit ubuntu and try it all over on that as I've spent days with this. :mad::mad:

---

### Post by chili555 on 2011-04-30
> line 291
Quote:
init_MUTEX(prwlock); Did you try changing it to:```
sema_init(prwlock)
```??

---

### Post by pooper on 2011-04-30
yeah sorry here is the errors from terminal > /home/michael/Desktop/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c: In function ‘_rwlock_init’:
/home/michael/Desktop/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.c:291:2: error: too few arguments to function ‘sema_init’
include/linux/semaphore.h:32:20: note: declared here
make[2]: *** [/home/michael/Desktop/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/michael/Desktop/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2


---

### Post by chili555 on 2011-04-30
I suggest you email the developer; his name and email address is probably in the README. Be sure to tell him your kernel version:```
uname -a
```

---

### Post by pooper on 2011-04-30
Ok thanks for your help. I installed the 32 bit version of ubuntu 11.04 to try that and it still gives me the same error. I shall look for contact details now. for any one else interested  here's results for uname -a > Linux michael 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

---

### Post by chili555 on 2011-04-30
> **pooper said:**
> Ok thanks for your help. I installed the 32 bit version of ubuntu 11.04 to try that and it still gives me the same error. I shall look for contact details now. for any one else interested  here's results for uname -aI think it's the developer that will need to know what kernel version you're running.

---

### Post by MooPi on 2011-04-30
Just tried also on a 32bit natty install with no luck. Same error as pooper. The 8192cu.ko module will not install and 8192cu module mia. Natty is leaving me shaking my head and wondering wondering........

---

### Post by pooper on 2011-05-01
I've contacted realtek as I couldnt find any developer contact details in readme. I actually got the device working last night using 11.04 32bit and ndiswrapper.. I've tried today to get it working with ndiswrapper and 64 bit, but nothing's working.

---

### Post by pooper on 2011-05-01
ok, so I got this working on ubuntu 11.04 32 bit using ndiswrapper and the driver for xp 32 bit from edimax website. Now I have a new problem. When I turn on the computer the device lights up as it should flashing blue (which it didn't before installation) but I get no display... something else isn't loading. On my LG TV I get message (from TV not computer) "Invalid Input"


Any Ideas on this one? 

I see a lot of problems on this wireless issue I think I'm going to return the product and try another, quite possibly a pci.

---

### Post by bobotep on 2011-05-01
Hi,
I had the same compilation problem with the linux drivers(32 bit) and 11.04 and fixed it with the following patches.

diff -r e33a0d4b1d47 rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c
--- a/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c    Sun May 01 16:04:55 2011 -0400
+++ b/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c    Sun May 01 16:11:25 2011 -0400
@@ -302,7 +302,7 @@
 {
 #ifdef PLATFORM_LINUX
 
-    init_MUTEX(pmutex);
+    sema_init(pmutex, 1);
 
 #endif
 #ifdef PLATFORM_OS_XP


After that file compiled, there was an error in usb_intf.c, i commented out the autosuspend_delay variable which is no longer in that structure.  I haven't had time to research if there is a better fix for the usb file, but my wifi is working:)

diff -r e33a0d4b1d47 rtl8192CU_linux_v2.0.1324.20110126/os_dep/linux/usb_intf.c
--- a/rtl8192CU_linux_v2.0.1324.20110126/os_dep/linux/usb_intf.c    Sun May 01 16:04:55 2011 -0400
+++ b/rtl8192CU_linux_v2.0.1324.20110126/os_dep/linux/usb_intf.c    Sun May 01 16:11:25 2011 -0400
@@ -914,7 +914,7 @@
     if( padapter->registrypriv.power_mgnt != PS_MODE_ACTIVE )
     {
         if(padapter->registrypriv.usbss_enable ){     /* autosuspend (2s delay) */
-            pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time     
+            // pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time     
 
             #if (LINUX_VERSION_CODE>=KERNEL_VERSION(2,6,35))
             usb_enable_autosuspend(padapter->dvobjpriv.pusbdev);


Cheers.

---

### Post by MooPi on 2011-05-01
> **pooper said:**
> ok, so I got this working on ubuntu 11.04 32 bit using ndiswrapper and the driver for xp 32 bit from edimax website. Now I have a new problem. When I turn on the computer the device lights up as it should flashing blue (which it didn't before installation) but I get no display... something else isn't loading. On my LG TV I get message (from TV not computer) "Invalid Input"


Any Ideas on this one? 

I see a lot of problems on this wireless issue I think I'm going to return the product and try another, quite possibly a pci.

I think it would probably be a better idea just to roll back to 10.10 as this device is stable and rock solid with 10.10.

---

### Post by pooper on 2011-05-01
ok Moopi I'll try that. I did originally have 10.10 but at the time when trying to install the usb adapter I didn't have a wired connection so no internet connection and nothing would work as I couldn't download additional bits. So got it wired up and saw 11.04 and went with that.
Can you confirm the Edimax I have works with the 64bit version of 10.10 ? if not I'll download the 32bit.

cheers

---

### Post by pooper on 2011-05-02
hey Moopi

I've installed 10.4 l.t.s version and the thing installed fine!! :) (needs an ethernet connection though for internet connection to download the other bits) got the driver from edimax website rather than the one supplied on provided cd. 

One more question though.. A load of automatic updates have appeared for this 10.4, are there any I shouldn't update?

Thanks a lot to everyone who contributed not only have I finally got it to work (with out resorting to windows), but I've also learned a bit too.

---

### Post by jotie on 2011-05-17
Hey pooper,

Did you get this working with Ubuntu 10.10 64-bit or 32-bit?
I can't get this to work with 64-bit.

---

### Post by jotie on 2011-05-17
Nevermind that. I successfully install this on Ubuntu 10.04 64-bit using MooPi method.
Thanks!!

---

### Post by pooper on 2011-05-18
I couldn't get it working on 10.10 64 bit then I tried 11.04 and couldn't get it to work on that either both 32 and 64 bit versions so I just got 10.04 32 bit and worked straight away after installing linux drivers from edimax website. Didnt try 10.04. 64bit as i'd already spent so long trying to get the thing running! Glad to hear it does work though.

---

### Post by chili555 on 2011-05-18
I heard a very reliable rumor that MooPi knows how to get this working on 11.04 32-bit.

Don't ya, MooPi??

---

### Post by pooper on 2011-05-20
To be honest I find 10.04 better anyway, I found 11.04 to be quite glitchy and not sure about the new menu.

---

### Post by MooPi on 2011-06-17
> **chili555 said:**
> I heard a very reliable rumor that MooPi knows how to get this working on 11.04 32-bit.

Don't ya, MooPi??

Yes I have completed the install using the Realtek drivers for RTL8192CU driver.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU")

 Included with the driver is an install script. Navigate to the unzipped driver folder just open a terminal and issue this command ```
sudo sh install.sh
```
To my amazement it worked immediately.

I would like to add that this chip is working with other manufactures as well. I have tested this device from Rosewill and Edimax with same results. Earlier tests were obviously from a flawed driver from Realtek not working on the current kernel.

---

### Post by netslacker on 2011-07-11
> **MooPi said:**
> Yes I have completed the install using the Realtek drivers for RTL8192CU driver.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU")

 Included with the driver is an install script. Navigate to the unzipped driver folder just open a terminal and issue this command ```
sudo sh install.sh
```
To my amazement it worked immediately.

I would like to add that this chip is working with other manufactures as well. I have tested this device from Rosewill and Edimax with same results. Earlier tests were obviously from a flawed driver from Realtek not working on the current kernel.

This worked for me after fidgeting with the driver from edimax for a couple of hours I downloaded the one from RealTek, ran the install script and voila.  If you have the Edimax usb gadget don't bother with their drive on 11.04, just go to RealTek and save yourself the pain.  Works like a champ and was a one command install of the driver.  Thanks for the hints on here!

---

### Post by 808hawk on 2011-08-12
i'm new here. i used the moopi method and it worked.

 i made the mistake of renaming the folder and it didn't work. so dont rename anything.

here is what i did.

download from moopi's link (realtek)
dragged from downloads and dumped it on the desktop.
right click the icon and extract here.

opened a terminal. 

cd Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715

sudo sh install.sh

enter password 
 
bingo, thank you moopi.

---

### Post by pooper on 2011-08-12
yeah I think we've established they've made a fix to the driver.

---

### Post by AllanM on 2011-08-31
Hi. Just used the MooPi method above on 64-bit 11.04 on a Macbook Pro 8.1 (as the built in bcm4331 isn't supported yet) and it worked first time. Nice and fast and cute too with the flashing blue light. :P:P Thx. Allan.

---

### Post by 14opsrc on 2011-10-09
Open rtl8192cu_linux_v2.0.xxxx.2010xxxx/os_dep/osdep_service.c and edit the following line:
(probably line no. 291):

change this line 

init_MUTEX(prwlock)

to

sema_init(prwlock,1)

now compile and insert the module

---

### Post by princ_zuku on 2011-12-11
thx moopi!!! me working too!
it's good idea to check chipset manufacturers page and not that edimax...

---

### Post by csunderland on 2012-01-13
Thanks to the Moopi solution, I have got this working on my son's little netbook - given it a new lease of life since the internal wifi adapter is very flaky.

Thanks again!! :D :D :D

---

### Post by mw1coe on 2012-01-29
I cannot get this to work on my Emac running Lubuntu..

As it's a PowerPC is that a major problem why I cannot get this to compile or install properly..

Rob..

---

### Post by chili555 on 2012-01-29
> **mw1coe said:**
> I cannot get this to work on my Emac running Lubuntu..

As it's a PowerPC is that a major problem why I cannot get this to compile or install properly..

Rob..Please post:```
lsusb
uname -r
```Thanks.

---

### Post by UltimateCat on 2012-01-30
I see that you have the RTL8192

In the past I had the RTL8111/8168B and I learned that I had to blacklist the 8169 and until I did Ndiswrapper wouldn't work even with the inf file.

Trying to be of help-

---

### Post by chili555 on 2012-01-30
> In the past I had the RTL8111/8168B and I learned that I had to blacklist the 8169This is your ethernet device; not wireless. Are you saying that somehow the ethernet must be stopped for wireless to work???

---

### Post by mw1coe on 2012-01-30
lsusb returns :

Bus 004 Device 005: ID 05ac:020b Apple, Inc Pro Keyboard [Mitsumi, A1048/US Layout]
Bus 004 Device 004: ID 04d9:1605 Holtek Semiconductor, Inc
Bus 004 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc.
Bus 004 Device 002: ID 05ac:1003 Apple, Inc Pro Keyboard [Mitsumi, A1048]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub

uname -r  returns

2.6.38-13-powerpc

Incidentally Ndiswrapper won't work as it returns the error : Unable to find a version on ndiswrapper! even though both the Common and Source are installed of Synaptic

---

### Post by chili555 on 2012-01-30
> ID 0bda:8176 Realtek Semiconductor Corp.Your device uses the module *rtl8192cu* which is included by default in Ubuntu 11.10 but must be compiled in older versions like yours. Did you try and fail to compile it? I am not too sure about PPC.

---

### Post by mw1coe on 2012-01-30
Yeah what sucks is that 11.10 screws my PowerPC up somewhat Chronic..

Always totally scraps my PC..

Get all sorts of Issues so sticking to 11.04 which Still Works..

Tried all sorts of attempts of Compiling and Installing Drivers for this but I use 11.10 Lubuntu on a i386 and needs no Drivers but any attempt to put 11.10 on my PowerPC will render my PC as Scrap until they fix it..

Mem..

---

### Post by chili555 on 2012-01-30
> Tried all sorts of attempts of Compiling and Installing Drivers for thisWhat happens? What is the error? Do you have build-essential and linux-headers installed?

---

### Post by mw1coe on 2012-01-31
Yes Linux Headers and Build Essentials are reported to be Installed..

I may have found the Error but not sure how to fix it..

Here's a Paste of my Error Message :

When I run :

sudo bash install.sh

Aftern some lines of data load I get :

Please select card type(1/2):

1) RTL8192cu
2) RTL8192du

I select RTL8192cu 

You have selected RTL8192cu
rtw_version.h has existed!
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=ppc CROSS_COMPILE= -C /lib/modules/2.6.38-13-powerpc/build  M=/home/emac/wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.2012010   3  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-13-powerpc'
Makefile:556: /usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-13-powerpc'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

I have noticed that it seems that this Driver assumes a Directory of */Arch/ppc/*

I do not have that folder. Instead I have */Arch/Powerpc/*

How do I solve the Installation to Install to the Correct Folder ?

Rob..

---

### Post by chili555 on 2012-01-31
> [COLOR="Red"]Makefile:556[/COLOR]: /usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-13-powerpc'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

I have noticed that it seems that this Driver assumes a Directory of */Arch/ppc/*

I do not have that folder. Instead I have */Arch/Powerpc/*

How do I solve the Installation to Install to the Correct Folder ?I'd suggest you try editing the Makefile, perhaps at line 556, to change the file to look in Arch/Powerpc instead of arch/ppc. Try the install again and note any errors.

Be sure of the correct location; Arch is not the same as arch and so forth. Also, I'd keep a note in the folder that you extracted to explain what changes you made and what you changed EXACTLY; something like:> 01-31-2012:
line 556 of Makefile; changed:

<snip>.../arch/ppc/Makefile...<snip>
to:
<snip>.../Arch/Powerpc/Makefile...<snip>There is little worse than getting to step ten and deciding you messed up step three and not having documentation of what step three changed.

By the way; I am skeptical. My linux-headers DO have a folder arch/powerpc. By certain you have Arch and not arch and Powerpc and not powerpc. Like my teacher at Prairie School, spelling and caps and punctuation count!> Instead I have */Arch/Powerpc/*Please be sure.

---

### Post by mw1coe on 2012-01-31
Unfortunately there is no reference to ppc or powerpc in Makefile.

Ahh Well..

Rob..

---

### Post by chili555 on 2012-01-31
Using gedit, search for *arch* around line 556. What is the link to the file you downloaded?

---

### Post by mw1coe on 2012-01-31
I see loads of information with regards to arch but I can see no mention of any reference to the ppc folder..

The Download URL is.. 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

Unless I am seeing things..

LOL..

Rob..

I'm convinced this is a PowerPC issue as my Aspire One i386 runs the same Network Card straight off the bat with no compiling or issues..

---

### Post by chili555 on 2012-02-01
Please try this:```
cd /usr/src/linux-headers-`uname -r`/arch
sudo ln -s powerpc ppc
```Those tick-marks are on the left side of my US keyboard on the same key with ~.

Now cd back to the directory where you extracted the file and try again:```
sudo bash install.sh
```Did it error out?> I'm convinced this is a PowerPC issue as my Aspire One i386 runs the same Network Card straight off the bat with no compiling or issues.. What Ubuntu version is the AAO running? Later versions support your device out of the box.

---

### Post by mw1coe on 2012-02-01
And here lies the Issue...

I Installed Kubuntu 11.10 on the Acer Aspire One and Lubuntu 12.04 on the Emac and it still Won't Run !!

So I think it's definitely an Issue with the PowerPC

During the install I got a ton of the following :

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefile:xxxx: warning : overriding commands for target `x `

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefile:xxxx: warning : ignoring old commands for target ` x `

`xxxx` numbers from 100 to 1520
'x' numerous entries including kernelversion and export-report and /

I am also seeing "permission Denied" flash up just after the messages pop up then replaced by the next line.

Can you help explain whats going on as it's been doing this for over 10 minutes..

Thanks

Rob..

---

### Post by chili555 on 2012-02-02
> During the install I got a ton of the following :

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefilexxx: warning : overriding commands for target `x `

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefilexxx: warning : ignoring old commands for target ` x `

`xxxx` numbers from 100 to 1520
'x' numerous entries including kernelversion and export-report and /That just strongly suggests that the step we took here was wrong:> Please try this:
```
cd /usr/src/linux-headers-`uname -r`/arch
sudo ln -s powerpc ppc
```It appears that the package you downloaded is not going to compile in powerpc. What is it about 11.10 that messes up yout system? Your driver is included in 11.10 by default.

---

### Post by mw1coe on 2012-02-02
Well I finally got 12.04 to work after much searching..

When I first tried it refused to recognize my hard drive..

Well I still got no Wireless but I do have a result in that trying :

lsusb

Now reports Realtek Semiconductor Corp  RTL8188CUS 802.11n WLAN so now it's recognized just  need to get it to access networks..

---

### Post by chili555 on 2012-02-03
> lsusb

Now reports Realtek Semiconductor Corp RTL8188CUS 802.11n WLAN so now it's recognized just need to get it to access networks..What does this tell us?```
dmesg | grep 819
```We are close!

---

### Post by spegru on 2012-02-05
I just got one of these tiny USB wifi adaptors for my new Linux Mint 12 (Ubuntu 11.10 based) laptop. It worked immediately and I didnt have to do anything!

---

### Post by mw1coe on 2012-02-07
dmesg | grep 819[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.558819] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    1.381970] scsi1 : pata_macio
[   31.388199] type=1400 audit(1328668560.375:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=901 comm="apparmor_parser"
[  276.268398] rtl8192cu:_rtl92cu_read_adapter_info():<0-0> RTL819X Not boot from eeprom, check it !!
[  276.268415] rtl8192cu:_rtl92cu_read_adapter_info():<0-0> EEPROM ID(0x0) is invalid!!
[  276.393316] usbcore: registered new interface driver rtl8192cu

---

### Post by chili555 on 2012-02-08
> [ 276.268398] rtl8192cu:_rtl92cu_read_adapter_info():<0-0> RTL819X Not boot from eeprom, check it !!
[ 276.268415] rtl8192cu:_rtl92cu_read_adapter_info():<0-0> EEPROM ID(0x0) is invalid!!Wow.

It is unclear whether it recovers from this issue. Is a wireless interface created?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```If not, any error or warning may be helpful. Do you have the firmware in place?```
md5sum /lib/firmware/rtlwifi/rtl8192cufw.bin
```I am googling the eeprom message but haven't found a solution yet.


---------
Reminder: ID 0bda:8176 Realtek Semiconductor Corp.

---

### Post by skotu on 2012-02-26
> **808hawk said:**
> i'm new here. i used the moopi method and it worked.

 i made the mistake of renaming the folder and it didn't work. so dont rename anything.

here is what i did.

download from moopi's link (realtek)
dragged from downloads and dumped it on the desktop.
right click the icon and extract here.

opened a terminal. 

cd Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715

sudo sh install.sh

enter password 
 
bingo, thank you moopi.

I followed steps above, which worked for me on Ubuntu 10.04

> **pooper said:**
> I couldn't get it working on 10.10 64 bit then I tried 11.04 and couldn't get it to work on that either both 32 and 64 bit versions so I just got 10.04 32 bit and worked straight away after installing linux drivers from edimax website. Didnt try 10.04. 64bit as i'd already spent so long trying to get the thing running! Glad to hear it does work though.

Ubuntu 10.04 32-bit and 64-bit versions both worked for me, except I used the [Realtek drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772") referenced earlier.

Thanks all for the help!

---

### Post by akyazi on 2013-01-12
Hi everyone :)

I've been trying to revive my old powerbook g4 12" and unfortunately i have no airport so decided to use edimax usb wireless.  I installed ubuntu 10.0.4 to powerbook and want to learn completely using debian systems like windows. So i need help please. When i try to install build essential terminal gives the error which i copied below. What should i have to do?

> 
brainticket@brainticket-laptop:~$ sudo apt-get install build-essential
[sudo] password for brainticket: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cpp-4.4 dpkg-dev fakeroot g++ g++-4.4 gcc-4.4 gcc-4.4-base libgcc1 libgomp1
  libstdc++6 libstdc++6-4.4-dev patch xz-utils
Suggested packages:
  gcc-4.4-locales debian-keyring debian-maintainers g++-multilib
  g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg gcc-4.4-multilib
  libmudflap0-4.4-dev libgcc1-dbg libgomp1-dbg libmudflap0-dbg libcloog-ppl0
  libppl-c2 libppl7 libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
  xz-utils
The following packages will be upgraded:
  cpp-4.4 gcc-4.4 gcc-4.4-base libgcc1 libgomp1 libstdc++6
6 upgraded, 8 newly installed, 0 to remove and 502 not upgraded.
Need to get 13,2MB of archives.
After this operation, 25,5MB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main g++ 4:4.4.3-1ubuntu1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main xz-utils 4.999.9beta+20091116-1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main patch 2.6-2ubuntu1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.6
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main build-essential 11.4build1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main fakeroot 1.14.4-1ubuntu1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main gcc-4.4-base 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main libstdc++6 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main libgomp1 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main cpp-4.4 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main gcc-4.4 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main libgcc1 1:4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main libstdc++6-4.4-dev 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security/main g++-4.4 4.4.3-4ubuntu5.1
  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libstdc++6_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libstdc++6_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libgomp1_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libgomp1_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/cpp-4.4_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/cpp-4.4_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libgcc1_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libgcc1_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5.1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/p/patch/patch_2.6-2ubuntu1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/p/patch/patch_2.6-2ubuntu1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.6_all.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.6_all.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/b/build-essential/build-essential_11.4build1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/b/build-essential/build-essential_11.4build1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_powerpc.deb)  Could not resolve 'ports.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
brainticket@brainticket-laptop:~$ 

---

### Post by chili555 on 2013-01-13
> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?I suggest you try just that:```
sudo apt-get update
sudo apt-get install build-essential
```If you get the same error, there is no need to post all the details, just a single example will do like:> Failed to fetch [http://ports.ubuntu.com/ubuntu-ports....1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports....1_powerpc.deb) Could not resolve 'ports.ubuntu.com'I can resolve and get the packages here:> $ wget [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb)
--2013-01-13 17:16:51--  [http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb)
Resolving ports.ubuntu.com (ports.ubuntu.com)... 91.189.92.175
*Connecting to ports.ubuntu.com *(ports.ubuntu.com)|91.189.92.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 118266 (115K) [application/x-debian-package]
Saving to: `gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb'

100%[======================================>] 118,266      220K/s   in 0.5s    

2013-01-13 17:16:52 (220 KB/s) - `gcc-4.4-base_4.4.3-4ubuntu5.1_powerpc.deb' saved [118266/118266]


---

### Post by chinolofus on 2013-01-25
> **MooPi said:**
> Yes I have completed the install using the Realtek drivers for RTL8192CU driver.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

 Included with the driver is an install script. Navigate to the unzipped driver folder just open a terminal and issue this command ```
sudo sh install.sh
```To my amazement it worked immediately.


I would like to add that this chip is working with other manufactures as well. I have tested this device from Rosewill and Edimax with same results. Earlier tests were obviously from a flawed driver from Realtek not working on the current kernel.

i tried this and all i get is   sh: cant open install.sh
i did make the file executable. i really dont know anything about using the terminal. am i supposed to be directing the terminal to the folder somehow? if so how do i do that? oh and im using ubuntu 11.

---

### Post by chili555 on 2013-01-25
Yes, you should be directing the terminal to the location of the files. Where did you extract the package? Your desktop? Then do:```
cd Desktop/RTLwhatever it's named
```Then check for the install.sh file by listing the contents of the directory:```
ls
```Is it there? If so, please proceed.

---

### Post by chinolofus on 2013-01-25
awesome that worked, you're the best! i really appreciate it.

---

### Post by seeingstars63 on 2013-02-26
Hello all,

I am fairly new to Linux/Ubuntu and brand new to this forum. I just bought the edimax EW-7811Un wireless adapter and am having trouble installing the Linux driver. I also tried to download the driver from the edimax website, but realized it contains the same files that I got from the disc. I'm assuming I have to use some of the text files in the command prompt, but am not too familiar with that, yet either. So glad that I found this forum:] Thanks.

---

### Post by chili555 on 2013-02-26
For each of the items in a code block below, enter the text in a terminal (Ctrl+Alt+t) and tell us the result. What version of Ubuntu did you install?```
lsb_release -d
```Which version of 7811 do you have?```
lsusb
```Is there any reaction when you simply insert the device?```
dmesg | grep rtl8
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by kurt18947 on 2013-02-28
> **seeingstars63 said:**
> Hello all,

I am fairly new to Linux/Ubuntu and brand new to this forum. I just bought the edimax EW-7811Un wireless adapter and am having trouble installing the Linux driver. I also tried to download the driver from the edimax website, but realized it contains the same files that I got from the disc. I'm assuming I have to use some of the text files in the command prompt, but am not too familiar with that, yet either. So glad that I found this forum:] Thanks.

The search function hasn't yet returned since the forum upgrade.  I have the EW-7811Un and have been unsuccessful getting it to function using the 'built-in' driver.  It'll recognize the adapter but either connects briefly or not at all.   Chili555 is far more knowledgeable than I about this stuff so maybe he can get the 'built-in' driver to work well.  I've taken the coward's way out:redface:.  I downloaded the driver from RealTek's site,  extracted it to the desktop and ran the script according to the directions included in the tarball.  I've blacklisted the 'built-in' driver (rtl8192cu). Sometimes blacklisting appears necessary, other times not.  The module created by the RealTek script that appears to drive the device is labeled 8192cu, not rtl8192cu.  At least that's how it appears.  It would be wonderful to get out-of-box operation with this device, it's a great choice for portables.  Someone who knows about source code might be able to dissect the download from Realtek, compare the differences with the 'built-in' module and fix it.  I'd bet there isn't much difference, just enough.

Here's the source I've used for the RealTek driver:
[URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false"]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false 


[/URL]

---

### Post by dauntless77 on 2013-06-13
I have Linux Mint 10, would this route that Moopi suggested work for Mint 10. Any other suggestions on wifi issues for mint 10?

---

### Post by kurt18947 on 2013-06-13
> **dauntless77 said:**
> I have Linux Mint 10, would this route that Moopi suggested work for Mint 10. Any other suggestions on wifi issues for mint 10?

I'm not certain which kernel/image Mint 10 uses but I think it's older than Ubuntu 12.04's 3.2.x.  The download from RealTek should work for you, I believe.  The kernels newer than 3.5.x seem to have the problem with the driver from RealTek.  Do bear in mind that if/when there's a kernel upgrade, you'll need to rerun the install script.  One of the useful things the .deb file from Tim Phillips does is incorporate DKMS functions so kernel updates don't break the driver.  I'm not certain if that modded driver would work on an older kernel or not.  Here's the thread if you don't know about it:

[http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934)

---

### Post by dauntless77 on 2013-06-14
Thanks for the feedback. Mint 10 is off a Ubuntu 10.10 code base. Kernel is 2.6.35. I'll check out that the link you provided, much appreciated.

---

### Post by fenderbender1201 on 2013-07-17
hi guys
i tried what was recommended on page 3, what moopi said to do. 

all worked well however, it doesnt seem to save and ill lose everything i did upon shutting down/reboot. Ill have to re-install the driver each time i boot up. 
it is weird cause i did the exact same thing on another computer today and it worked just fine...

was wondering if it could have anything to do with the fact that i have another wireless reciever active, the one that came built into the computer. It is just fairly crappy and goes in and out (on my acer aspire one netbook). 

also obviously wondering if you guys have any advice. 


here is the copy/paste from the terminal. 
sorry if it is hella long, i dont know how to put it into a scroll-able text box. 


> 
derp@BOB:~$ cd /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105derp@BOB:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo sh install.sh
[sudo] password for derp: 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
Authentication requested [root] for make clean:
install.sh: 38: [: unexpected operator
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
install.sh: 48: [: unexpected operator
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-23-generic/build M=/home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.o
  LD [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.mod.o
  LD [M]  /home/derp/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
##################################################
Compile make driver ok!!
##################################################
install.sh: 68: [: unexpected operator
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.5.0-23-generic
##################################################
The Setup Script is completed !
##################################################
derp@BOB:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 



---

### Post by chili555 on 2013-07-17
> was wondering if it could have anything to do with the fact that i have another wireless reciever active, the one that came built into the computer. It is just fairly crappy and goes in and out (on my acer aspire one netbook). Very possibly. I suggest we blacklist its driver so it doesn't activate at all and see if doesn't fix the problem. If not, we'll probe a bit deeper. So we know what your driver is, please post:```
lsmod
```I doubt you need to rebuild the driver each time. Instead, try:```
sudo modprobe 8192cu
```

---

