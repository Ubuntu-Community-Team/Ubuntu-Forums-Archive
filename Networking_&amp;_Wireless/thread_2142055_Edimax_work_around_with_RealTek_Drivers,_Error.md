---
title: "Edimax work around with RealTek Drivers, Error"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by SteelCtyVitt on 2013-05-04
Hey all, I will start by saying new to Linux however I have done quite a few hours worth of research on my own and have found that the Edimax 11n can be used with Ubuntu if you perform a work around installing RealTek drivers... thus far I have followed the directions found and have run into a few errors.  I am on Ubuntu 13.04, I downloaded the drivers from RealTeks website, unzipped, moved to location and have sudo sh install.sh... the output is as follows...

```
vitt@vitt-System-Product-Name:~/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo sh install.sh
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function ‘thread_enter’:
/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
In file included from /home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:24:
/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/vitt/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```

I have also updated, reinstalled, and installed the build-drivers as well as quite a few other tools, completely lost... any help would be greatly thankful for

---

