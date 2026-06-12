---
title: "Errors when attempting to install RTL8712 driver for Edimax EW-7811Un wireless usb"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by slatts04 on 2012-12-05
Recently installed Ubuntu 12.04 on an old Dell Inspiron 1420. The build in wireless card is flaky, so I purchased an Edimax EW-7811Un "nano" USB adapter. I downloaded the driver for it from the Realtek website, unzipped the folder, unzipped the driver folder, and attempted to install it using the sudo bash install.sh command in the terminal. However, after some installation stuff occurs, I get the error:


---------------------


Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-34-generic-pae/build M=/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
  CC [M]  /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0,
                 from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type
In file included from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0,
                 from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type
make[2]: *** [/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/stephen/Desktop/starter/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


-------------

Any help with this would be appreciated. I am brand new to Ubuntu so go easy on the slang/skipping of "assumed" steps.

---

