---
title: "Noob can't get USB wireless going"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by AliMcFerrin on 2010-12-09
Hi

I've been trying to get my GetNet 300 GN-621U USB wireless device working for a while now. When I first booted into my clean meerkat 64-bit install, both my wired and wireless were visible in network connections but neither could connect. I have since figured out what was wrong with the internal NIC and am happy to say i'm connected to the net, but need wireless to work.

Having blacklisted the generic wireless driver, i see nothing anywhere that the device is on the system

My initial attempt led me down the route of installing **ndisgtk** for running the windows driver. I've since removed the driver/device from Windows Wireless Devices and have been trying to install the bona fide linux driver from getnet.

First some diagnostics:

root@alastair-ubuntu:~# /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


here it is listed in usb devices:

lsusb
Bus 002 Device 007: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys
Bus 002 Device 006: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 002 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
...

When trying to make the driver:

root@alastair-ubuntu:~/Drivers/LinuxDriver# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.o
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_initiate’:
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:1603: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast
include/linux/usb.h:1261: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_isr’:
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:2060: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast
include/linux/usb.h:1261: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:2067: warning: assignment makes pointer from integer without a cast
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12320: error: ‘struct net_device’ has no member named ‘open’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12321: error: ‘struct net_device’ has no member named ‘stop’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12322: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12323: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12324: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12325: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12326: error: ‘struct net_device’ has no member named ‘get_stats’
/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.c:12327: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/alastair/Drivers/LinuxDriver/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

(I've attached the driver readme)

Cheers for some help.

---

### Post by AliMcFerrin on 2010-12-09
So, the general consensus around the web is that the linux package for the GetNet GN-621U USB wireless adapter (Realtek RLT8172SU) doesnt work, it didnt for me. You get a load of errors when making.

For me, the Ndiswrapper (Windows Wireless) package wasnt working in meerkat 64-bit running the XP-32 or Win7-64 version of the driver.

I have since reinstalled to lynx 32-bit. Again the linux install of the driver failed.

this time the ndiswrapper worked for the XP-32 bit version (after rebooting).

---

