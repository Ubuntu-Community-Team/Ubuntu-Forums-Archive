---
title: "Can't install driver for RNX-N180UDE Wireless Adapter"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by D3mon_Spawn on 2012-05-31
I seem to be having trouble getting the Linux driver for this particular device installed properly. I downloaded the driver from the munufactor and uncompressed it ([http://www.rosewill.com/products/1721/ProductDetail_Download.htm]("http://www.rosewill.com/products/1721/ProductDetail_Download.htm")). 
I already ran:

```
sudo apt-get install build-essential
```
and 
```
sudo apt-get install linux-headers-`uname -r`
```
when I try and run make I get an error. 
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.0-24-generic/build M=/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.o
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:23:0:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/osdep_service.h: In function ‘_init_timer’:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_ht.h:25:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:67,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h: In function ‘get_da’:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:350:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:350:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:353:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:353:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:356:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:356:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:359:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:359:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h: In function ‘get_sa’:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:374:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:374:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:377:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:377:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:380:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:380:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:383:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:383:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h: In function ‘get_hdr_bssid’:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:397:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:397:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:400:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:400:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:403:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/wifi.h:403:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:70:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_cmd.h: At top level:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:72:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:73:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_recv.h:204:24: error: field ‘recv_tasklet’ has incomplete type
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:73:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_recv.h:434:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_recv.h:434:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/drv_types.h:77:0,
                 from /home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:24:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_io.h: At top level:
/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/john/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [modules] Error 2

```
Not sure if I'm doing something wrong or what. Any insight would be appreciated.

---

