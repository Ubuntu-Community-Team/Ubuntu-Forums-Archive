---
title: "Realtek RTL8192CU Driver issues under 13.04"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by intrloper on 2013-05-24
Ok I am not sure what I am missing but I can not get this damn thing to work.

I have so far blacklisted the default driver and downloaded the newest: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
driver

I tried to compile it using sudo bash ./install.sh

and it returns an error message:

```
annie@annie-PC:~/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo bash ./install.sh[sudo] password for annie: 
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-21-generic/build M=/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-21-generic'
  CC [M]  /home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function ‘thread_enter’:
/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
In file included from /home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:24:
/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/annie/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-21-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```

I have been reading all night trying to fix this. 
I tried to install sudo apt-get install linux-headers-2.6.32-21-generic as per on post but it couldnt find the install. So I thought I needed to install the headers for the version I have. When I try that it says they are already installed and upto date,
So then I installed sudo apt-get install build-essential which it seems to have installed that. 
Ran the install.sh again but same error. 

Next I tried to download a 8192cu.ko and tried to load the driver directly, seems that didnt work either.
Lastly I tried to install firmware-realtek_0.38_all.deb but it gave me an error also. 

At this point I am pretty annoyed. I am new to Linux and trying very hard not to give up. 

I am running Ubuntu 13.04 64Bit 

Any help would be amazing because like I said I would like to make Linux my home but as it stands now it doesnt look too good.
Please help.
Thank you.

EDIT: Wanted to mention the reason I am not using the default driver is because the wireless will work for just a few minutes then it stops. It doesnt show that I dropped off my network but I just time out on ever page, even 192.168.1.1.I Also tested using phone as Wifi Hotspot and also works at first but then starts to time out. I did notice on the "Attached Devices" page on router internals that once the connection starts to time out my wireless stops showing up. However on the linux side it still says I should be connected to my network. Not sure if that info helps but I really hope someone can assist me. Thanks again.

---

### Post by agillator on 2013-05-24
This is a common problem that I also cannot find a successful solution for. Someone has suggested it actually has to do with Linux support for draft-N wireless, but I don't know. At any rate I would suggest you google for 'ubuntu rtl8192C' or some such. Read carefully because some of the suggestions have unwanted side affects, for example losing sound. I tried several things to no avail - yet. I'm sure it will be solved in the not too distant future, but that doesn't help us now. My eventual solution was to use a different piece of hardware that used a different chipset. I had a Belkin F5D7050 which is only G, but that is good enough for the moment and I believe is fairly inexpensive. Luckily this doesn't happen too often. Most hardware is well supported in Linux. If youdo find something that works, PLEASE post it on here so others can use it. There have been many similar threads.

---

### Post by intrloper on 2013-05-24
I actually have googled several different search strings trying to find help. I have also tried to get it to work on Linux Mint 14 but on Mint it loops the WPA2 authorization. It seems that it is an ongoing issue for years now. If no official fix yet then I don't see one coming soon. So I guess one thing is why wont this compile? Is there a work around so it will? Compiling is new to me so not sure what else I could do. Is it the 3.8 Kernel? Thank you again.

---

### Post by agillator on 2013-05-24
I couldn't get it t compile either, reason unknown. It could be that it is written for a different kernel than we are each using so the headers are different, or the kerel headers are not installed (mine are, are yours?). I believe the driver may be written for a 2.x kernel, I'm not sure and haven't had time to follow up or contact RealTek. However, if that is the case perhaps they need to update it. Have you tried contacting them directly?

---

### Post by intrloper on 2013-05-24
The RealTek site mentions Kernel 2.6 and 3.0~ 
I am still new to linux so I am not sure if running 3.8.0.21 makes it incompatible.

I have not tried to contact RealTek, I dont see them writing updated drivers per one persons email.

It does seem though, least according to the dates of a lot of the posts it has been an issue for least a few years.

---

### Post by I_ated_it on 2013-05-24
I had the same problem trying to compile the driver but I used the fix posted here:

[http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934)

pretty simple, the only problem is my speeds are awfully slow.

Hope this helps.

---

### Post by MIJ-VI on 2013-09-30
The rtl8192cu-based StarTech USB150WN1X1 (which hasn't worked for me since Ubuntu 12.04.1 / Linux 3.2.x) has been working fine for nearly 3 hours under ubuntu-13.10-beta2-desktop-amd64 in conjunction with a Belkin F5D6230-3 (802.11b) WiFi router (I'm a cheapskate :P):

