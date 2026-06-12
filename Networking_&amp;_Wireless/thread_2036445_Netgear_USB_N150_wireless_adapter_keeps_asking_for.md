---
title: "Netgear USB N150 wireless adapter keeps asking for password ubuntu 12.04"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by katsumodo on 2012-08-01
I've seen several other forum posts on this site as well as others about similar problems but have yet to find a solution.  I'm new to ubuntu so I apologize in advance for my n00bery. I have a Netgear N150 Wireless USB Micro Adapter (WNA1000M). I've tried so many different ways to get this stupid thing working and I worry that with so many different attempts I may have a problem. I heard once that using ndiswrapper was a possible solution, but also ready that you should avoid using it if possible. So i attempted to remove ndiswrapper and I'm pretty sure I did it wrong. 

Here is my latest attempt:
jon@jon-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse

So from running lsusb we can see that I should install the rtl8188cus driver right? So I downloaded the driver from Realtek, unzipped it and ran the following:

jon@jon-desktop:~$ **sudo apt-get install linux-headers-generic build-essential**
[sudo] password for jon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jon@jon-desktop:~$ **cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/**
jon@jon-desktop:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ **sudo sh install.sh**
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622.tar.gz
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Makefile
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Kconfig
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/clean
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622
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
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-27-generic-pae/build M=/home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-27-generic-pae'
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_cmd.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_security.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_debug.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_io.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_query.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_set.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ieee80211.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme_ext.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_wlan_util.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_pwrctrl.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_rf.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_recv.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_sta_mgt.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_xmit.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_p2p.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_br_ext.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_iol.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/rtw_efuse.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/hal_init.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/osdep_service.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/os_intfs.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/usb_intf.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_linux.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/xmit_linux.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/mlme_linux.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/recv_linux.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/rtw_android.o
  LD [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/8192cu.mod.o
  LD [M]  /home/jon/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-27-generic-pae'
##################################################
Compile make driver ok!!
##################################################
install.sh: 68: [: unexpected operator
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-27-generic-pae
##################################################
The Setup Script is completed !
##################################################

So then I reboot and still same problem. The wireless continually tries to connect to my router and asks for the password over and over and won't connect. Before I tried all of the above I tried what was listed in this forum: **[http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839)** At one point the wireless would work! However, after unplugging the ethernet I was using, the connection eventually is lost. I know it's not a signal problem because I can use this same micro adapter on any other computer in the house and it works just fine. 

And before that I tried messing around with ndiswrapper and like I said probably removed ndiswrapper incorrectly.......:(

What am I doing wrong?? Do I need to remove ndiswrapper (correctly) and all these other multiple drivers that are probably installed now? If so, how? HELP!

Thanks in advance ( I know....your eyebrows are all probably raised at this point...lol)

---

### Post by kurt18947 on 2012-08-02
I ran into the same problem.  Same chipset, different manufacturer.  I took the easy way out and downloaded RealTek's driver.  It comes with an install script which make it very easy.  Ubuntu 11.10 and Mint 13 required blacklisting the  driver included in the kernel,  Ubuntu 12.04 did not.  Here is the Realtek web site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

RTL8188CUS is the one I'm using and it's fast & reliable.  The caveat with using Realtek's driver is to keep the folder where you can find it again.  A new kernel will kill the driver and require re-running the script.  There's no uninstall/reinstall, just run the install script again and the lil' blue light should start flashing again.

---

### Post by katsumodo on 2012-08-02
I wish it were that simple. However, it still continues to ask for the password over and over and never connects. :(

---

### Post by chili555 on 2012-08-02
>  I know....your eyebrows are all probably raised at this point.A little bit...

First, rtl8192cu is built in to the kernel in 12.04 and covers your device. I am wondering why you tried ndiswrapper and downloaded the Realtek driver instead of the driver that's built in. Mostly, I am wondering how many competing drivers are loaded now. Please post:```
lsmod | grep -e ndis -e 8192
```If the built in and ndiswrapper also tried and failed to connect, it's likely not the driver then; it's likely Network Manager.

Thanks.

---

### Post by kurt18947 on 2012-08-02
> **chili555 said:**
> A little bit...

First, rtl8192cu is built in to the kernel in 12.04 and covers your device. I am wondering why you tried ndiswrapper and downloaded the Realtek driver instead of the driver that's built in. Mostly, I am wondering how many competing drivers are loaded now. Please post:```
lsmod | grep -e ndis -e 8192
```If the built in and ndiswrapper also tried and failed to connect, it's likely not the driver then; it's likely Network Manager.

Thanks.

Dueling drivers - or circular firing squads - is a good point.  There does seem to be some problem with the built-in driver and the RTL8188CUS chip.  When trying the built-in driver it would find the adapter but may or may not connect.  Usually not and if it did show a connection there was no data transfer taking place.   I had to blacklist rtl8291cu on some installs when using RealTek's driver.   It might be network manager, I don't know and I've never had much luck with wicd.

---

### Post by chili555 on 2012-08-02
>  It might be network manager, I don't know and I've never had much luck with wicd.Have you ever tried removing NM altogether and setting up /etc/network/interfaces? Then you will *know* if it is or isn't NM.

I suspect NM and wpa_supplicant and their interaction with the specific driver is at the heart of more problems than we know. The only solution most try is yet another driver with the same old faulty NM and/or wpa_supplicant...and then another.

---

### Post by katsumodo on 2012-08-02
Thanks for the help Chili! Here is the results to lsmod | grep -e ndis -e 8192

jon@jon-desktop:~$** lsmod | grep -e ndis -e 8192**
rtl8192cu              66592  0 
rtl8192c_common        46721  1 rtl8192cu
rtlwifi                64087  1 rtl8192cu
mac80211              465127  3 rtl8192cu,rtl8192c_common,rtlwifi
compat                 13247  4 rtl8192cu,rtlwifi,mac80211,cfg80211

so meaning there's a few too many right? :(

---

### Post by chili555 on 2012-08-02
Not really; maybe just the wrong ones. Please try:```
sudo modprobe -r rtl8192su
sudo modprobe 8192cu
```Any improvement? Any errors, warnings, etc.?

---

### Post by katsumodo on 2012-08-02
jon@jon-desktop:~$ sudo modprobe -r rtl8192su
[sudo] password for jon: 
FATAL: Module rtl8192su not found.
jon@jon-desktop:~$ sudo modprobe 8192cu
FATAL: Error inserting 8192cu (/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/8192cu.ko): Device or resource busy

---

### Post by chili555 on 2012-08-02
> FATAL: Module rtl8192[COLOR="Red"]s[/COLOR]u not found.Sorry; I made a mistake. I should have said:```
sudo modprobe -r rtl8192[COLOR="Red"]c[/COLOR]u
sudo modprobe 8192cu
```Sorry for the mis-step. Please try again.

---

### Post by katsumodo on 2012-08-02
I entered the commands and they just went to the next line with no errors. I rebooted and still  have the same issue. The wireless just continually tries to connect and ask for the password over and over. Any other ideas?

---

### Post by chili555 on 2012-08-02
> I rebooted and still have the same issue. When you reboot, these temporary changes are wiped out. Is there any change in performance if you execute the changes and *DO NOT* reboot? If so, we can amend a couple of files and make them persistent.> I entered the commands and they just went to the next line *with no errors*.Perfect.

---

### Post by katsumodo on 2012-08-02
Ah yes there is a difference now. Right after entering <sudo modprobe -r rtl8192cu> the  wireless from system settings> network disappears. Just ethernet now.

---

### Post by chili555 on 2012-08-02
> **katsumodo said:**
> Ah yes there is a difference now. Right after entering <sudo modprobe -r rtl8192cu> the  wireless from system settings> network disappears. Just ethernet now.Since you unloaded the possibly incorrect driver rtl8192cu, that's what we expected. Now what happens when you load the driver you carefully compiled:```
sudo modprobe 8192cu
```> Authentication requested [root] for install driver:
install -p -m 644 [COLOR="Red"]8192cu[/COLOR].ko /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-27-generic-pae

---

### Post by katsumodo on 2012-08-02
jon@jon-desktop:~$ sudo modprobe 8192cu
[sudo] password for jon: 
jon@jon-desktop:~$

No difference. Wireless still won't show up or even try connecting in system settings > network :(

---

### Post by chili555 on 2012-08-02
Let's see if there are any messages that help us here:```
sudo modprobe 8192cu
dmesg | grep 8192
```Thanks.

---

### Post by katsumodo on 2012-08-02
jon@jon-desktop:~$ **sudo modprobe 8192cu**
[sudo] password for jon: 
jon@jon-desktop:~$ **dmesg | grep 8192**
[    0.825437] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   17.187312] rtl8192cu: Chip version 0x10
[   17.445993] rtl8192cu: MAC address: 4c:60:de:5e:db:80
[   17.446003] rtl8192cu: Board Type 0
[   17.446171] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   17.462869] usbcore: registered new interface driver rtl8192cu
[   18.097160] rtl8192cu: MAC auto ON okay!
[   18.147283] rtl8192cu: Tx queue select: 0x05
[  108.204056] usbcore: deregistering interface driver rtl8192cu
[  117.693627] usbcore: registered new interface driver rtl8192cu
[ 2072.247444] Error: Driver 'rtl8192cu' is already registered, aborting...
jon@jon-desktop:~$

---

### Post by Transmogriphi on 2012-08-03
Hi.  I'm a total noob in Ubuntu as well, and am having the same problem.  I dual booted 12.04 on Macbook 8,1.  After dealing with the Broadcom 43xx driver issue using the instructions at 
[http://www.techlw.com/2012/06/macbook-pro-wifiwireless-drivers-for.html](http://www.techlw.com/2012/06/macbook-pro-wifiwireless-drivers-for.html)
I now have the same problem as the original poster. The drivers work and my wireless card shows various wireless networks I can connect to.  When I choose one, it just keeps asking me for the password and attempting to connect over and over.

My apologies if I'm thread-jacking too much, but I think the solutions to our problems will be the same or similar (since the problems are similar). Instead of making a whole new thread for this issue, I'll just try to latch onto this one and see if we can't come up with a solution.

Thanks.

---

### Post by chili555 on 2012-08-03
> My apologies if I'm thread-jacking too much, I believe you are. I think the original posters issue, at this point is related to his driver, rtl8192cu. You have a Broadcom device which is unrelated.

---

### Post by chili555 on 2012-08-03
> **katsumodo said:**
> jon@jon-desktop:~$ **sudo modprobe 8192cu**
[sudo] password for jon: 
jon@jon-desktop:~$ **dmesg | grep 8192**
[    0.825437] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   17.187312] rtl8192cu: Chip version 0x10
[   17.445993] rtl8192cu: MAC address: 4c:60:de:5e:db:80
[   17.446003] rtl8192cu: Board Type 0
[   17.446171] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   17.462869] usbcore: registered new interface driver rtl8192cu
[   18.097160] rtl8192cu: MAC auto ON okay!
[   18.147283] rtl8192cu: Tx queue select: 0x05
[  108.204056] usbcore: deregistering interface driver rtl8192cu
[  117.693627] usbcore: registered new interface driver rtl8192cu
[ 2072.247444] [COLOR="Red"]Error: Driver 'rtl8192cu' is already registered, aborting...[/COLOR]
jon@jon-desktop:~$Thsi suggests that rtl8192cu didn't get unloaded correctly for whatever reason. Please try this:```
sudo modprobe -r rtl8192cu
```Now check:```
lsmod | grep -e rtl -e 80211
```Anything you find, please remove with:```
sudo modprobe -r whatyoufound
```Check again:```
lsmod | grep -e rtl -e 80211
```Keep going until there is nothing reported back when you check.

Now load the newer driver:```
sudo modprobe 8192cu
```Check:```
dmesg | grep 8192
```Will it now connect? If so, we'll need to amend a couple of files.

---

### Post by katsumodo on 2012-08-05
Sorry for the delay in responses, I was out of town for the weekend. But I'm back and ready to tackle this wireless network debacle once again! :)

 

 So here's what happened when I tried what you replied with:
 

 ```
sudo modprobe -r rtl8192cu
```
 results: 

no errors or results back in terminal, but the small black network connection indicator window pops up in the top right hand corner of the screen and displays “Wireless Network: Disconnected.” Also at this point wireless networks do not show in System Settings > Network. Only ethernet.
 

 ```
lsmod | grep -e rtl -e 80211
```
 results: 

no results were given in terminal, so I guess nothing to remove?
 

 Load the new driver:
 ```
sudo modprobe 8192cu
```
 results: 

no errors in terminal
 

 Check:
 ```
dmesg | grep 8192
```
 

 results:
 ```
[    0.829439] agpgart-intel 0000:00:00.0: detected 8192K stolen memory 
 [   17.548532] rtl8192cu: Chip version 0x10 
 [   17.766780] rtl8192cu: MAC address: 4c:60:de:5e:db:80 
 [   17.766789] rtl8192cu: Board Type 0 
 [   17.766822] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin 
 [   17.770848] usbcore: registered new interface driver rtl8192cu 
 [   18.168282] rtl8192cu: MAC auto ON okay! 
 [   18.212673] rtl8192cu: Tx queue select: 0x05 
 [  292.024055] usbcore: deregistering interface driver rtl8192cu 
 [  728.985365] usbcore: registered new interface driver rtl8192cu 
```


 After doing the above steps it unfortunately looks like we still have the same problem. Wireless doesn't pick up on it's own and wireless networks do not appear in System Settings > Network. Only "Wired" and "Network Proxy."

---

### Post by chili555 on 2012-08-07
> [  292.024055] usbcore: deregistering interface driver rtl8192cu 
 [  728.985365] usbcore: registered new interface driver rtl8192cuThis may be an issue. It looks like the same in-kernel driver was reloaded. Let's verify. Please repeat all of the commands above and check:```
lsmod | grep 8192
```Is it [COLOR="Red"]rtl[/COLOR]8192cu that's loaded or the driver you compiled, 8192cu? If it is 8192cu, the compiled version, we know it isn't helping us at all and we may as well uninstall it:```
cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/
sudo make uninstall
```The next thing we might try is the Ubuntu version of the compat-wireless driver:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```Reboot and let us know if there is any improvement.

---

### Post by katsumodo on 2012-08-07
jon@jon-desktop:~$ **[COLOR=Black]sudo modprobe -r rtl8192cu[/COLOR]**
[sudo] password for jon: 
jon@jon-desktop:~$** lsmod | grep -e rtl -e 80211**
jon@jon-desktop:~$ **sudo modprobe 8192cu**
jon@jon-desktop:~$** lsmod | grep 8192**
[COLOR=Red]**8192**[/COLOR]cu                502394  0 
jon@jon-desktop:~$ **cd Desktop**
jon@jon-desktop:~/Desktop$ **cd RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/**
jon@jon-desktop:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ **sudo make uninstall**
make: *** No rule to make target `uninstall'.  Stop.

how come it won't uninstall? I've seen this before but haven't figured out why it appears.

Thanks again for all the help Chili!

---

### Post by chili555 on 2012-08-07
> jon@jon-desktop:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ sudo make uninstall
make: *** No rule to make target `uninstall'. Stop.Let's see what our possibilities are:```
ls ~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622
```I know there is an install.sh in there, but is there an uninstall script or ...what? If there is a README, please attach it to your reply if you can't see any uninstall instructions.

---

### Post by katsumodo on 2012-08-07
I couldn't find any uninstall scripts in this folder. I've attached all the documentation I could find. I went through all the documentation and couldn't find anything that related to uninstalling it. :( You'll probably be able to find something though if it's not as obvious.

---

### Post by chili555 on 2012-08-07
> I couldn't find any uninstall scripts in this folder. What all is in the folder?```
ls ~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622
```Is there a tarball in there that the install.sh extracts that itself contains the Makefile; and therefor the 'make uninstall?'

---

### Post by katsumodo on 2012-08-07
The path to the folder that was on my desktop i think is the wrong one and an earlier one that I was playing around with. The path to the one I believe is the original is listed below. 

jon@jon-desktop:~/Desktop/Jon/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ ls
**android_reference_codes    **          install.sh
**android_reference_codes_ICS_nl80211**  readme.txt
**document**                             ReleaseNotes.pdf
**driver**                               **WiFi_Direct_User_Interface**
**hardware_wps_pbc**                     **wireless_tools**
[COLOR=YellowGreen]**install**[/COLOR]                              **wpa_supplicant_hostapd**

---

### Post by chili555 on 2012-08-07
How about:```
cd driver && ls
```

---

### Post by katsumodo on 2012-08-07
jon@jon-desktop:~/Desktop/Jon/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ **cd driver && ls**
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622.tar.gz

---

### Post by chili555 on 2012-08-07
> jon@jon-desktop:~/Desktop/Jon/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ cd driver && ls
[COLOR="Red"]rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622[/COLOR]
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622.tar. gzAnd there is the file the install script extracted. Now please do:```
cd rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622
sudo make install
```Then install the backports package and let's cross our fingers.

---

### Post by katsumodo on 2012-08-07
I take it you meant "sudo make uninstall" instead of "sudo make install"? So I ran sudo make uninstall in that directory,then installed the backports package, and then rebooted. And......drumroll please.......no success. Still asking for the password over and over. :(

---

### Post by chili555 on 2012-08-07
We are quickly getting to the end of our options. Let's try a driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```I am shutting down for the evening; back tomorrow.

---

### Post by katsumodo on 2012-08-08
It actually connected! I'm not sure if driver/setup has anything to do with poor signal strength because it's connected at 11mbps. Nevertheless it is connected! So how do we make these changes permanent?

---

### Post by chili555 on 2012-08-08
> Nevertheless it is connected! So how do we make these changes permanent?Woo hoo!

Please do:```
sudo gedit /etc/modprobe.d/rtl8192cu.conf
```A new empty file will open. Add one line:```
options rtl8192cu swenc=1
```Proofread, save and close gedit. Please use thread tools at the top to mark Solved.

---

### Post by katsumodo on 2012-08-08
I spoke too soon.....<bangs head on desk> I entered everything you told me to, unhooked my ethernet, restarted and now it won't connect and keeps asking for the password. :( :( :(

---

### Post by katsumodo on 2012-08-08
but to be clear, it did connect before. And I even disconnected my ethernet to see if the connection was working. Ran a speed test and everything and it was fine! ugh......why?! <shakes fists in the air>

---

### Post by chili555 on 2012-08-09
I am running very low on reasonable ideas. Let's ditch Network Manager and see if Wicd works better:```
sudo apt-get install wicd
sudo apt-get remove --purge network-manager
```Reboot with the ethernet detached, open Wicd and connect.

---

### Post by katsumodo on 2012-08-09
I installed WICD but it won't pick up any wireless networks. It recognizes wired connections but won't pick up any of the wireless networks nearby.

---

### Post by katsumodo on 2012-08-09
Actually I did find out how to get it to find networks by changing wlan0 to wlan2 etc. However it will still try to 'validate authentication' and eventually fail due to "bad password". I've even tried different different encryptions ie. WEP passphrase, hex 0-9/A-F, etc. and none will connect. So essentially the same problem as before with this network manager as well. <bangs head on desk> :(

---

### Post by chili555 on 2012-08-09
Me, too. Off to bed.

"Now,in the bullpen warming up we see NDISWRAPPER!"

---

### Post by chili555 on 2012-08-10
> And before that I tried messing around with ndiswrapper And what was your experience? Do you have the Windows *XP* .inf and .sys files available? Mind if we try again?

---

### Post by katsumodo on 2012-08-10
I never could find the right files. The only thing I have is the small driver CD that came with the USB adapter. The files I see on the CD are things like "autorun.inf","setup.ini","TRANS.tbl", "autorun.exe" etc. How do I install ndiswrapper again? **sudo get-apt ndisgtk**?

---

### Post by chili555 on 2012-08-10
> **katsumodo said:**
> I never could find the right files. The only thing I have is the small driver CD that came with the USB adapter. The files I see on the CD are things like "autorun.inf","setup.ini","TRANS.tbl", "autorun.exe" etc. How do I install ndiswrapper again? **sudo get-apt ndisgtk**?Yes, exactly.

Let me look around a bit before we try to extract the autorun.exe or install it with wine. Back in a few minutes.

---

### Post by chili555 on 2012-08-10
Is yours a 32- or 64-bit system?```
arch
```I found the files right where you found the Linux drivers; on Realtek's site!

---

### Post by katsumodo on 2012-08-10
Nice!

My system is running on "i686" (32 bit)

---

### Post by chili555 on 2012-08-10
First we need to unload and blacklist the native driver:```
sudo su
modprobe -r rtl8192cu
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf

```Now we load the Windows driver. Download the file I've attached to your desktop. Right-click it and select *Extract Here*. Now back to the previously opened terminal:```
ndisgtk
```When the window opens, point it to Desktop/WinXP/netrtwlanu.inf and let it install the driver and firmware files. Now in the terminal:```
modprobe ndiswrapper
exit
```Any improvement?

---

### Post by katsumodo on 2012-08-10
I ran sudo apt-get install ndisgtk and from what it looked like it installed correctly. However when I point ndiswrapper at that .inf file I get this message in ndiswrapper:

"Module could not be loaded. Error was:
FATAL: Module ndiswrapper not found.
Is the ndiswrapper module installed?"

Ideas?

---

### Post by chili555 on 2012-08-10
Please do:```
sudo apt-get install ndiswrapper-dkms
```After it's done, try again. Meantime, I shall draft a bug report.

---

### Post by katsumodo on 2012-08-10
So it looks like I installed the dkms module successfully. I installed the windows driver, and as it stands without rebooting I have no connection. I noticed that the hardware status in ndiswrapper said "Hardware Present: No" so I clicked on "Configure Network" upon which an error message popped up saying, "Could not find a network configuration tool." Does this mean that we need to switch back to the default network configuration tool instead of using wicd? (if so, how would I do that?) Also no wireless options or responses are appearing/happening in either wicd, or network tools. 



Just rebooted and still seeing the same issues.

---

### Post by chili555 on 2012-08-10
> ID [COLOR="Red"]0846:9041[/COLOR] NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]The inf file I attached includes this:> [Netgearcus.NTx86]
;;%Netgearcus.DeviceDesc% = RTL8192cu.ndi, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9041[/COLOR]				      ; Netgear 88CUSfor B/G/NI feel it's the correct file for your device. Please post:```
ndiswrapper -l
dmesg | grep ndis
```That's an l for 'list.' Thanks.>  Does this mean that we need to switch back to the default network configuration tool instead of using wicd?I doubt it. Let's troubleshoot first.

---

### Post by katsumodo on 2012-08-10
jon@jon-desktop:~$** ndiswrapper -l**
netrtwlanu : driver installed
jon@jon-desktop:~$ **dmesg | grep ndis**
jon@jon-desktop:~$ 


no results showed for **dmesg | grep ndis**

---

### Post by chili555 on 2012-08-11
Please try:```
sudo ndiswrapper -d 0846:9041 netrtwlanu
dmesg | grep ndis
sudo modprobe ndiswrapper
```Any improvement?

This problem is getting more tenacious than my ex-wife's lawyer!!

---

### Post by katsumodo on 2012-08-11
It's connected! But I lose it when I reboot! :(Only after repeated the steps you gave me again will it find networks and connect again.

---

### Post by chili555 on 2012-08-11
Please try this:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Reboot and let us have a good report!

---

### Post by katsumodo on 2012-08-11
HAIL TO THE CONQUERING HERO! Chili you are the man!! Wifi is working like a charm now. Tested it several different ways and so far it's working perfectly! I can't thank you enough! So in conclusion, what exactly was the problem? Was it just that I had the wrong driver? Or was it that it just had to be installed with ndiswrapper? Anyhow, thank you so much. I'm sure this thread will be of much help to several others out there with same or similar problems. 

THANK YOU! :D:D:D:D:D

---

### Post by chili555 on 2012-08-11
Thank you for your very kind comments.

The native Linux drivers evidently aren't working well right now. We tried and succeeded with the Windows XP driver wrapped with the ndiswrapper driver tool. In a future Ubuntu release, the newer accompanying native driver will work better, but in your case, I suggest you not experiment with what isn't broken; namely, ndiswrapper.

Wow! A lightning fast 55 posts! For the benefit of the other interested persons, please use thread tools at the top to mark Solved.

By the way, you persevered just as well as I did. Great job!

---

### Post by edfast on 2012-10-31
@chili555; My god, chili, I can't believe what you just made me do to my computer... I am running lubuntu 12.04 off of my daughter's ancient compaq presario. Have been using it for a few years already, mostly to fiddle around with various linux distros. However, was never able to get it to hook up to our home wifi network, even using a plethora of linux flavours and incarnations, so had to remain within a cable's length of the router, which seemed a bit of a chore in this 21st century. I finally gave up on the resident wifi module, and bought the N150, but still no luck. Found this thread a week later, followed as best I could, ended up in the ditch a couple of times, but managed to crawl out and continued down the path. And now the old lump is actually working!! I guess I won't be able to scrap it, after all... Many thanks, this was quite a ride!:D

---

### Post by chili555 on 2012-10-31
> And now the old lump is actually working!! I guess I won't be able to scrap it, after all... Many thanks, this was quite a ride!Wow! I just received my payday! Thank you for your kind comments. I'm very glad it's working.

---

### Post by winwiz on 2012-11-20
To anyone still watching this thread:

Last week, I got a new PC assembled for android build and got this WLAN adapter to connect my system to network. I have an Intel i5 3570 and I am running Ubuntu 12.04 LTS (64-bit).

I have the exact same issue, unfortunately, my happiness seeing this solution ended with a kernel panic when I modprobed ndiswrapper after installing a 'WinX64' driver.

I tried drivers from 'WinXP' as well as 'Win7X64' folders from the latest Realtek driver package. It will either fail to load or it will end in a kernel panic.

The attachment 'WinXP.zip' would not work for me since my 'arch' is 'X86_64'. I have tried steps like blacklisting the driver that came with Ubuntu, re-build the latest Linux driver in Ubuntu etc.

From Ubuntu's site I downloaded the following packages required (using another machine connected to internet):
ndisgtk_0.8.5-1_amd64.deb
ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb
python-glade2_2.24.0-3_amd64.deb
dkms_2.2.0.3-1ubuntu3_all.deb
libglade2-0_2.6.4-1ubuntu1.1_amd64.deb

I got the following from Realtek for (ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]):
RTL819xCU_AutoInstallPackage.zip
RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip
v14114-OmniPeek-V6_CU_DU.zip

Any ideas to make this work?

---

### Post by chili555 on 2012-11-20
> **winwiz said:**
> To anyone still watching this thread:

Any ideas to make this work?Please try this.

By the way, ndiswrapper always requires *XP* drivers.

---

### Post by winwiz on 2012-11-20
> **chili555 said:**
> Please try this.

By the way, ndiswrapper always requires *XP* drivers.

hmm... that is why is was complaining about some missing symbols when I tried with Windows 7 driver.

I tried with the version you attached but again there is a kernel panic. I also tried Win XP X64 version from the latest version of the driver and it has the same issue. Along with the call trace I see a line which says:

BUG: scheduling while atomic: kworker/u:5/65/0x10000200
...
Pid:65, comm: kworker/u:5 Tainted: P      D  C O 3.2.0-29-generic #46-Ubuntu
...

Could this happen because I installed 'dkms' package and deps that I downloaded manually (not using apt-get and not checking if it is for 12.04.1 LTS 64-bit)?

---

### Post by chili555 on 2012-11-20
> **winwiz said:**
> 
Could this happen because I installed 'dkms' package and deps that I downloaded manually (not using apt-get and not checking if it is for 12.04.1 LTS 64-bit)?It could very well be. Can you correct that? Either hook up the ethernet temporarily and do:```
sudo apt-get install --reinstall dkms
```Or, if that's not an option, remove the debs you installed and download and install new ones with respect to architecture, version, etc.

R-E-S-P-E-C-T, as the lady says.

---

### Post by winwiz on 2012-11-23
> **chili555 said:**
> Or, if that's not an option, remove the debs you installed and download and install new ones with respect to architecture, version, etc.

I downloaded the DVD version of 12.04.1 LTS (64-bit [amd64]) and re-installed Ubuntu. Now the only package missing was 'ndiswrapper-dkms'.

I downloaded and installed the correct version from [here]("http://www.ubuntuupdates.org/package/core/precise/universe/base/ndiswrapper-dkms") but still I get a kernel panic as soon as I do 'modprobe ndiswrapper'.

Might have something to do with NDIS or the WLAN driver on a SMP 64-bit CPU (4 cores)??

On Windows 7 (another machine) with AMD Dual Core 64-bit, I am able to scan for networks using the same adapter.

Any other go? Is there a patch (by 3rd party or a dev) which I can apply to the Linux driver source code for resolving this bug?

---

### Post by chili555 on 2012-11-23
> Might have something to do with NDIS or the WLAN driver on a SMP 64-bit CPU (4 cores)??Indeed. 

Are there any interesting messages here after a kernel panic and reboot?```
sudo cat /var/log/dmesg.0 | grep ndis
sudo cat /var/log/syslog | grep ndis
ndiswrapper -l
```Depending on what we see, you could:

*Compile the latest ndiswrapper 1.58-rc1; or
*Try 32-bit; or
*Try a different wireless device.

---

### Post by priyadarsanroy on 2013-02-04
I tried this same device in Linux Mint 13 which is a derivative of ubuntu 12.04 and it works. Just plug it in and the default drivers works. Where as in Ubuntu the same driver keeps asking for the password. Strange.

---

### Post by Whitehatyoyoer on 2013-02-11
Chili, I thank you. I followed the instructions you gave to people on this post and another, and got kinda frustrated. Then I used ndiswrapper and the Windows driver and it works perfectly. You truly are a master at this.

--Whitehat

---

### Post by ceptic on 2013-03-03
> **chili555 said:**
> Wow! I just received my payday! Thank you for your kind comments. I'm very glad it's working.

Chilli, I also want to say thank you for your patience and thoroughness in this 'tutorial'/problem solving exercise. My Netgear USB N150 is now working on my old TPG laptop (Arima W720-K8M)... I was worried I was going to have to go back to clunky XP from Lubuntu 12.04 but everything is great. It is forums and communities like this that make playing on linux so much fun!

---

### Post by chili555 on 2013-03-03
Thanks for your nice comments and enjoy Ubuntu!

---

### Post by DZDB on 2013-03-25
**Installing USB G54/N150 Adapter on Ubuntu 12.04**
 
 
I have Ubuntu 12.04.  I am trying to get my Netgear n-150 micro usb adapter to work.  I successfully installed ndiswrapper by going to the software center and installing the following:
 

[LIST=1]
[*]ndisgtk
[*]ndiswrapper-source
[*]ndiswrapper-dkms
[*]ndiswrapper-common
[*]ndiswrapper-utils-1.9
[/LIST]
 
I now I no longer receive the “FATAL: Module ndiswrapper not found” error message.  Using the ndisgtk application, I tried to install the following windows drivers:
 

[LIST=1]
[*]netrtwlanu.inf
[*]RTLBt.inf
[/LIST]
 

[LIST=1]
[*]In each case I received an “Invalid Driver” error message. So my question is which specific window driver do I need to install for the micro Netgear n-150 usb adapter? I was thinking that I need to install the windows driver “netrtwlanu.inf”.
[/LIST]

---

### Post by chili555 on 2013-03-25
> In each case I received an “Invalid Driver” error message. So my question is which specific window driver do I need to install for the micro Netgear n-150 usb adapter? You need the XP driver appropriate to your architecture, either 32- or 64-bit. Confirm:```
arch
```If yours is a 32-bit system (i686), I'd try the drivers I attached in post #46 above. Then be sure to add the step I suggested in post #52.

If yours is a 64-bit system (x86_64), I probably have something I could attach.

---

### Post by DZDB on 2013-03-26
When I installed Ubuntu 12.04, I installed the 32-bit version.  So I am pretty sure that I have a 32-bit system (i686).  However is there a command that I can run from the terminal to confirm this? One note.  I am a real newby.

I did try the drivers that you attached in post 46 (WinXP.zip).  Next I extracted the drivers to the desktop.  I then went into the ndisgtk application (the description on the icon is "Windows Wireless Drivers") and I pointed it to Desktop/WinXP/netrtwlanu.inf.  At that point I received the following error message:

"netrtwlanu Invalid Driver!"

I guess my next step is to confirm that I have a 32-bit system.  If I do have a 32-bit system then what would be my next step?

---

### Post by chili555 on 2013-03-26
>  So I am pretty sure that I have a 32-bit system (i686). However is there a command that I can run from the terminal to confirm this? One note. I am a real newby.
Yes, there is:```
arch
```> "netrtwlanu Invalid Driver!"Let's have a look at:```
lsusb
```

---

### Post by DZDB on 2013-03-27
[FONT=Times New Roman][SIZE=3][COLOR=#000000][FONT=Times New Roman][SIZE=3][COLOR=#000000]My results for Code Arch:[/COLOR][/SIZE][/FONT] MMmm
 [/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=3][COLOR=#000000][FONT=Times New Roman][SIZE=3][COLOR=#000000]My results for Code: arch[/COLOR][/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ arch[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]i686[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$

So it is confirmed that I have a 32-bit system (i686).



My results for Code: lsub


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ lsusb[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS][/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 006 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash [EMAIL="Drivedzdb@dzdb-System-Product-Name:~$"]Drive[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT]What is my next step?

[FONT=Times New Roman][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]




[/COLOR][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT]

---

### Post by chili555 on 2013-03-27
I think it is actually the correct driver for your device. Let's see if we can find out what's wrong. With the device inserted, please run and post:```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```Some of these may produce errors or warnings; it is those that we'll use to find out what to fix.

---

### Post by bezgoan on 2013-03-27
Hi Chill,

I have same problem of wifi disconnecting from TP-WN821N usb wifi device.
Using 12.10 64 bit on i7 3770 core.

out of the commands you gave 
sudo modprobe -r rtl8192cu 
successfully uninstalled the module.
but doesn't seem to recognize sudo modprobe 8192cu command.

lsmod | grep -e rtl -e 80211 returns nothing.

sudo apt-get install linux-backports-modules-cw-2.2-precise-generice-pae didn't work

sudo modprobe rtl8192cu swenc=1 seems to connect to network but there is no traffic seen and get page not available error 

Didn't wanted to try ndiswrapper as I am on 64 bit and XP drivers might not help.

Please suggest.

Thanks
Shashank.

---

### Post by chili555 on 2013-03-27
> **bezgoan said:**
> Hi Chill,

I have same problem of wifi disconnecting from TP-WN821N usb wifi device.
Using 12.10 64 bit on i7 3770 core.

out of the commands you gave 
sudo modprobe -r rtl8192cu 
successfully uninstalled the module.
but doesn't seem to recognize sudo modprobe 8192cu command.

lsmod | grep -e rtl -e 80211 returns nothing.

sudo apt-get install linux-backports-modules-cw-2.2-precise-generice-pae didn't work

sudo modprobe rtl8192cu swenc=1 seems to connect to network but there is no traffic seen and get page not available error 

Didn't wanted to try ndiswrapper as I am on 64 bit and XP drivers might not help.

Please suggest.

Thanks
Shashank.Let's confirm your exact device:```
lsusb
iwconfig

```Thanks.

---

### Post by bezgoan on 2013-03-27
Hi Chill,

was eagerly waiting for response...

output below..

lsusb 

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 058f:6387 Alcor Micro Corp. Flash Drive
**Bus 001 Device 007: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 002 Device 003: ID 1a2c:0023  
Bus 002 Device 004: ID 0461:4d64 Primax Electronics, Ltd 


iwconfig :
eth0      no wireless extensions

lo          no wireless extensions

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
Thanks
Shashank.

---

### Post by bezgoan on 2013-03-27
Apologies for mis-spell. It should be Chili all the way.

Off tonight :-(.
Will get back to you tomorrow.

---

### Post by bezgoan on 2013-03-28
Hi chili any luck with device ?

---

### Post by DZDB on 2013-03-28
Chili555, my results of the terminal commands are as follows:

ndiswrapper -l:

[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]netrtwlanu : invalid [EMAIL="driver!dzdb@dzdb-System-Product-Name:~$"]driver![/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]

sudo modprobe ndiswrapper:


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo modprobe ndiswrapper[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/COLOR][/SIZE][/FONT]


dmesg | grep ndis:


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ dmesg | grep ndis[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][ 1649.605116] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][ 1649.681346] usbcore: registered new interface driver [EMAIL="ndiswrapperdzdb@dzdb-System-Product-Name:~$"]ndiswrapper[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]

---

### Post by chili555 on 2013-03-28
> **bezgoan said:**
> 

sudo modprobe rtl8192cu swenc=1 seems to connect to network but there is no traffic seen and get page not available error 

When it says it is connected and the ethernet is not, please run and post:```
ifconfig
iwconfig
nm-tool
```Thanks.

---

### Post by chili555 on 2013-03-28
> **DZDB said:**
> 

[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]netrtwlanu : invalid [EMAIL="driver!dzdb@dzdb-System-Product-Name:~$"]driver![/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]

Please try the step in post #52 above: [http://ubuntuforums.org/showthread.php?t=2036445&page=6&p=12164705#post12164705](http://ubuntuforums.org/showthread.php?t=2036445&page=6&p=12164705#post12164705)

---

### Post by bezgoan on 2013-03-28
> **chili555 said:**
> When it says it is connected and the ethernet is not, please run and post:```
ifconfig
iwconfig
nm-tool
```Thanks.


output:

ifconfig:


bezgoan@bezgoan-optimus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:46:5d:90:a7:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:315640 (315.6 KB)  TX bytes:315640 (315.6 KB)


wlan0     Link encap:Ethernet  HWaddr a0:f3:c1:0f:f5:10  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a2f3:c1ff:fe0f:f510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942 (942.0 B)  TX bytes:13787 (13.7 KB)








iwconfig:
bezgoan@bezgoan-optimus:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Thomson87C510"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:87:C5:10   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




bezgoan@bezgoan-optimus:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Thomson87C510] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        A0:F3:C1:0F:F5:10


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    SKY02685:        Infra, 00:1F:33:82:60:92, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    TALKTALK-289410: Infra, 34:6B:D3:28:94:12, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTHomeHub2-KH28: Infra, 00:24:17:CC:FA:7D, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTHub3-TGH3:     Infra, 00:81:D8:79:9A:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTHub3-2T2S:     Infra, AC:E8:7B:4D:87:5B, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWiFi:          Infra, 02:81:D8:79:9A:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    BTWiFi-with-FON: Infra, 12:81:D8:79:9A:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    *Thomson87C510:  Infra, 00:26:44:87:C5:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA
    BTWiFi-with-FON: Infra, 62:E8:7B:4D:87:5D, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    BTWiFi:          Infra, 62:E8:7B:4D:87:5C, Freq 2462 MHz, Rate 54 Mb/s, Strength 100


  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:46:5D:90:A7:E1


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


Thanks
Shashank.

---

### Post by chili555 on 2013-03-28
Looks pretty solid, but, as we see, traffic is being passed:> wlan0 Link encap:Ethernet HWaddr a0:f3:c1:0f:f5:10
inet addr:192.168.1.69 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::a2f3:c1ff:fe0f:f510/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6 errors:0 dropped:0 overruns:0 frame:0
TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
[COLOR="#FF0000"]RX bytes:942 (942.0 B) TX bytes:13787 (13.7 KB)[/COLOR]
Are these settings obtained by DHCP, that is, automatically, from the router? Can you ping the router?```
ping -c3 192.168.1.254
```How about the outside world?```
ping -c3 8.8.8.8
```

---

### Post by bezgoan on 2013-03-28
Couple of observations:

a) ping 192.168.1.254 router gives Destination Host Unreachable
b) Found multiple instances of PC connected to router on router home page.
c) Made the ip address static for this PC, then followed same procedure  sudo modprobe rtl8192cu swenc=1
d) If I disconnect the network after it is found, it wont connect again.

Seems something is wrong with disconnection logic as well ??

---

### Post by chili555 on 2013-03-28
>  Made the ip address static for this PC, Why, I wonder. I suggest you remove any and all settings from Network Manager and let it do the heavy lifting.

---

### Post by bezgoan on 2013-03-28
When I restore all configurations and restart n/w mgr doesn't appear on the top right ??

nm-tool shows it is connecting to Thomson87c510 router (which is my router).

---

### Post by bezgoan on 2013-03-28
get reconfirmation of password, time and again, without any connection now.

---

### Post by bezgoan on 2013-03-28
> **chili555 said:**
> Looks pretty solid, but, as we see, traffic is being passed:Are these settings obtained by DHCP, that is, automatically, from the router? Can you ping the router?```
ping -c3 192.168.1.254
```How about the outside world?```
ping -c3 8.8.8.8
```


After a restart, nm came back and connected to network.

output:
bezgoan@bezgoan-optimus:~$ ping -c3 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.69 icmp_seq=1 Destination Host Unreachable
From 192.168.1.69 icmp_seq=2 Destination Host Unreachable
From 192.168.1.69 icmp_seq=3 Destination Host Unreachable


--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2005ms
pipe 2
bezgoan@bezgoan-optimus:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.69 icmp_seq=1 Destination Host Unreachable
From 192.168.1.69 icmp_seq=2 Destination Host Unreachable
From 192.168.1.69 icmp_seq=3 Destination Host Unreachable


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms
pipe 2

---

### Post by chili555 on 2013-03-28
> **bezgoan said:**
> When I restore all configurations and restart n/w mgr doesn't appear on the top right ??

nm-tool shows it is connecting to Thomson87c510 router (which is my router).Does it re-appear if you do:```
nm-applet &
```You might have to leave the terminal open as you troubleshoot in order for the applet to remain.

---

### Post by bezgoan on 2013-03-28
> **chili555 said:**
> Does it re-appear if you do:```
nm-applet &
```You might have to leave the terminal open as you troubleshoot in order for the applet to remain.

got the nm back...lets not worry about it now.
More concerned about not able to access network.

---

### Post by bezgoan on 2013-03-28
> **chili555 said:**
> Looks pretty solid, but, as we see, traffic is being passed:Are these settings obtained by DHCP, that is, automatically, from the router? Can you ping the router?```
ping -c3 192.168.1.254
```How about the outside world?```
ping -c3 8.8.8.8
```

Hi Chili555,

Reposting the results of ping if you missed earlier.

[COLOR=#000000]After a restart, nm came back and connected to network.[/COLOR]

[COLOR=#000000]output:[/COLOR]
[COLOR=#000000]bezgoan@bezgoan-optimus:~$ ping -c3 192.168.1.254[/COLOR]
[COLOR=#000000]PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=1 Destination Host Unreachable[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=2 Destination Host Unreachable[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=3 Destination Host Unreachable[/COLOR]


[COLOR=#000000]--- 192.168.1.254 ping statistics ---[/COLOR]
[COLOR=#000000]3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2005ms[/COLOR]
[COLOR=#000000]pipe 2[/COLOR]
[COLOR=#000000]bezgoan@bezgoan-optimus:~$ ping -c3 8.8.8.8[/COLOR]
[COLOR=#000000]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=1 Destination Host Unreachable[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=2 Destination Host Unreachable[/COLOR]
[COLOR=#000000]From 192.168.1.69 icmp_seq=3 Destination Host Unreachable[/COLOR]


[COLOR=#000000]--- 8.8.8.8 ping statistics ---[/COLOR]
[COLOR=#000000]3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms[/COLOR]
[COLOR=#000000]pipe 2

Thanks
Shashank.[/COLOR]

---

### Post by bezgoan on 2013-03-28
SSH from troubled PC to laptop returns :
"The server at 192.168.1.68 cannot be found"

and 

from laptop to troubled PC
"SSH program unexpectedly exited."

---

### Post by bezgoan on 2013-03-28
Guys.... good news... I am now able to connect to network post changing my desktop to near-by router.
It should be bloody distance issue between router and PC.
I feel I am living in a palace not a 2 bed home.

But any suggestions how to get TP-LINK WUSB work at around 10-15 mts.

Btw..posting this from my troubled PC.

---

### Post by bezgoan on 2013-03-28
Just measure the distance between router and troubled location = 10.8 meters... and as per specs... the WUSB should perform at [COLOR=#333333][FONT=Arial]11M: -85dBm@8% PER.
[/FONT][/COLOR]

---

### Post by DZDB on 2013-03-29
Chili555, I ran the commands as you suggested (i.e. post 52) which were as follows:

Code:
sudo ndiswrapper -d 0846:9041 netrtwlanu
dmesg | grep ndis
sudo modprobe ndiswrapper

In addition I ran:

Code:
ndiswrapper -l

My results are as follows:

[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo ndiswrapper -d 0846:9041 netrtwlanu[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]WARNING: Driver 'netrtwlanu' will be used for '0846:9041'[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]This is safe _only_ if driver netrtwlanu is meant for chip in device 0846:9041[/COLOR][/SIZE][/FONT]



[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ dmesg | grep [EMAIL="ndisdzdb@dzdb-System-Product-Name:~$"]ndis[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo modprobe ndiswrapper[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/COLOR][/SIZE][/FONT]



[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]netrtwlanu : invalid [EMAIL="driver!dzdb@dzdb-System-Product-Name:~$"]driver![/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]


As you can see I got nothing on [FONT=Times New Roman][SIZE=3][COLOR=#000000]dmesg | grep [/COLOR][/SIZE][/FONT][EMAIL="ndisdzdb@dzdb-System-Product-Name:~$"][FONT=Times New Roman][SIZE=3]ndis[/SIZE][/FONT][/EMAIL].  The first time it said ndiswrapper version 1.57 loaded (post #80)

Based on post #52 I was really hoping/expecting to connect and then lose connection on the reboot.  Well that didn't happen.  So what are my next steps?

---

### Post by bezgoan on 2013-03-29
> **chili555 said:**
> Does it re-appear if you do:```
nm-applet &
```You might have to leave the terminal open as you troubleshoot in order for the applet to remain.


Hi Chili555,

Appreciate you support for last couple of days.
See you have good following on wireless related aspects.

Cheers
shashank.

---

### Post by chili555 on 2013-03-29
> **DZDB said:**
> Well that didn't happen.  So what are my next steps?Let's look for a different .inf file. Please download, extract and install this one. For the benefit of the searchers, it is for 32-bit only. 

Before you do so, uninstall the earlier one:```
sudo ndiswrapper -e netrtwlanu
sudo rm -rf /etc/ndiswrapper/*
```Fingers crossed!

---

### Post by DZDB on 2013-03-30
Chili, I ran the commands that you listed in post 98 which were as follows:

Code:
sudo ndiswrapper -e netrtwlanu
sudo rm -rf /etc/ndiswrapper/*


My results are as follows:
[FONT=Times New Roman][SIZE=3][COLOR=#000000][EMAIL="dzdb@dzdb-System-Product-Name:~$"]dzdb@dzdb-System-Product-Name:~$[/EMAIL] sudo ndiswrapper -e netrtwlanu[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/COLOR][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo rm -rf /etc/ndiswrapper/*[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$

Then I tried to load the netrtwlanu.inf file coming from the WinXPlater.zip file.  I received an "Invalid Driver" error message.

I then ran the following status codes for your information:

lsusb
ndiswrapper -l
dmesg | grep ndis

My results are as follows:


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ lsusb[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 001 Device 003: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS][/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Bus 006 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for [EMAIL="Businessdzdb@dzdb-System-Product-Name:~$"]Business[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL]
[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]netrtwlanu : invalid [EMAIL="driver!dzdb@dzdb-System-Product-Name:~$"]driver![/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/EMAIL][/COLOR][/SIZE][/FONT]

dzdb@dzdb-System-Product-Name:~$ dmesg | grep ndis
[   77.029981] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   77.082536] usbcore: registered new interface driver ndiswrapper
[  299.744208] usbcore: deregistering interface driver ndiswrapper
[  299.756638] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  299.781122] usbcore: registered new interface driver [EMAIL="ndiswrapperdzdb@dzdb-System-Product-Name:~$"]ndiswrapper[/EMAIL]
[EMAIL="ndiswrapperdzdb@dzdb-System-Product-Name:~$"]dzdb@dzdb-System-Product-Name:~$[/EMAIL]

Chili, I noted that when you were working with katsumodo, posts 45 or 46, you advised him to unload and blacklist the native driver.  So do need to do the same? And if so, can you give me the code?
 







[/COLOR][/SIZE][/FONT]

---

### Post by DZDB on 2013-03-30
Chili555, in addition I ran code lsmod|grep -e ndis -e8192 for your information.  My results are as follows:

dzdb@dzdb-System-Product-Name:~$ lsmod|grep -e ndis -e8192
rtl8192cu              97757  0
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95839  1 rtl8192cu
mac80211              436493  3 rtl8192cu,rtl8192c_common,rtlwifi
dzdb@dzdb-System-Product-Name:~$

---

### Post by chili555 on 2013-03-30
> **DZDB said:**
> Chili555, in addition I ran code lsmod|grep -e ndis -e8192 for your information.  My results are as follows:

dzdb@dzdb-System-Product-Name:~$ lsmod|grep -e ndis -e8192
rtl8192cu              97757  0
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95839  1 rtl8192cu
mac80211              436493  3 rtl8192cu,rtl8192c_common,rtlwifi
dzdb@dzdb-System-Product-Name:~$Let's blacklist the native driver:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us see:```
ndiswrapper -l
```

---

### Post by DZDB on 2013-03-30
Hi Chili,

Per your post #101 I ran the following:

Code:
sudo su
echo "blacklist rtl8192cu" &gt;&gt; /etc/modprobe.d/blacklist.conf
exit

I then rebooted and ran the following:

Code:
ndiswrapper -l

The results are as follows:

dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
netrtwlanu : invalid driver!
dzdb@dzdb-System-Product-Name:~$


In addition I ran the following:

Code:
lsusb
lsmod|grep -e ndis -e8192


The results are as follows:

dzdb@dzdb-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 003: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 006 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
dzdb@dzdb-System-Product-Name:~$



dzdb@dzdb-System-Product-Name:~$ lsmod|grep -e ndis -e8192
dzdb@dzdb-System-Product-Name:~$


Note "netrtwlanu : invalid driver!"

So what are my next steps? Should I uninstall and then install the "netrtwlanu" driver?

---

### Post by chili555 on 2013-04-01
> **DZDB said:**
> 

So what are my next steps? Should I uninstall and then install the "netrtwlanu" driver?Regrettably, I can find no better Windows XP files other than the ones you have tried. In fact, the WinXPlater files I attached were gathered from Realtek's own website and they seem to clash, in some way, with ndiswrapper. If you wish to continue to try ndiswrapper, I think the next step is to download and compile the latest version of ndiswrapper. [http://ubuntuforums.org/showthread.php?t=1695036&page=15&p=12573923#post12573923](http://ubuntuforums.org/showthread.php?t=1695036&page=15&p=12573923#post12573923)

---

### Post by DZDB on 2013-04-02
Chili, I thank you for all your efforts.  I just have a few follow-up questions which are as follows:

1) I blacklisted Ubuntu 12.04's native driver by using the following code:

    sudo su
    echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf  

    What is the code to unblacklist Ubuntu 12.04's native driver?

2) The netrtwlanu driver worked for Katsumodo (see post #55) and he has the same usb adapter which is Netgear usb n-150 wireless adapter.  So why isn't the netrtwlanu driver working for me? Is he using a different version of ndiswrapper? My version is 1.57.

3) I also have a Linksys N300 wireless-N usb adapter.  Can you give me a driver (inf file) that will work with the Linksys N300 adapter and ndiswrapper 1.57 in Ubuntu 12.04?

4) If you don't have a driver that will will work with the Linksys N300 adapter and ndiswrapper 1.57 in Ubuntu 12.04, then can you recommend a usb adapter that will work on Ubuntu 12.04 using ndiswrapper 1.57 (if necessary)?


Once again thanks for your efforts!

---

### Post by chili555 on 2013-04-02
> 1) I blacklisted Ubuntu 12.04's native driver by using the following code:

sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf

What is the code to unblacklist Ubuntu 12.04's native driver?Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```At the end will be the line: blacklist rtl8192cu. Remove it, or, if you want to be able to recall it in case you want to experiment, comment it out like this: #blacklist rtl8192cu. The hashtag # says to the system to not act upon what follows. This can be used to add explanations as well: #chili recommends in forum post.

After you have made your change, proofread carefully, save and close gedit. Then load the module again:```
sudo modprobe rtl8192cu
```> 2) The netrtwlanu driver worked for Katsumodo (see post #55) and he has the same usb adapter which is Netgear usb n-150 wireless adapter. So why isn't the netrtwlanu driver working for me? Is he using a different version of ndiswrapper? My version is 1.57.I have no idea which version he's using. I also have no idea why things occasionally work beautifully for one person and not at all for another. > 3) I also have a Linksys N300 wireless-N usb adapter. Can you give me a driver (inf file) that will work with the Linksys N300 adapter and ndiswrapper 1.57 in Ubuntu 12.04?Please tell me more:```
lsusb
```Let's try to solve this before you go shopping again.

---

### Post by DZDB on 2013-04-02
Chili, thanks for sticking with me.  I inserted the Linksys N300 usb adapter in the pc usb port and ran the following code:

lsusb

My results are as follows:

dzdb@dzdb-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 001 Device 002: ID 13b1:0039 Linksys AE1200 802.11bgnWireless Adapter [Broadcom BCM43235]
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical MouseM90
Bus 006 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120for Business
Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer MicroFlash Drive
dzdb@dzdb-System-Product-Name:~$

---

### Post by chili555 on 2013-04-02
The file is too big to add as an attachment, so I've given you a link to my personal Dropbox. [https://dl.dropbox.com/u/58267392/xpae1200.zip](https://dl.dropbox.com/u/58267392/xpae1200.zip)  It's still syncing, so give it a few minutes.

Gotta love the Dropbox!

---

### Post by DZDB on 2013-04-03
Chili,
I tried installing the bcmwlhigh5.inf file using the ndisgtk application.  Again I received an "Invalid Driver" message. My questions are as follows:

1) Did I attempt to install the correct file? 
2) Also I am wondering if I installed and loaded ndiswrapper properly.  Is there a command that I can run to confirm proper installion and loading of ndiswrapper?
  

I have run the following commands:

ndiswrapper -l
dmesg|grep ndis


My results are as follows:

dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
bcmwlhigh5 : invalid driver!
dzdb@dzdb-System-Product-Name:~$


 281.914818] ndiswrapper version 1.57 loaded (smp=yes,preempt=no)
[  481.052339]  [<f927d331>]load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[  481.052384]  [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0[ndiswrapper]
[  481.052451]  [<f928b8ee>]wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  481.052639]  [<f927e6cd>] loader_init+0x9d/0x130[ndiswrapper]
[  481.052670]  [<f928cf47>] ?wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  481.052700]  [<f9292c31>] ? wrapndis_init+0x41/0x50[ndiswrapper]
[  481.052726]  [<f9201077>] wrapper_init+0x77/0x1000[ndiswrapper]
[  601.052317]  [<f927d331>]load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[  601.052361]  [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0[ndiswrapper]
[  601.052429]  [<f928b8ee>]wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  601.052617]  [<f927e6cd>] loader_init+0x9d/0x130[ndiswrapper]
[  601.052648]  [<f928cf47>] ?wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  601.052679]  [<f9292c31>] ? wrapndis_init+0x41/0x50[ndiswrapper]
[  601.052704]  [<f9201077>] wrapper_init+0x77/0x1000[ndiswrapper]
[  721.052342]  [<f927d331>]load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[  721.052388]  [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0[ndiswrapper]
[  721.052456]  [<f928b8ee>]wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  721.052646]  [<f927e6cd>] loader_init+0x9d/0x130[ndiswrapper]
[  721.052677]  [<f928cf47>] ?wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  721.052708]  [<f9292c31>] ? wrapndis_init+0x41/0x50[ndiswrapper]
[  721.052734]  [<f9201077>] wrapper_init+0x77/0x1000[ndiswrapper]
[  841.052328]  [<f927d331>]load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[  841.052371]  [<f928aebf>]wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[  841.052439]  [<f928b8ee>]wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  841.052627]  [<f927e6cd>] loader_init+0x9d/0x130[ndiswrapper]
[  841.052658]  [<f928cf47>] ?wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  841.052689]  [<f9292c31>] ? wrapndis_init+0x41/0x50[ndiswrapper]
[  841.052715]  [<f9201077>] wrapper_init+0x77/0x1000[ndiswrapper]
[  961.052336]  [<f927d331>]load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[  961.052381]  [<f928aebf>]wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[  961.052448]  [<f928b8ee>]wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  961.052637]  [<f927e6cd>] loader_init+0x9d/0x130[ndiswrapper]
[  961.052668]  [<f928cf47>] ?wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  961.052699]  [<f9292c31>] ? wrapndis_init+0x41/0x50[ndiswrapper]
[  961.052725]  [<f9201077>] wrapper_init+0x77/0x1000[ndiswrapper]
[ 1081.052353] [<f927d331>] load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[ 1081.052399] [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[ 1081.052467] [<f928b8ee>] wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1081.052656] [<f927e6cd>] loader_init+0x9d/0x130 [ndiswrapper]
[ 1081.052687] [<f928cf47>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1081.052717] [<f9292c31>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1081.052743] [<f9201077>] wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1201.052338] [<f927d331>] load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[ 1201.052383] [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[ 1201.052451] [<f928b8ee>] wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1201.052640] [<f927e6cd>] loader_init+0x9d/0x130 [ndiswrapper]
[ 1201.052672] [<f928cf47>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1201.052702] [<f9292c31>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1201.052728] [<f9201077>] wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1321.052327] [<f927d331>] load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[ 1321.052371] [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[ 1321.052439] [<f928b8ee>] wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1321.052628] [<f927e6cd>] loader_init+0x9d/0x130 [ndiswrapper]
[ 1321.052660] [<f928cf47>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1321.052690] [<f9292c31>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1321.052716] [<f9201077>] wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1441.052336] [<f927d331>] load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[ 1441.052380] [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[ 1441.052448] [<f928b8ee>] wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1441.052635] [<f927e6cd>] loader_init+0x9d/0x130 [ndiswrapper]
[ 1441.052667] [<f928cf47>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1441.052697] [<f9292c31>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1441.052723] [<f9201077>] wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1561.052335] [<f927d331>] load_wrap_driver+0x101/0x1b0 [ndiswrapper]
[ 1561.052380] [<f928aebf>] wrap_pnp_start_device+0x2f/0x2c0 [ndiswrapper]
[ 1561.052447] [<f928b8ee>] wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1561.052635] [<f927e6cd>] loader_init+0x9d/0x130 [ndiswrapper]
[ 1561.052666] [<f928cf47>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1561.052697] [<f9292c31>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1561.052723] [<f9201077>] wrapper_init+0x77/0x1000 [ndiswrapper]
dzdb@dzdb-System-Product-Name:~$

---

### Post by chili555 on 2013-04-03
I am pretty confident that the .inf file is correct. It says, in part:> ;-----------------------------------------------------------------
; x86 - Win2K, WinXP
;
[Cisco]
	%Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_[COLOR="#FF0000"]13B1[/COLOR]&PID_[COLOR="#FF0000"]0039[/COLOR]
	%Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A
   
;-----------------------------------------------------------------I've highlighted your device ID. Also, as you can see, it is for XP and x86, also known as 32-bit which I read above is what you've installed. 

I suggest you do as I previously suggested:> If you wish to continue to try ndiswrapper, I think the next step is to download and compile the latest version of ndiswrapper. [http://ubuntuforums.org/showthread.php?t=1695036&page=15&p=12573923#post12573923](http://ubuntuforums.org/showthread.php?t=1695036&page=15&p=12573923#post12573923)

---

### Post by DZDB on 2013-04-04
**Installing Ndiswrapper 1.58**
 
 
Chili555,
 
Per post #109 you recommended that I install ndiswrapper 1.58.
 
For me (I have two kids ages 5 and 3) to use a temporary Ethernet connection is a time consuming and major event.  So I want to ensure that my instructions to install ndiswrapper 1.58 are “fairly” complete and accurate.  I also have a few questions which are imbedded in my steps.
 

[LIST=1]
[*]Hook up the Ethernet cord.  Then go to the terminal and type the following code:
[/LIST]
 
sudo apt-get install linux-headers-generic build-essential
 
 

[LIST=1]
[*]Go here and download the 1.58 tar.gz and drag and drop it to your desktop so we can find it.  
[/LIST]
 
[COLOR=#ff0000]I’m not sure what you mean by “go here”?[/COLOR][COLOR=#ff0000]
 
How does one drag and drop the 1.58 tar.gz from the terminal to the desktop?[/COLOR][COLOR=#ff0000]
[/COLOR] 
 

[LIST=1]
[*]Go to the terminal and run the following codes:
[/LIST]
 
cd Desktop/nidiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
 
 

[LIST=1]
[*]In addition, to load (or attach to Kernel?) run the following code:
[/LIST]
 
sudo modprobe ndiswrapper
 

[LIST=1]
[*]Remove Ethernet cord
[/LIST]
 

[LIST=1]
[*]Insert usb adapter
[/LIST]
 
 

[LIST=1]
[*]Using the ndisgtk application (a gui) load either the netrtwlanu driver (for the Netgear N150 usb adapter) or the bcmwlhigh5.ini driver (for the Linksys N300 usb adapter)
[/LIST]
 
Hopefully I receive a “Driver Installed” message as opposed “Invalid Driver” message.
 
 
[COLOR=#ff0000]Are my steps correct?[/COLOR]

---

### Post by chili555 on 2013-04-04
Your steps are correct.> I’m not sure what you mean by “go here”?That means find and download the needed package at the link I provided.

> How does one drag and drop the 1.58 tar.gz from the terminal to the desktop?
Not with the terminal. People have downloads set in Firefox to go all sorts of places; Downloads, Desktop, /home/user, and probably more that I haven't discovered. Then, when it's time to install something, they complain that they can't find it in the terminal and post to ask *ME*, of all people, where it went!!! If your Firefox preferences are not set for downloads to go to Desktop, you can drag and drop the file to Desktop as you will see attached. In this way, we all can find and work on the file because we know it's at Desktop because we put it there.

Also, be sure, once the file is on your Desktop, to right-click it and select 'Extract Here.'> Hopefully I receive a “Driver Installed” message as opposed “Invalid Driver” message.May the Force be with us!

---

### Post by DZDB on 2013-04-05
Chili,

First I went to the terminal and ran the following code:

sudo apt-get install linux-headers-generic build-essential

The results are as follows:

dzdb@dzdb-System-Product-Name:~$ sudo apt-get installlinux-headers-generic build-essential
[sudo] password for dzdb:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
The following packages were automatically installed and areno longer required:
 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
 linux-headers-3.2.0-38-generic linux-headers-generic
0 upgraded, 2 newly installed, 0 to remove and 343 notupgraded.
Need to get 982 kB of archives.
After this operation, 11.2 MB of additional disk space willbe used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/precise-updates/main](http://us.archive.ubuntu.com/ubuntu/precise-updates/main) linux-headers-3.2.0-38-generic i386 3.2.0-38.61 [980 kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/mainlinux-headers-generic i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/mainlinux-headers-generic i386 3.2.0.38.46
  404  Not Found [IP: 91.189.92.200 80]
Fetched 980 kB in 0s (1,600 kB/s)
Failed to fetchhttp://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.38.46_i386.deb  404 Not Found [IP: 91.189.92.200 80]
E: Unable to fetch some archives, maybe run apt-get update ortry with --fix-missing?
dzdb@dzdb-System-Product-Name:~$

**[COLOR=#ff0000]It appears that there are some errors.  Am I correct?[/COLOR]**



Per your post 111, I then dragged and dropped your attached file to the desktop of my computer.  I accomplished this by left clicking on the attachment and then moving the attachment file from the Ubuntu Forum website to my Desktop.  I then unclicked the mouse.  Once on my desktop, I then right-clicked the attached file. Unfortunately I never saw an option for "Extract Here".

**[COLOR=#ff0000]Why didn't I ever see the "Extract Here" option?[/COLOR]**
 
Some more information which may be pertinent:

Name: Size 149.9 KB
Type: Unknown
Size: Unknown


I then went to the terminal and attempted to do the following:
 
cd Desktop/nidiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit


My output is as follows:

dzdb@dzdb-System-Product-Name:~$ cd Desktop/nidiswrapper-1.58
bash: cd: Desktop/nidiswrapper-1.58: No such file ordirectory
dzdb@dzdb-System-Product-Name:~$ sudo su
[sudo] password for dzdb:
root@dzdb-System-Product-Name:/home/dzdb# make
make: *** No targets specified and no makefile found.  Stop.
root@dzdb-System-Product-Name:/home/dzdb# cdDesktop/nidiswrapper-1.58
bash: cd: Desktop/nidiswrapper-1.58: No such file ordirectory
root@dzdb-System-Product-Name:/home/dzdb# make install
make: *** No rule to make target `install'.  Stop.
root@dzdb-System-Product-Name:/home/dzdb#

[B][COLOR=#ff0000]I now see that I made a mistake with:

cd Desktop/nidiswrapper-1.58

it should be:

cd Desktop/ndiswrapper-1.58[/COLOR][/B]

---

### Post by chili555 on 2013-04-05
> It appears that there are some errors. Am I correct?Yes, and until they are resolved, there is no need to proceed; all succeeding steps will be errors as well.> Get:1 [http://us.archive.ubuntu.com/ubuntu/...e-updates/main](http://us.archive.ubuntu.com/ubuntu/...e-updates/main) linux-headers-3.2.0-38-generic i386 3.2.0-38.61 [980 kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/mainlinux-headers-generic i386 3.2.0.38.46
404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/mainlinux-headers-generic i386 3.2.0.38.46
404 Not Found [IP: 91.189.92.200 80]Evidently, one of the repositories was either temporarily unavailable or maybe unavailable from your country. I'd try again:```
sudo apt-get install --reinstall linux-headers-generic 
sudo apt-get install --reinstall build-essential
```Then proceed. If the repository still can't be found, I'd try other locales under Software Sources. See here. [http://i.stack.imgur.com/kmKL6.png](http://i.stack.imgur.com/kmKL6.png)

>  I then right-clicked the attached file. Unfortunately I never saw an option for "Extract Here".I'm not quite sure I understand why not. Please see attached. Again, it a step fails; that is, you are unable to extract the package, until it is resolved, there is no need to proceed; all succeeding steps will be errors as well.

---

### Post by DZDB on 2013-04-05
Chili,

Regarding why the code "sudo apt-get install linux-headers-generic build-essential" didn't install properly. I reside in Maryland, U.S. I believe we live in the same country. So it should have loaded properly. The second link appears to be better. I am at work right now so I cannot use the ultimate test which is extracting the file to my Ubunutu computer located in my home. However when I double click on the attachment file I see the "Extract Here" option.

I'm starting to get very frustrated. I will probably try again tomorrow morning starting with the codes:


sudo apt-get install --reinstall linux-headers-generic
 sudo apt-get install --reinstall build-essential

If these steps are accomplished successfully then I will proceed.

---

### Post by chili555 on 2013-04-05
>  I reside in Maryland, U.S. I believe we live in the same country. So it should have loaded properly.Quite correct. That doesn't mean, however, that the US repositories weren't temporarily out of service.

---

### Post by DZDB on 2013-04-08
Chili,

Yes, maybe the US repositories were temporarily out of service.  I ran the following commands:

[COLOR=#000000]sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall build-essential


My results are as follows:

[/COLOR]dzdb@dzdb-System-Product-Name:~$ sudo apt-get install--reinstall linux-headers-generic
[sudo] password for dzdb:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and areno longer required:
 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
 linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic
The following NEW packages will be installed:
 linux-headers-3.2.0-39 linux-headers-3.2.0-39-genericlinux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 376 notupgraded.
Need to get 12.7 MB of archives.
After this operation, 67.5 MB of additional disk space willbe used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/precise-updates/main](http://us.archive.ubuntu.com/ubuntu/precise-updates/main) linux-headers-3.2.0-39 all 3.2.0-39.62 [11.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/precise-updates/main](http://us.archive.ubuntu.com/ubuntu/precise-updates/main) linux-headers-3.2.0-39-generic i386 3.2.0-39.62 [981 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/precise-updates/main](http://us.archive.ubuntu.com/ubuntu/precise-updates/main) linux-headers-generic i386 3.2.0.39.47 [2,590 B]
Fetched 12.7 MB in 1s (6,451 kB/s)                 
Selecting previously unselected packagelinux-headers-3.2.0-39.
(Reading database ... 170234 files and directories currentlyinstalled.)
Unpacking linux-headers-3.2.0-39 (from.../linux-headers-3.2.0-39_3.2.0-39.62_all.deb) ...
Selecting previously unselected packagelinux-headers-3.2.0-39-generic.
Unpacking linux-headers-3.2.0-39-generic (from.../linux-headers-3.2.0-39-generic_3.2.0-39.62_i386.deb) ...
Selecting previously unselected packagelinux-headers-generic.
Unpacking linux-headers-generic (from.../linux-headers-generic_3.2.0.39.47_i386.deb) ...
Setting up linux-headers-3.2.0-39 (3.2.0-39.62) ...
Setting up linux-headers-3.2.0-39-generic (3.2.0-39.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
Setting up linux-headers-generic (3.2.0.39.47) ...
dzdb@dzdb-System-Product-Name:~$ sudo apt-get install--reinstall build-essential
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and areno longer required:
 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and376 not upgraded.
Need to get 0 B/5,796 B of archives.
After this operation, 0 B of additional disk space will beused.
(Reading database ... 192535 files and directories currentlyinstalled.)
Preparing to replace build-essential 11.5ubuntu2.1 (using.../build-essential_11.5ubuntu2.1_i386.deb) ...
Unpacking replacement build-essential ...
Setting up build-essential (11.5ubuntu2.1) ...
dzdb@dzdb-System-Product-Name:~$



[COLOR=#000000]


[/COLOR]
Did the commands run successfully? It looks like it wasn't successfull since I see these get: 1, get: 2 and get: 3 requests.  Yesterday afternoon I returned both the Netgear N150 and the Linksys N300 usb adpaters back to Radio Shack.  Yesterday was the last day that could return the usb adapters and still get a full refund.  If my commands did run successfully I will then repurchase the Netgear N150 usb adapter. 

Some more background information.  I will have an additional Verizon FIOS cable line installed which will be for the Linux Ubuntu computer.  This will facilitate the task of trouble shooting.  Moving the Ubuntu computer, along with the monitor, keyboard, and mouse, to the office, re-plugging all wires back in (including the Verizon FIOS cable line) proved to be a monumental tasks.  The additional cable line will probably will be installed within two weeks.  So if my commands didn't work, I will then regroup and try again.  I have not given up. I have the feeling the installing other types of drives, such as printers, will also prove challenging.  However I like the fact that Linux is free.  I also intent to build more linux computers.

If I were to go to the Ubuntu Software centers and download ndiswrapper, would version 1.58 download?

---

### Post by chili555 on 2013-04-08
> Did the commands run successfully? Yes, perfectly.> I see these get: 1, get: 2 and get: 3 requests.Yes, but not what you saw before: Failed to fetch ... 404 Not Found. As well, you see this indicating they were installed after they were downloaded:> Setting up linux-headers-3.2.0-39 (3.2.0-39.62) ...
Setting up linux-headers-3.2.0-39-generic (3.2.0-39.62) ...
Setting up build-essential (11.5ubuntu2.1) ...> If I were to go to the Ubuntu Software centers and download ndiswrapper, would version 1.58 download? Nope. You'd get the older and possibly faulty 1.57. I suggest you download 1.58 from here: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)  If you are no longer connected to the FIOS, you could easily download the package on any other computer on a USB stick, insert it in your Ubuntu computer, drag and drop it from the USB stick to your desktop and then right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/ndiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
```I suspect it will all go well, but if there is any error or warning, post it here.

---

### Post by DZDB on 2013-04-08
Chili,

I am still connected to FIOS.  In additon you telling my sudo apt-get install commands ran successfully has inspired me.  I will run the commands you recommended tomorrow morning.

---

### Post by DZDB on 2013-04-09
Chili,

I received an error message with the first command which is as follows:


cd Desktop/ndiswrapper-1.58My results are as follows:dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
bash: cd: Desktop/ndiswrapper-1.58: No such file or directory
dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
bash: cd: Desktop/ndiswrapper-1.58: No such file or directory
dzdb@dzdb-System-Product-Name:~$

---

### Post by chili555 on 2013-04-09
> **DZDB said:**
> Chili,

I received an error message with the first command which is as follows:


cd Desktop/ndiswrapper-1.58My results are as follows:dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
bash: cd: Desktop/ndiswrapper-1.58: No such file or directory
dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
bash: cd: Desktop/ndiswrapper-1.58: No such file or directory
dzdb@dzdb-System-Product-Name:~$Did you get the ndiswrapper tar.gz to your desktop? Did you right-click it and select 'Extract Here?' How could it not be there if you put it there? What does this tell us?```
cd Desktop
ls
```

---

### Post by DZDB on 2013-04-09
Chili,

No, I never did get the ndiswrapper tar.gaz on by desktop.  I will do that tomorrow morning.  Then run the commands.  What exactly is the ndiswrapper tar.gaz.  The first link that you sent me I was unable to get it on my Ubuntu PC desktop.  On the second link, when I double click the image, I do see the "Extract here" option.  Things should work better tomorrow morning.

---

### Post by chili555 on 2013-04-09
Go here: [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) 

Download ndiswrapper-1.58.tar.gz. Get it to your desktop. Right-click the package and select 'Extract Here.' Then open a terminal and do:```
cd Desktop/ndiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
```Is there any error? If so, post it here and we'll troubleshoot.

If there is no error, your wireless should be working. It may take a reboot.

---

### Post by DZDB on 2013-04-10
Chili,

I downloaded ndiswraqpper, got it to my desktop, and then extracted it. I then ran the commands per your post #122 instructions. I believe everything ran successfully. My results are as follows:

dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
dzdb@dzdb-System-Product-Name:~/Desktop/ndiswrapper-1.58$sudo su
[sudo] password for dzdb:
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58#make
make -C utils
make[1]: Entering directory`/home/dzdb/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory`/home/dzdb/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory`/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.2.0-38-generic-paeM=/home/dzdb/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory`/usr/src/linux-headers-3.2.0-38-generic-pae'
LD /home/dzdb/Desktop/ndiswrapper-1.58/driver/built-in.o
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/crt_exports.h
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/hal_exports.h
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
MKEXPORT/home/dzdb/Desktop/ndiswrapper-1.58/driver/usb_exports.h
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/crt.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/hal.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/loader.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pe_linker.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pnp.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/proc.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapmem.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapper.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/usb.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/divdi3.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
Building modules,stage 2.
MODPOST 1 modules
CC /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory`/usr/src/linux-headers-3.2.0-38-generic-pae'
make[1]: Leaving directory`/home/dzdb/Desktop/ndiswrapper-1.58/driver'
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58#make install
make -C driver install
make[1]: Entering directory`/home/dzdb/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.2.0-38-generic-pae/misc
install -m 0644 ndiswrapper.ko/lib/modules/3.2.0-38-generic-pae/misc
/sbin/depmod -a 3.2.0-38-generic-pae
modmake[1]: Leaving directory`/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory`/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory`/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58#modprobe ndiswrapper
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58#exit
exit
dzdb@dzdb-System-Product-Name:~/Desktop/ndiswrapper-1.58$


Since I returned the Netgear N150 micro wireless usb adpater, I need to go to Staples and purchase another one.

I believe my remaining steps are as follows:

1) Purchase the Netgear N150 micro wireless usb adapter.
2) Insert the usb adapter in my Ubuntu 12.04 computer.
3) Use the ndisgtk application to install the netrtwlanu driver (hopefully I get a driver installed message).

4) Go to the terminal and do the following commands (otherwise I will lose the connection on the reboot):


sudo su
echo ndiswrapper >> /etc/modules
exit

5) At this point I should be able to connect to the internet.


My question are as follows:
1) Based on my results did I installed ndiswrapper 1.58 successfully?
2) Are my remaining steps correct?

---

### Post by chili555 on 2013-04-10
> 1) Based on my results did I installed ndiswrapper 1.58 successfully?Yes, indeed! You are well on your way to being a driver dawg!> 2) Are my remaining steps correct? Almost perfect. I suggest you add one step so that the sequence is:

1) Purchase the Netgear N150 micro wireless usb adapter.
2) Insert the usb adapter in my Ubuntu 12.04 computer.
3) Use the ndisgtk application to install the netrtwlanu driver (hopefully I get a driver installed message).
[COLOR="#FF0000"]3a) Do the following command:

sudo modprobe ndiswrapper

If it's already loaded, it won't hurt; if it's *not* loaded, it will be.
[/COLOR]
4) Go to the terminal and do the following commands (otherwise I will lose the connection on the reboot):


sudo su
echo ndiswrapper >> /etc/modules
exit

You are doing well, I have my fingers crossed!

---

### Post by DZDB on 2013-04-10
Chili,

I will run the following commands:


3a) sudo modprobe ndiswrapper


4)  sudo su
echo ndiswrapper >> /etc/modules
exit

When I run the above commands in the terminal, do I need to have the Verizon FIOS cable plugged in?

---

### Post by chili555 on 2013-04-10
> **DZDB said:**
> Chili,

I will run the following commands:


3a) sudo modprobe ndiswrapper


4)  sudo su
echo ndiswrapper >> /etc/modules
exit

When I run the above commands in the terminal, do I need to have the Verizon FIOS cable plugged in?Not at all. I suggest it be detached.

---

### Post by DZDB on 2013-04-11
Chli,

The results are disappointing.

I tried to install the netrtwlanu.inf driver.  I received an "Invalid driver" error message.  See results for the command ndiswrapper -l below:

dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
netrtwlanu : invalid driver!
dzdb@dzdb-System-Product-Name:~$


I used the Ubuntu software center to install the ndisgtk application.  Is my ndisgtk application buggy? Do I need to reinstall the ndisgtk application using the terminal?


I also ran the following:

dmesg | grep ndis

My results are as follows:

dzdb@dzdb-System-Product-Name:~$ dmesg|grep ndis
[  131.888106]ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  131.911968] usbcore:registered new interface driver ndiswrapper
dzdb@dzdb-System-Product-Name:~$

It appears that ndiswrapper 1.57 is loaded and ndiswrapper 1.58 never loaded.  Very confusing.  What happened? Do I need to reinstall Ubuntu 12.04 and then blacklist the native drivers, install ndisgtk and ndiswrapper 1.58 through the terminal?

So what are my next steps?

---

### Post by chili555 on 2013-04-11
Ouch. When you installed ndisgtk through the Software Center, you over-wrote all the fine work you did compiling 1.58. If I missed that subtlety above, I apologize. Please do:```
sudo apt-get remove --purge ndisgtk
sudo apt-get remove --purge ndiswrapper*
``` That removes everything you now have installed so we can start fresh. Now do:```
cd Desktop/ndiswrapper-1.58
sudo su
make clean
make
make install

```If you get this at the end, it installed correctly and there is no need to post everything for a confirmation:> install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory`/home/dzdb/Desktop/ndiswrapper-1.58/utils'Then proceed:```
cd
ndiswrapper -i Desktop/driver_folder/netrtwlanu.inf 
```...where 'driver_folder' is the folder containing the Windows XP driver files. Next do:```
modprobe ndiswrapper
exit
ndiswrapper -l
```Errors, warnings?

---

### Post by DZDB on 2013-04-11
Chili,

I installed the ndisgtk application about a month ago.  Did that still over wrote the fine work I did installing ndiswrapper 1.58?

---

### Post by chili555 on 2013-04-11
> **DZDB said:**
> Chili,

I installed the ndisgtk application about a month ago.  Did that still over wrote the fine work I did installing ndiswrapper 1.58?I'm not quite sure, but I suspect the version of ndisgtk you installed calls on it's brothers the 1.57 version. That's why I'd like to remove it and use the old-school methods: sudo ndiswrapper -i.

What does this tell us?```
ndiswrapper -v
```

---

### Post by DZDB on 2013-04-12
Chili,

I am going to reinstall Ubuntu 12.04 so that I have a clean slate.  I will then blacklist the native drivers, install ndisgtk and ndiswrapper 1.58 through the terminal? Finally I will load the netrtwlanu driver.  Over the weekend I will work on detail step by step procedure and then I will post it here on Monday or Tuesday.  You can then review it and then edit as necessary.

This process my take more time, but I think in the long run it will be better for me in the event that I have a problem in the future.  I think it will also benefit our viewer/readers.  They will be able to see the entire detail step by step process of installing the Netgear N150 micro usb adapter from start to finish.

---

### Post by chili555 on 2013-04-12
> **DZDB said:**
> Chili,

I am going to reinstall Ubuntu 12.04 so that I have a clean slate.  I will then blacklist the native drivers, install ndisgtk and ndiswrapper 1.58 through the terminal? Finally I will load the netrtwlanu driver.  Over the weekend I will work on detail step by step procedure and then I will post it here on Monday or Tuesday.  You can then review it and then edit as necessary.

This process my take more time, but I think in the long run it will be better for me in the event that I have a problem in the future.  I think it will also benefit our viewer/readers.  They will be able to see the entire detail step by step process of installing the Netgear N150 micro usb adapter from start to finish.I will look forward to your step-by-step. I'd leave ndisgtk out of the process and install the driver the old way using only ndiswrapper-1.58.

---

### Post by DZDB on 2013-04-15
Chili,
My step-by-step instructions are below.  Please review them [COLOR=#000000]and edit as necessary.  Tomorrow morning I will attempt to install the Netgear G54/N150 usb adapter. [/COLOR][B]



Installing Netgear G54/N150 USB Adapter on Ubuntu 12.04[/B]
**                        (From Start to Finish)**
 
 
**1)    ****_Reinstall Ubunto 12.04 _**
This I know how to do
 
Note: Plug the Verizon FIOS cable when installing Ubunto 12.04
 
 
**2)    ****_Blacklist the Native Drivers_**
Go to the terminal:
_Code:_
sudo su
echo “blacklist rtl8192cu” >> /etc/modprobe.d/blacklist.conf
exit
 
 
**3)    ****_Install ndiswrapper 1.58_**
Go to the terminal:
_Code:_
sudo apt-get install linux-headers-generic build-essential
 
 
_Download nidiswrapper-1.58.tar.gz_
[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)
 
Move file to desktop.  Right-click the package and select: “Extract Here.”
 
 
Go to the terminal:
_Code:_
cd Desktop/ndiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
 
 
**4)    ****Check load status of ndiswrapper 1.58**
Go to the terminal:
_Code:_
dmesg | grep ndis
 
 
**5)    ****_Remove Verizon FIOS cable_**
 
 
**6)    ****_Insert the Netgear G54/N150 micro USB adapter in USB port_**
 
 
**7)    ****_Install the netrtwlanu driver_**
Download netrtwlanu.inf file to the desktop
 
Go to the terminal:
_Code:_
sudo ndiswrapper –d 0846:9041 netrtwlanu
 
 
Note: For our readers, the netrtwlanu.inf file is attached in this post.
 
 
 
**8)    ****_Check installation status of the netrtwlanu driver_**
 
Go to the terminal:
Code:
ndiswrapper –l
 
Note: At this point one should be able to connect to the internet.
 
 
**9)    ****_Save the settings in the prior step_**
 
Go to the terminal:
_Code:_
sudo su
echo ndiswrapper >> /etc/modules
exit
 
Note: failure to do this step will cause one to lose connection to the internet after rebooting

---

### Post by chili555 on 2013-04-15
I would amend this slightly:> 7) Install the netrtwlanu driver
Download netrtwlanu.inf file *to the desktop*

Go to the terminal:
```
cd Desktop/WinXPlater
sudo ndiswrapper &#8211;d 0846:9041 netrtwlanu
```
Otherwise, it looks awesome! May the Force be with you!

---

### Post by DZDB on 2013-04-16
Chili,

Overall I believe I was unsuccessful. I do think I ran the command "sudo apt-get install linux-headers-generic build-essential" successfully.  Am I correct? My results are as follows:

dzdb@dzdb-System-Product-Name:~$ sudo apt-get install linux-headers-generic build-essential
[sudo] password for dzdb:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages were automatically installed and are no longer required:
linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
libstdc++6-4.6-dev libtimedate-perl linux-headers-3.2.0-40-generic
Suggested packages:
debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
libstdc++6-4.6-doc
The following NEW packages will be installed:
build-essential dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
libstdc++6-4.6-dev libtimedate-perl linux-headers-3.2.0-40-generic
linux-headers-generic
0 upgraded, 13 newly installed, 0 to remove and 369 not upgraded.
Need to get 10.2 MB of archives.
After this operation, 38.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.1 [180 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.1 [469 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main build-essential i386 11.5ubuntu2.1 [5,796 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main fakeroot i386 1.18.2-1 [87.9 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-40-generic i386 3.2.0-40.64 [978 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic i386 3.2.0.40.48 [2,568 B]
Fetched 10.2 MB in 1s (5,900 kB/s) 
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 169078 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-40-generic.
Unpacking linux-headers-3.2.0-40-generic (from .../linux-headers-3.2.0-40-generic_3.2.0-40.64_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.40.48_i386.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.1) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.1) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.2.0-40-generic (3.2.0-40.64) ...
Setting up linux-headers-generic (3.2.0.40.48) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
dzdb@dzdb-System-Product-Name:~$





Here my pc got hung up over the "modprobe ndiswrapper" command. I let the pc run for about 15 minutes there was still no progress. I finally just type "exit' and closed the terminal. Normally how long does the "modprobe ndiswrapper" normally take? 



dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
dzdb@dzdb-System-Product-Name:~/Desktop/ndiswrapper-1.58$ sudo su
[sudo] password for dzdb:
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# make
make -C utils
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.2.0-40-generic-pae M=/home/dzdb/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-40-generic-pae'
LD /home/dzdb/Desktop/ndiswrapper-1.58/driver/built-in.o
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/crt_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/hal_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/usb_exports.h
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/crt.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/hal.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/loader.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pe_linker.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pnp.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/proc.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapmem.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapper.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/usb.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/divdi3.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
Building modules, stage 2.
MODPOST 1 modules
CC /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-40-generic-pae'
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# make install
make -C driver install
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.2.0-40-generic-pae/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.2.0-40-generic-pae/misc
/sbin/depmod -a 3.2.0-40-generic-pae
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# modprobe ndiswrapper
exit

I also ran the command "dmesg | grep ndis". I received a "ndiswrapper 1.58 not found" error message.

---

### Post by chili555 on 2013-04-16
> I do think I ran the command "sudo apt-get install linux-headers-generic build-essential" successfully. Am I correct? Yes. Compiling ndiswrapper also went smoothly.> Normally how long does the "modprobe ndiswrapper" normally take?Less than a second. 

Please reboot. Then run and post:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndiswrapper
```I feel like we're really close!

---

### Post by DZDB on 2013-04-17
Chili,

After I reinstalled Ubuntu 12.04, I couldn't shutdown.  I kept getting the password screen.  After I put in my password, I then went forward to my main desktop screen.  It was weird.  I tried fix the problem.  I was unsuccessful and then I discovered that I couldn't connect to the internet even with the Verizon FIOS cable plug in.  So on Friday morning I will reinstall Ubuntu 1204 and go through my steps.  Hopefully this time I don't get stuck at the "modprobe ndiswrapper" command.

---

### Post by chili555 on 2013-04-17
>  So on Friday morning I will reinstall Ubuntu 1204 and go through my steps. Hopefully this time I don't get stuck at the "modprobe ndiswrapper" command. I hope not. I will look forward to a good report!

---

### Post by DZDB on 2013-04-19
Chili,

My results were mixed. I successfully blacklisted the native drivers and downloaded ndiswrapper 1.58. Unfortunately I got hung up at the "modprobe ndiswrapper" command again. I was also unable to do the command "cd Desktop/WinXPlater.

My results are as follows:

[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo su[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]root@dzdb-System-Product-Name:/home/dzdb# echo "blacklist rtl8192cu">>/etc/modprobe.d/blacklist.conf[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]root@dzdb-System-Product-Name:/home/dzdb#[/COLOR][/SIZE][/FONT]

dzdb@dzdb-System-Product-Name:~$ cd Desktop/ndiswrapper-1.58
dzdb@dzdb-System-Product-Name:~/Desktop/ndiswrapper-1.58$ sudo su
[sudo] password for dzdb:
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# make
make -C utils
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.2.0-40-generic-pae M=/home/dzdb/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-40-generic-pae'
LD /home/dzdb/Desktop/ndiswrapper-1.58/driver/built-in.o
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/crt_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/hal_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
MKEXPORT /home/dzdb/Desktop/ndiswrapper-1.58/driver/usb_exports.h
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/crt.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/hal.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/loader.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pe_linker.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/pnp.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/proc.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/rtl.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapmem.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapndis.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/wrapper.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/usb.o
CC [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/divdi3.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
Building modules, stage 2.
MODPOST 1 modules
CC /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
LD [M] /home/dzdb/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-40-generic-pae'
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# make install
make -C driver install
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.2.0-40-generic-pae/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.2.0-40-generic-pae/misc
/sbin/depmod -a 3.2.0-40-generic-pae
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/dzdb/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@dzdb-System-Product-Name:/home/dzdb/Desktop/ndiswrapper-1.58# modprobe ndiswrapper


dzdb@dzdb-System-Product-Name:~$ dmesg|grep ndis
[ 1483.831222] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 1681.104324] [<f926f543>] load_wrap_device+0x193/0x1f0 [ndiswrapper]
[ 1681.104363] [<f927c8d4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[ 1681.104570] [<f926f6b5>] loader_init+0x85/0x130 [ndiswrapper]
[ 1681.104604] [<f927e0c7>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1681.104636] [<f9283db1>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1681.104664] [<f8c99077>] wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1801.104346] [<f926f543>] load_wrap_device+0x193/0x1f0 [ndiswrapper]
[ 1801.104386] [<f927c8d4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[ 1801.104599] [<f926f6b5>] loader_init+0x85/0x130 [ndiswrapper]
[ 1801.104632] [<f927e0c7>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1801.104665] [<f9283db1>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1801.104693] [<f8c99077>] wrapper_init+0x77/0x1000 [ndiswrapper]
dzdb@dzdb-System-Product-Name:~$


[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ cd Desktop/WinXPlater[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]bash: cd: Desktop/WinXPlater: No such file or directory[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ sudo ndiswrapper -d 0846:9041 netrtwlanu[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][sudo] password for dzdb:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]ls: cannot access /etc/ndiswrapper/netrtwlanu/: No such file or directory[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]driver 'netrtwlanu' is not installed (properly)![/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$ cd Desktop/WinXPlater.zip[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]bash: cd: Desktop/WinXPlater.zip: Not a directory[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]dzdb@dzdb-System-Product-Name:~$[/COLOR][/SIZE][/FONT]


I left the "sudo apt-get install linux-headers-generic build-essential" results file at home. But since ndiswrapper 1.58 installed (see results for command "dmesg|grep ndis"), the "sudo apt-get install linux-headers-generic build-essential" results must have been successful.


My questions are as follows:
1) Why am I getting stuck on the "modprobe ndiswrapper" command?

2) I downloaded the [FONT=Times New Roman][SIZE=3][COLOR=#000000]WinXPlater folder[/COLOR][/SIZE][/FONT] to the Desktop. So why didn't the "cd Desktop/WinXPlater" command work? Is it because it was on my Desktop in a zip format (i.e. WinXPlater.zip)? If so then do I need to unzip the folder? 

3) The same thing happened again. I couldn't shutdown. I kept getting the [COLOR=#417394]password[/COLOR] screen The background was a red screen with white dots. After I put in my [COLOR=#417394]password[/COLOR], I then went forward to my main desktop screen. I received some type of message saying "Program running Gnome Settings Daemon". In order to turn off the computer I had to pull the plug. Does this have anything do to with installing ndiswrapper 1.58? The only way I can confirm this is to reinstall Ubuntu 12.04 and then shutdown. If I shutdown properly then I can say that the problem is caused by installing ndiswrapper 1.58. Anyway do you know how I can fix this problem without having to do a reinstall.

4) Provided I don't have to do a reinstall to fix the problem decribed in #3, at this point I no longer need to plug-in the Verizon FIOS cable since I have already downloaded ndiswrapper 1.58. Am I correct?

---

### Post by chili555 on 2013-04-20
> 1) Why am I getting stuck on the "modprobe ndiswrapper" command?Meaning what? Meaning the command just hangs there and the prompt never returns until you close the terminal or Ctrl+c. Or do you mean that you enter the command and press Enter and the prompt pops back immediately with no further signs of life?> 2) I downloaded the WinXPlater folder to the Desktop. So why didn't the "cd Desktop/WinXPlater" command work? Is it because it was on my Desktop in a zip format (i.e. WinXPlater.zip)? If so then do I need to unzip the folder? Yes, you need to unzip the file which you can do by right-clicking and select 'Extract Here.' A folder will appear named WinXPlater. If you open the folder, you will see the .inf and .sys files within.

I have no idea if ndiswrapper is causing the freeze. I do know that many people, many times, including me, have compiled ndiswrapper-1.58 without the very slightest issue. I suspect that pulling the power plug is probably the very *worst* way to shut down. Before I ever did that, I'd try Ctrl+Alt+F1 and see if you can get to a command prompt. Log in and do:```
sudo reboot
```If that wouldn't work, I'd hold down the power switch on the computer for a few seconds until it powers down. After you power back up, check /var/log/syslog for clues. As you can see from my snip, it is timestamped, so note the time on the computer at the time of the freeze and look at the log for the corresponding time:> Apr 20 08:13:57 Think410 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/fdefab2a82c2483a8275adfa8f127acf
Apr 20 08:17:01 Think410 CRON[4286]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 08:19:24 Think410 AptDaemon: INFO: Quitting due to inactivity
[COLOR="#FF0000"]Apr 20 **08:19:24**[/COLOR] Think410 AptDaemon: INFO: Quitting was requested
>  But since ndiswrapper 1.58 installed (see results for command "dmesg|grep ndis"), the "sudo apt-get install linux-headers-generic build-essential" results must have been successful.Quite correct. ndiswrapper compiled perfectly.

There is no need for the FIOS cable. I suggest you remove everything related to ndiswrapper, if any:```
sudo rm -rf /etc/ndiswrapper/*
```Extract the file on your desktop. Now load the .inf file:```
sudo ndiswrapper -i Desktop/WinXPlater/netrtwlanu.inf
```Is there any error or warning? If so, *STOP* and report it here. If not, now modprobe:```
sudo modprobe ndiswrapper
```Check for errors:```
dmesg | grep ndis
```Please report back so we know where to go next.

---

### Post by DZDB on 2013-04-22
Chili,

My answers to your question is as follows:

1) When I say that I am getting stuck on the "modprobe ndiswrapper" command this means that [COLOR=#000000]the command just hangs there and the prompt never returns until I close the terminal.
[/COLOR]

My questions to you are as follows:
1) Can I shutdown by using a command from the terminal such the following command?

    _Code:_
    sudo poweroff


 I guess one way to find out is just to try.


2) Why am I removing everything from ndiswrapper by using the code below? I worked so hard to compile ndiswrapper 1.58.  I guess I am missing something here.

     [COLOR=#000000][FONT=Ubuntu Mono]sudo rm -rf /etc/ndiswrapper/*
[/FONT][/COLOR]

On Tuesday morning I will try again.  Hopefully I am at least able to connect to the internet.  Hopefully in the future I will resolve my shutdown issues.

---

### Post by chili555 on 2013-04-22
```
2) Why am I removing everything from ndiswrapper by using the code below? I worked so hard to compile ndiswrapper 1.58. I guess I am missing something here.

sudo rm -rf /etc/ndiswrapper/*

```Files located in the /etc directory are configuration files, not program files. All the old netrtwlanu.inf files, the ones that were reported to be invalid, are located there. I am suggesting that we wipe the slate clean and install one hopefully known good netrtwlanu.inf file. 

The files that were built when you compiled 1.58, the program and library files are elsewhere:```
[COLOR="#FF0000"]/lib/modules[/COLOR]/3.5.0-21-generic/misc/ndiswrapper.ko
/lib/modules/3.5.0-27-generic/misc/ndiswrapper.ko
[COLOR="#FF0000"]/usr/sbin[/COLOR]/ndiswrapper
/usr/sbin/ndiswrapper-1.9
/usr/sbin/ndiswrapper-buginfo
/usr/share/doc/ndiswrapper-common
[COLOR="#FF0000"]/usr/share/doc[/COLOR]/ndiswrapper-utils-1.9
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz
etc., etc.
```...not, as you can see, in /etc.

---

### Post by DZDB on 2013-04-23
Chili,

To me everything looks good! My results are as follows:

dzdb@dzdb-System-Product-Name:~$ sudo rm -rf/etc/ndiswrapper/*
[sudo] password for dzdb:
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ sudo ndiswrapper -iDesktop/WinXPlater/netrtwlanu.inf
[sudo] password for dzdb:
installing netrtwlanu ...
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ sudo modprobe ndiswrapper
[sudo] password for dzdb:
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ dmesg|grep ndis
[  830.473307]ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  830.499848] usbcore:registered new interface driver ndiswrapper
dzdb@dzdb-System-Product-Name:~$

To add even more positive news, my computer shutdown properly.

So my steps are?

---

### Post by chili555 on 2013-04-23
Looks very good so far! What does this tell us?```
iwconfig
ndiswrapper -l
```

---

### Post by DZDB on 2013-04-23
Chili,

Before I run the "iwconfig" and "nidiswrapper -l" commands, do I need to insert the Netgear n150 usb adapter in the computer's usb port?

---

### Post by chili555 on 2013-04-23
Yes, please. If you are working on trying to get the Netgear working, then we need to have it inserted.

---

### Post by DZDB on 2013-04-24
Chili,

It appears that I am very close now.  My results are as follows:

dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
netrtwlanu : driver installed
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ iwconfig
lo        no wirelessextensions.
 
eth0      no wirelessextensions.
 
dzdb@dzdb-System-Product-Name:~$


So what are my next steps?

---

### Post by chili555 on 2013-04-24
> dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
netrtwlanu : driver installed [COLOR="#FF0000"]??device (0846:9041) present??[/COLOR]Was the device inserted at the time?? Please be sure the device is inserted. Be sure the system sees it:```
lsusb
```Be sure the module is loaded:```
sudo modprobe ndiswrapper
```Check again:```
ndiswrapper -l
```Check the log for messages:```
dmesg | grep ndis
```

---

### Post by DZDB on 2013-04-24
Chili,

The device (usb adapter) was inserted at the time I ran the commands "iwconfig" and "ndiswrapper -l"(this morning, post 147).  When I ran the command "modprobe ndiswrapper" yesterday (post #143) the device was not inserted.

---

### Post by chili555 on 2013-04-24
It doesn't help us to get the device going if it isn't inserted. Please see and follow my post just above.

---

### Post by DZDB on 2013-04-25
Chili,

I inserted the device and then ran the commands you suggested in post #148. My results are as follows:


dzdb@dzdb-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer MicroFlash Drive
Bus 005 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120for Business
Bus 006 Device 002: ID 046d:c05a Logitech, Inc. Optical MouseM90
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ sudo modprobe ndiswrapper
[sudo] password for dzdb:
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ ndiswrapper -l
netrtwlanu : driver installed
dzdb@dzdb-System-Product-Name:~$


dzdb@dzdb-System-Product-Name:~$ dmesg|grep ndis
[ 597.803141]ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 597.842521] usbcore:registered new interface driver ndiswrapper
dzdb@dzdb-System-Product-Name:~$


In addition I ran the command "iwconfig". My result is as follows:

dzdb@dzdb-System-Product-Name:~$ iwconfig
lo no wirelessextensions.

eth0 no wirelessextensions.

dzdb@dzdb-System-Product-Name:~$


So as you can see ndiswrapper 1.58 is installed and loaded and the netrtwlanu driver is also installed. However, per command "iwconfig" I have no wireless extensions. I'm pretty sure that is not a good thing. The Netgear N150 usb adapter, as per command "lsusb", is recognized though. 

So what are my next steps? Or is there nothing more you can do?

---

### Post by eralexander on 2013-05-24
Chilli, 

Could you please attach the 64-bit windows driver version for Netgear N150?

I get the following error after installing your WinXP.zip that you shared in previous posts... Thanks for your consistent follow up on this issue.

[    5.695650] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[    5.942829] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    5.942837] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netrtwlanu'
[    5.942911] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netrtwlanu'
[    5.942945] usbcore: registered new interface driver ndiswrapper
[  215.377480] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  215.377485] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netrtwlanu'
[  215.377586] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netrtwlanu'

---

### Post by kurt18947 on 2013-05-24
I'm not Chili555 but Tim Phillips has done yeoman work and produced a .deb package that seems to drive an RTL-8188CUS device perfectly.  I'm using it with an Edimax device using the same chipset.  Installing it is no more difficult than installing any other .deb package.  I use Gdebi but it's not required.    If you use Tim's package, you'll want to completely uninstall NDISwrapper first.  Here's the thread I'm referring to.  Check posts # 9 & 10.

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188cus](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188cus)

Not only does this drive the RealTek 8188CUs - and I suspect other Realtek 8188 & 819CU USB devices - but Tim has included DKMS functionality so kernel upgrades don't break the driver requiring a reinstall.  Don't forget to blacklist the 'native' drivers so they don't conflict.

---

### Post by chili555 on 2013-05-24
And I am Chili and I'm back from a temporary hiatus on Cape Cod. Please try kurt18947's excellent solution and let us hear your report. Since he has the device, he's the best resource.

---

