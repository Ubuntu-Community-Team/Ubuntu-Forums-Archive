---
title: "AWUS036NHR is not working"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by vianneydaianee on 2012-04-13
Hey I would like to know how to install my AWUS036NHR i've been trying to make it work but I can't .. I would really appreciate if someone could help me please. I tried to install the drivers and the an error appears at the end.

vianneydaianee@vianney-natty:~$ cd ~/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715
vianneydaianee@vianney-natty:~/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715$ sudo ./install.sh
[sudo] password for vianneydaianee: 
        Auto install for 8192cu
        September, 1 2010 v 1.0.0
rtl8192_8188CU_linux_v3.0.2164.20110715/
rtl8192_8188CU_linux_v3.0.2164.20110715/autoconf_rtl8192c_usb_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/clean
rtl8192_8188CU_linux_v3.0.2164.20110715/core/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/rtw_efuse.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_debug.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_eeprom.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ieee80211.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_io.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_query.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_rtl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_set.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme_ext.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp_ioctl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_p2p.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_pwrctrl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_rf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_security.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_sta_mgt.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_wlan_util.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_dm.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_sreset.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0
rtl8192_8188CU_linux_v3.0.2164.20110715/include/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig
rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c
rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa
rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp
rtl8192_8188CU_linux_v3.0.2164.20110715
Authentication requested [root] for make driver:
make  ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.0.0-17-generic-pae/build  M=/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715   modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.0.0-17-generic-pae»
   CC [M]   /home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In  file included from  /home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29:  error fatal: linux/smp_lock.h: No existe el archivo o el directorio
compilación terminada.
make[2]:  ***  [/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o]  Error 1
make[1]: ***  [_module_/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715]  Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.0.0-17-generic-pae»
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg

---

### Post by vianneydaianee on 2012-04-13
Hey I would like to know how to install my AWUS036NHR i've been trying  to make it work but I can't .. I would really appreciate if someone  could help me please. I tried to install the drivers and the an error  appears at the end.
```

vianneydaianee@vianney-natty:~$ cd ~/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715
vianneydaianee@vianney-natty:~/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715$ sudo ./install.sh
[sudo] password for vianneydaianee: 
        Auto install for 8192cu
        September, 1 2010 v 1.0.0
rtl8192_8188CU_linux_v3.0.2164.20110715/
rtl8192_8188CU_linux_v3.0.2164.20110715/autoconf_rtl8192c_usb_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/clean
rtl8192_8188CU_linux_v3.0.2164.20110715/core/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/rtw_efuse.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_debug.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_eeprom.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ieee80211.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_io.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_query.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_rtl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_set.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme_ext.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp_ioctl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_p2p.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_pwrctrl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_rf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_security.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_sta_mgt.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_wlan_util.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_dm.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_sreset.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0
rtl8192_8188CU_linux_v3.0.2164.20110715/include/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig
rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c
rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa
rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp
rtl8192_8188CU_linux_v3.0.2164.20110715
Authentication requested [root] for make driver:
make  ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.0.0-17-generic-pae/build  M=/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715    modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.0.0-17-generic-pae»
   CC [M]   /home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In  file included from  /home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29:   error fatal: linux/smp_lock.h: No existe el archivo o el directorio
compilación terminada.
make[2]:  ***  [/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o]   Error 1
make[1]: ***  [_module_/home/vianneydaianee/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715]   Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.0.0-17-generic-pae»
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg
```

---

### Post by chili555 on 2012-04-13
On my system, smp_lock.h is not installed in kernels after 3.0.0-12; you are running 3.0.0-17. On the other hand rtl8192cu is installed by default, requiring no compiling. Why isn't the default rtl8192cu working for you? Please post:```
lsmod | grep 819
dmesg | grep 819
```

---

### Post by mörgæs on 2012-04-13
Please post a question only once and remember to use CODE tags.

---