USB Wireless Network Adapter - USB to Wireless N Adapter | 802.11N | StarTech.com
[http://www.startech.com/Networking-IO/Wireless/USB-150Mbps-Mini-Wireless-N-Network-Adapter-802-11n-g-1T1R~USB150WN1X1](http://www.startech.com/Networking-IO/Wireless/USB-150Mbps-Mini-Wireless-N-Network-Adapter-802-11n-g-1T1R~USB150WN1X1)

Belkin F5D6230-3, specs at DuckDuckGo
[https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs](https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs)

```
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:9e:95:9c:54:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.11.0-9-generic firmware=N/A ip=192.168.2.31 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by tjeremiah on 2013-10-17
> **MIJ-VI said:**
> The rtl8192cu-based StarTech USB150WN1X1 (which hasn't worked for me since Ubuntu 12.04.1 / Linux 3.2.x) has been working fine for nearly 3 hours under ubuntu-13.10-beta2-desktop-amd64 in conjunction with a Belkin F5D6230-3 (802.11b) WiFi router (I'm a cheapskate :P):

USB Wireless Network Adapter - USB to Wireless N Adapter | 802.11N | StarTech.com
[http://www.startech.com/Networking-IO/Wireless/USB-150Mbps-Mini-Wireless-N-Network-Adapter-802-11n-g-1T1R~USB150WN1X1](http://www.startech.com/Networking-IO/Wireless/USB-150Mbps-Mini-Wireless-N-Network-Adapter-802-11n-g-1T1R~USB150WN1X1)

Belkin F5D6230-3, specs at DuckDuckGo
[https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs](https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs)

```
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:9e:95:9c:54:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.11.0-9-generic firmware=N/A ip=192.168.2.31 link=yes multicast=yes wireless=IEEE 802.11bgn
```
how'd you get it to work?

---

### Post by MIJ-VI on 2013-10-17
I just plugged it in, tried to connect to my WiFi router, and it worked.

---

### Post by kurt18947 on 2013-10-17
> **MIJ-VI said:**
> I just plugged it in, tried to connect to my WiFi router, and it worked.

I've had the same experience with this device:

> ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

I did notice one interesting trait though.  I have two routers, the second configured as an access point.  I tried the RTL8192CU on two different machines, a home-built AMD desktop & R61 thinkpad.  The desktop seemed to work fine, the thinkpad was an absolute pain.  It'd connect then lose internet access.  Ping would return "host not found" but the machine was connected to the router.  Drove me up the wall.  I finally changed the second router from access point/repeater mode to router mode.  Now the RTL8192CU device seems quite reliable.  Why did it work reliably on the desktop in access point mode but not on the Thinkpad?  I have no clue but that's how it appears, could have something to do with the 2nd router.  This is using the driver included with 13.10.  

I could not get the driver from Realtek to work on any release since 12.10.  I had luck with this driver in 13.04.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

This was with a 8188CUs device but I think the driver is the same for 8192CU & 8188CUs.  This above driver does not work with 13.10.

---

### Post by balinares2 on 2013-10-24
> **kurt18947 said:**
> This was with a 8188CUs device but I think the driver is the same for 8192CU & 8188CUs.  This above driver does not work with 13.10.

I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

---

### Post by van hanegen on 2013-10-27
Nice job, balinares2!
It works fine with my 13.10 clean install. (The built-in driver lost connection after a few minutes).
Thank you very very much!!

---

### Post by kurt18947 on 2013-10-29
> **van hanegen said:**
> Nice job, balinares2!
It works fine with my 13.10 clean install. (The built-in driver lost connection after a few minutes).
Thank you very very much!!

Edit:  To make clear, this is using the 'baked-in' driver, not balinares2's work.

Here is a trick I've discovered for the stalled/lost connection state.  I find the connection to the router intact, it appears to be some sort of problem with resolving internet - somethings.  I click on the network icon in the upper right corner (I'm using gnome-shell) and click the wifi off button.  Wait a second or two then click the wifi on and the internet connection is restored.  I've look at dmesg output after these occurrences and it's usually similar to this:

```
wlan3: deauthenticating from 00:xx:xx:xx:xx:xx by local choice (reason=3)
[51263.577909] cfg80211: Calling CRDA to update world regulatory domain
[51263.582492] cfg80211: World regulatory domain updated:
[51263.582497] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[51263.582499] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51263.582501] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51263.582503] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[51263.582504] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51263.582505] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51268.637024] rtl8192cu: MAC auto ON okay!
[51268.673284] rtl8192cu: Tx queue select: 0x05
[51269.059751] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[51270.619284] wlan3: authenticate with 00:xx:xx:xx:xx:xx
[51270.635712] wlan3: send auth to 00:xx:xx:xx:xx:xx (try 1/3)
[51270.678766] wlan3: authenticated
[51270.682499] wlan3: associate with 00:xx:xx:xx:xx:xx (try 1/3)
[51270.689801] wlan3: RX AssocResp from 00:xx:xx:xx:xx:xx (capab=0x431 status=0 aid=1)
[51270.689910] wlan3: associated
[51270.690003] IPv6: ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready


