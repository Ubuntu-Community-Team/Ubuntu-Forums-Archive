---
title: "Need help with wireless USB dongle D-Link DWA-131"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by Pierrot Lafouine on 2012-10-22
Hi
I'm trying to install the driver for DWA-131 on Ubuntu Lucid Lynx (10.04) and Debian Squeeze.  I read this post: [_Help with D-Link DWA-131 Wireless N USB Adapter driver needed_]("http://ubuntuforums.org/showthread.php?t=1457505").

I followed the instructions (and even post my question in this thread but remained unanswered), but it look to me something changed from these instructions :

> Originally Posted by bmjbmj  
BIG WARNING!!!! Read to the end of this discussion if your kernel version is higher then Kernel 2.6.32-22 

The new drivers 2.60006.2010625 do NOT need more then download
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=) 5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true #RTL8192SU

unpacking
unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226/driver
tar -xvzf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226

Building
sudo su
make clean
make
make install

Unpacking instruction works fine, (but the driver I downloaded [_here_]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") changed version to v2.6.6.0.20120405)

Building instruction doesn't work at all, there is no 'make' file in any folder.  There is a bash file install.sh, that stop working after I entered the root password.  Any lead to make this script works ?

Thanks

---

### Post by chili555 on 2012-10-22
May we see the result of:```
cd directory/you/extracted/newfile
sudo su
./install.sh
exit
```In order to work, the new file will probably require rtl8192su to be blacklisted.

---

### Post by Pierrot Lafouine on 2012-10-22
This is the output of ./install.sh

```
./install.sh
bash: ./install.sh: Permission denied

```

This is the output of ```
sh install.sh
``` ran as root
```

root@TSP:/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405# sh install.sh 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/autoconf_rtl8712_usb_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/clean
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/config
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ifcfg-wlan0
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/autoconf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/basic_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/big_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/generic.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/little_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swab.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swabb.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/circ_buf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/cmd_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_conf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ethernet.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/farray.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/h2clbk.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/hal_init.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/if_ether.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ioctl_cfg80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ip.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mlme_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mp_custom_oid.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/nic_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_ce_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_intf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/recv_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_efuse.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/vssver.scc
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_byteorder.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_debug.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_eeprom.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ht.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_io.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_query.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_rtl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_set.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_led.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_phy_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_pwrctrl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_qos.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_security.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_sme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtw_android.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sta_info.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_vendor_req.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/version.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wlan_bssdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/xmit_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Kconfig
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Makefile
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/rtw_android.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/rtl871x_pwrctrl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl8712_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl871x_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl8712_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl871x_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/runwpa
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/rtl871x_sta_mgt.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wlan0dhcp
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wpa1.conf
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl8712_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl871x_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-22-generic/build M=/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.o
  CC [M]  /TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1881: warning: ‘struct cfg80211_pmksa’ declared inside parameter list
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1881: warning: its scope is only this definition or declaration, which is probably not what you want
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1894: warning: ‘struct cfg80211_pmksa’ declared inside parameter list
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_flush_pmksa’:
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1910: error: storage size of ‘pmksa’ isn’t known
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of ‘sizeof’ to incomplete type ‘struct cfg80211_pmksa’ 
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: At top level:
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: error: unknown field ‘set_pmksa’ specified in initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: warning: excess elements in struct initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: warning: (near initialization for ‘rtw_cfg80211_ops’)
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: error: unknown field ‘del_pmksa’ specified in initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: warning: excess elements in struct initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: warning: (near initialization for ‘rtw_cfg80211_ops’)
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: error: unknown field ‘flush_pmksa’ specified in initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: warning: excess elements in struct initializer
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: warning: (near initialization for ‘rtw_cfg80211_ops’)
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_preinit_wiphy’:
/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2293: error: ‘struct wiphy’ has no member named ‘max_num_pmkids’
make[2]: *** [/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```

---

### Post by Pierrot Lafouine on 2012-10-22
Wow, compilation generate errors, source code doesn't compile...!!!

---

### Post by chili555 on 2012-10-22
I have no idea why it errors out although it purports to be written for 2-6-xx kernels including yours. I tried it a few minutes ago and it errors out for me, too. I have rtl8712_8188_8191_8192SU_usb_linux_v[COLOR="Red"]2.6.0006.20100511[/COLOR] somewhere in my collection and I could get it to you. It makes without any error or even warning on my 10.04 system.

Before you ask for it, frankly I think you'd have a lot more luck upgrading to 12.04 LTS where rtl8192su is built-in. There has been a lot of progress in drivers in the last two years!

What is your preference?

---

### Post by Pierrot Lafouine on 2012-10-22
> **chili555 said:**
> I have no idea why it errors out although it purports to be written for 2-6-xx kernels including yours. I tried it a few minutes ago and it errors out for me, too. I have rtl8712_8188_8191_8192SU_usb_linux_v[COLOR="Red"]2.6.0006.20100511[/COLOR] somewhere in my collection and I could get it to you. It makes without any error or even warning on my 10.04 system.

Before you ask for it, frankly I think you'd have a lot more luck upgrading to 12.04 LTS where rtl8192su is built-in. There has been a lot of progress in drivers in the last two years!

What is your preference?

Upgrade is unfortunately not an option yet.  We tried it and to many software stopped working... :-(

I spend a complete week trying to make this dongle works on Lucid Lynx and Debian Squeeze (it has to work on both), without success, so I'm little desperate and yes I will take your driver.  I have tried this one today : rtl8192SU_usb_linux_v2.6.0006.20100226.zip without any success, so lets give a try with your version 2.6.0006.20100511

Thanks

---

### Post by chili555 on 2012-10-22
> **Pierrot Lafouine said:**
> Upgrade is unfortunately not an option yet.  We tried it and to many software stopped working... :-(

I spend a complete week trying to make this dongle works on Lucid Lynx and Debian Squeeze (it has to work on both), without success, so I'm little desperate and yes I will take your driver.  I have tried this one today : rtl8192SU_usb_linux_v2.6.0006.20100226.zip without any success, so lets give a try with your version 2.6.0006.20100511

ThanksOK, let me work out the process. Be back soon.

---

### Post by chili555 on 2012-10-22
I hope this works as smoothly as it looks in the documentation!  Please download this file and drag and drop it to your desktop. Right-click it and select Extract Here. Now open a terminal and do:```
cd Desktop/rtl
```Press Tab and the remainder will fill in automatically. Press Enter.```
sudo su
make 
make install
modprobe 8712u
exit
```

[https://dl.dropbox.com/u/58267392/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511.tar.gz](https://dl.dropbox.com/u/58267392/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511.tar.gz)

May I see:```
lsusb
```

---

### Post by Pierrot Lafouine on 2012-10-22
This is what I have done so far:

```
1) I downloaded rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511.tar.gz
2) sudo su
3) tar -zxvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511.tar.gz
4) cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511
5) make clean
6) make
7) make install
8) insmod 8712u.ko
```

This is the output of lsusb:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 014: ID 07d1:3303 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This is the output of lsmod | grep 8712 :
```
8712u                 301393  0 
```

This is /etc/networks/interface
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
   wpa-ssid "subway"
   wpa-psk "my_secret_pwd"
```

This is the output of ifup wlan0:
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/1c:af:f7:f6:47:2c
Sending on   LPF/wlan0/1c:af:f7:f6:47:2c
Sending on   Socket/fallback
root@TheSubwayProjectLinux:/TSP/Technology/Equipements/DLink/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511# ifup wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/1c:af:f7:f6:47:2c
Sending on   LPF/wlan0/1c:af:f7:f6:47:2c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 15060
```

Almost done, but what am I missing ?
Thanks

---

### Post by chili555 on 2012-10-22
Is Network Manager removed? Does it scan?```
sudo iwlist wlan0 scan
```Is the ethernet detached?

---

### Post by Pierrot Lafouine on 2012-10-23
The output of : iwlist wlan0 scan

```
wlan0     Scan completed :
          Cell 01 - Address: 64:0F:28:11:DD:59
                    ESSID:"Subway"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  

```

I don't know about ethernet detached / network manager.
Thanks

---

### Post by chili555 on 2012-10-23
> Cell 01 - Address: 64:0F:28:11:DD:59
                    ESSID:"[COLOR="Red"]S[/COLOR]ubway"I suggest you change your /etc/network/interfaces:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
   wpa-ssid [COLOR="Red"]S[/COLOR]ubway
   wpa-psk "my_secret_pwd"
```You don't know about Network Manager?? It comes installed by default on Ubuntu 10.04. If it is in place; i.e. not removed, it will most likely interfer with manual methods in /etc/network/interfaces. Did you remove it?```
ps aux | grep -i network
```And you don't know about ethernet? Can't you reach around and detach the ethernet cable? Does the wireless connect or not with the ethernet detached?

---

### Post by Pierrot Lafouine on 2012-10-23
No luck with Subway.

This is the output of : ps aux | grep -i network


```
root       991  0.0  0.1   9452  2152 ?        Ss   Aug29   0:05 NetworkManager
pl       18070  0.0  0.0  15644  1184 ?        S    Sep05   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.7 /org/gtk/gvfs/exec_spaw/6
root     20920  0.0  0.0   3324   892 pts/2    S+   08:44   0:00 grep -i network
```

---

### Post by chili555 on 2012-10-23
Of course not, because Network Manager is installed and running:> root       991  0.0  0.1   9452  2152 ?        Ss   Aug29   0:05 [COLOR="Red"]NetworkManager[/COLOR]If you want to use manual methods, then remove it:```
sudo apt-get remove --purge network-manage*
```If you want to use NM, then ***don't*** use /etc/network/interfaces, except leave this:```
auto lo
iface lo inet loopback

```Whichever you pick, reboot and then try to connect.

---

### Post by Pierrot Lafouine on 2012-10-23
Hi
Thanks for all the support, I really appreciate.  I commented all line in interface, except loopback as specified, than reboot computer.

This is the output of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:60:8e:c3:80  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe8e:c380/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2231743 (2.2 MB)  TX bytes:524716 (524.7 KB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10104 (10.1 KB)  TX bytes:10104 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:af:f7:f6:47:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

wlan0 deosn't have any IP address yet.  I guess I have to configure NM ?
Thanks

---

### Post by chili555 on 2012-10-23
> wlan0 doesn't have any IP address yet. I guess I have to configure NM ?Not at all. You have to detach the ethernet cable. NM will know you now want to connect wirelessly since wired ethernet is no longer available. It then ought to pop up a little balloon that says 'Networks Available.' You should then click on the NM icon, see your network and click on it. It will ask for your network password and, hopefully, connect.

Please see attached.

---

### Post by Pierrot Lafouine on 2012-10-23
Ok, I disconnect internet cable, and I was able to connect on Internet with usb dongle as you said.

This is nice work and I learned very good stuff, I thank you very much, you rock :guitar:

From my point of view, this is half the job, as I need to setup this on Debian, and I also need to setup adhoc mode.  So more good stuff to come :popcorn:

Cheers!

---