```

This is with only 1 wifi access point so there could be something peculiar there, I'm not sure.  Plus I'm sure the 'baked-in' driver is -- 'imperfect'. I haven't tried one of these adapters on a public wifi system to see if they behave differently.

---

### Post by ankhmorporkian on 2013-10-30
> **balinares2 said:**
> I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

Worked beautifully for me. Thanks a bunch!

---

### Post by kurt18947 on 2013-10-30
> **balinares2 said:**
> I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

Perfect!!  Thank you so much. 150 mb/sec. and full strength signal - the best the 'baked-in' driver would do was 72 mb./sec.  We're lucky to have people like balinares2 & Tim Patterson with the skills and willingness to do this.  I'm still curious why the 'baked-in' version worked reasonably well on a home built AMD desktop running Ubuntu13.10 w/ gnome-shell but poorly/not-at-all on an R61 Thinkpad running Ubuntu-Gnome.

Edit:  When I tried the same procedure on the AMD desktop, I didn't have quite as good luck.  When I did the install on the Thinkpad, I prematurely removed the 8192CUs adapter.  I replaced it with an 8192**SU** adapter, copy/pasted the lines of code and all was well.  When I tried the desktop, I didn't remove the 8192CU based adapter, but copy/pasted with the adapter in place.  When I rebooted, I was still using the 'baked-in' driver even though the blacklist lines were in place and seemed correct.  I manually removed the 'baked-in' modules then manually loaded the 8192CU module.  It works MUCH better than the **rtl**8102cu module, signal strength is much greater, wavemon shows 300 mb./sec vs. 72 mb./sec with the 'baked-in' module.  I have no idea why the rtl8192cu module loaded when it was blacklisted, but it did.

Edit II:  Here's the fix to the above problem.  I left the original in case someone has a similar problem.   For some unknown reason, the 'baked-in' module rtl8192cu was listed in the "etc/modules" file.  Being listed there over-rides being blacklisted so it was loading instead of the desired '8192cu'.

---

### Post by NM5TF on 2013-11-08
> **balinares2 said:**
> I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

thanks for the link....that fixed my install of Ubu 14.04 wifi problem for kernel 3.11....:guitar:

but the upgrade to the 3.12 kernel is broken again....is there a similar fix for 3.12 ?? [-o<

Tommy

UPDATE: 11/09/13.....reran the 8192cu fixes, followed the instructions & now wifi is working 
correctly under krenel 3.12.0-1:P

---

### Post by tjeremiah on 2013-12-01
> **balinares2 said:**
> I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

is there anyway to make this into a deb. file? I cant get internet connection to get this to work. I tried an app for android (my phone) called easytether but it doesnt allow connection to github.

---

### Post by tomasio2 on 2014-02-15
Excellent, thanks for this. 

I do notice that on my fresh Ubuntu 13.10 / 3.11 kernel system, if I don't have any network activity for a little while (a minute or two) sometimes the network stops working. I need to disconnect/reconnect to the wifi and then it works again. Perhaps something to do with power-saving? Not sure.

Also, when I restart my system, the kernel module isn't loaded. Doing an "lsmod | grep 8192cu" doesn't show anything. I have to manually load the kernel module with "sudo modprobe rtl8192cu" then it appears, and the network is working. Automating this at startup, I placed the text "rtl8192cu" at the end of the /etc/modules file to load at boot time. Seems to be working well otherwise.

---

### Post by van hanegen on 2014-02-16
> **tomasio2 said:**
>  
I do notice that on my fresh Ubuntu 13.10 / 3.11 kernel system, if I don't have any network activity for a little while (a minute or two) sometimes the network stops working. I need to disconnect/reconnect to the wifi and then it works again. Perhaps something to do with power-saving? Not sure.
  
I have absolutely the same case with my 14.04 (TP-LINK TL-WL725,ver.1). Also think, may be this is all about power supplying, as the probability of disconnection is somehow linked with the value of mains voltage - the higher the voltage, the more stable work.

P.S. And here it seems ok with the kernel module after restarting:
```
andrey@andrey-G31M-S2L:~$ lsmod | grep 8192cu
rtl8192cu              66675  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                52835  2 rtl_usb,rtl8192cu
rtl8192c_common        47340  1 rtl8192cu
mac80211              546069  3 rtl_usb,rtlwifi,rtl8192cu
andrey@andrey-G31M-S2L:~$ 
```

---

### Post by ph752 on 2014-03-07
I have Xubuntu 13.10 saucy

> $ sudo dkms add ./rtl8192cu-fixes 
[sudo] password for philippe: 
Error! Could not find module source directory.
Directory: /usr/src/.-rtl8192cu-fixes does not exist.

---

### Post by ph752 on 2014-03-07
> $ git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Cloning into 'rtl8192cu-fixes'...
fatal: unable to access 'https://github.com/pvaret/rtl8192cu-fixes.git/': Could not resolve host: github.com

 i have not internet!
 my TP-LINK TL-WN725N  is for that!

---

### Post by kurt18947 on 2014-03-09
> **balinares2 said:**
> I've tried to port that driver to kernel 3.11 for Ubuntu 13.10: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

It works for me. Please let me know if it works for you.

(Sweetmuffins, the new Ubuntu login stuff is godawful.)

I thought I'd update this thread.  I have 14.04 gnome installed on two machines.  I decided that i hadn't broken anything in some time and was overdue:p.  I decided to see if balinares2 fix would build on 14.04 with its 3.13.0-16-generic kernel.  I followed the steps as documented and everything worked as advertized.  Both RTL8192CU & RTL8188CUs adapters flash happily away.  I'm not certain the speed is as good as it is with the 3.11 kernel but it seems stable, link quality & signal levels are maxed in wavemon.

---

### Post by kurt18947 on 2014-03-10
> **ph752 said:**
> i have not internet!
 my TP-LINK TL-WN725N  is for that!

Do you have "git" installed?  Yes, you do need an internet connection for this to work.  Either a wired connection or another working wireless network adapter.

---

### Post by xmbwd on 2014-10-27
I hope folks are still watching this thread.  I had previously used the fix here to get my [Edimax EW-7811Un]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CDMQFjAB&url=http%3A%2F%2Fwww.edimax.com%2Fen%2Fproduce_detail.php%3Fpd_id%3D347&ei=M4JOVMXsDMKQigKh-4DYAg&usg=AFQjCNGqB_PSjXcUeOzbAlTraQA2Y3JNbg&bvm=bv.77880786,d.cGE") wireless adapter working.  

But I updated to 14.10 from 14.04 last night.  And now it stopped working.  

My kernel is now 3.16.0-23-generic x86_64.  It worked on 3.13.0-32-genericx86_64.  

Is there any way to get this up and working again?

Thanks!

---

### Post by MIJ-VI on 2014-10-27
[I]"WI1 chip1: Realtek RTL8188CUS

Probable Linux driver
rtl8192cu (in backports) or Realtek's vendor driver"[/I]

Edimax EW-7811Un - WikiDevi
[https://wikidevi.com/wiki/Edimax_EW-7811Un](https://wikidevi.com/wiki/Edimax_EW-7811Un)

---

### Post by xmbwd on 2014-10-27
I can't tell if this if for my question, but I don't understand what you are trying to relate.  Please elaborate?  

> **MIJ-VI said:**
> [I]"WI1 chip1: Realtek RTL8188CUS

Probable Linux driver
rtl8192cu (in backports) or Realtek's vendor driver"[/I]

Edimax EW-7811Un - WikiDevi
[https://wikidevi.com/wiki/Edimax_EW-7811Un](https://wikidevi.com/wiki/Edimax_EW-7811Un)

---

### Post by MIJ-VI on 2014-10-28
My aim was to identify the chipset used (**Realtek** RTL8188CUS) for the benefit of others who may have more experience dealing with it and thus who are in a better position to help you than I am (I switched to Ralink-based WiFi adaptors a while back after the Realtek-based WiFi adaptor I used to own stopped working with Linux Mint 15 & 16).

This isn't the first time a usually supported Realtek-based WiFi adaptor has stopped working on a newer version of Ubuntu (it last happened with Ubuntu 12.10 and 13.04 IIRC).

IME a clean OS install is prefereable to an OS upgrade. Have you tried booting from the Ubuntu 14.10 Live DVD?

Ubuntu 14.10 (Utopic Unicorn)
[http://de.releases.ubuntu.com/utopic/](http://de.releases.ubuntu.com/utopic/)

---

### Post by kurt18947 on 2014-10-30
> **xmbwd said:**
> I hope folks are still watching this thread.  I had previously used the fix here to get my [Edimax EW-7811Un]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CDMQFjAB&url=http%3A%2F%2Fwww.edimax.com%2Fen%2Fproduce_detail.php%3Fpd_id%3D347&ei=M4JOVMXsDMKQigKh-4DYAg&usg=AFQjCNGqB_PSjXcUeOzbAlTraQA2Y3JNbg&bvm=bv.77880786,d.cGE") wireless adapter working.  

But I updated to 14.10 from 14.04 last night.  And now it stopped working.  

My kernel is now 3.16.0-23-generic x86_64.  It worked on 3.13.0-32-genericx86_64.  

Is there any way to get this up and working again?

Thanks!

This sure looks like a YMMV thing.  I just installed 14.10 last night (clean install) and plugged in a generic RTL8192CU adapter.  It was found and works. I've been using this for a few hours.  This adapter - RTL8192CU - has worked with previous versions but would always stall after a few minutes to an hour.  Powering off/on or unplug/replug would restore connectivity for a period of time.  Using pvaret's github solution yields normal function. Same with the Edimax adapter. 

Both adapters RTL8192CU & RTL8192CUs seem to function without the github fix.  I haven't had the RTL8192CU stall after using it for a couple hours.  I just plugged the Edimax in after powering down the RTL8192CU and so far so good. It works and connects. Speeds, on the other hand - I'm on a 25/15 broadband connection. That's what I see when connected via an ethernet cable.  Connecting via the Edimax 7811Un adapter using the 'baked in' driver in 14.10? About 4 mb. up, 2 mb. down.  Not so good.  Neither iwconfig nor ifconfig show anything out of the ordinary to my inexpert eye.  Wavemon is sort of interesting - it doesn't really show anything, no essid and no interface data.  I'm pretty sure it's not my wireless connection because the speed tests work correctly when using 14.04 with pvaret's fix.  Executive summary - two Realtek devices work with 14.10 and seem to stay connected for me but the speed is pretty bad compared to the patched Realtek driver. It does look that perhaps the stalling is fixed though it's too early to have too much confidence in that.

Edit:  I've spent more time using 14.10 and the 'baked-in' Realtek driver. I tried downloading an .iso from a known-fast mirror.  The speed averaged around 700KB./sec.  That's not horrible but not not close to the 3 MB./sec. this mirror usually provides. The good news is that the connection seems reliable, it hasn't stalled once.  That's progress.

---

### Post by marusic-sasha on 2015-02-03
When you say you "manually removed the baked-in modules" you are talking about opening the casing and switching the module?

I've tried running the commands but it seems the fix is only temporarily. I have rtl8192ce drivers and even when I use the blacklist cmd the driver is still active.

---

### Post by kurt18947 on 2015-02-04
> **marusic-sasha said:**
> When you say you "manually removed the baked-in modules" you are talking about opening the casing and switching the module?

I've tried running the commands but it seems the fix is only temporarily. I have rtl8192ce drivers and even when I use the blacklist cmd the driver is still active.

Using a command like "sudo modprobe -r <module_name>" should temporarily remove the specified module. A reboot will reload the module. To temporarily load a module, "sudo modprobe <module_name>  should work as well.  To make permanent loading or unloading modules on startup, there are several posts/threads on how to do that. Remember once you make permanent changes or wish to undo temporary changes you must reboot.

---

