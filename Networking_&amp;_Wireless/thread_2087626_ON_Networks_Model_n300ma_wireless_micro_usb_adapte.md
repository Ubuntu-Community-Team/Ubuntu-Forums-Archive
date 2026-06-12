---
title: "ON Networks Model n300ma wireless micro usb adapter"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by mthwgrn on 2012-11-24
I have a ON Networks Model n300ma wireless micro usb adapter and I am brand new to ubuntu. I am using the latest 12.04 version of Ubuntu and when I was reading about it, I read that it came prepackaged with most of the wireless adapter drivers/firmware already. Unfortunately the adapter I have isn't one of them. 

I have no idea what to do, can anyone point me in the right direction?

Regards,
Matt

---

### Post by mthwgrn on 2012-11-24
I ran the command lsusb and I found this information, 

Bus 001 Device 007: ID 0846:f001 NetGear, Inc.

This is not a Netgear product, but from what I have read they are near identical

---

### Post by mthwgrn on 2012-11-24
I have been reading for hours, trying to figure out what I can do to get this wireless adapter to work. I came across this article which seems to be the most helpful but I really don't understand what it means. Can someone with a bit more knowledge take 2 minutes and give me a brief rundown in terms a complete newbie would understand on what this article is telling me what to do? You have no idea how much I appreciate any help!

[http://wikidevi.com/wiki/Talk:Netgear_%28On_Networks%29_N300MA]("http://wikidevi.com/wiki/Talk:Netgear_%28On_Networks%29_N300MA")

[IMG]http://i1.cpcache.com/product/460453132/newbie_shirt.jpg?height=150&width=150[/IMG]

---

### Post by mthwgrn on 2012-11-24
Ok ladies and genlemen...

I have found the correct driver for the usb adapter I am trying to use, I believe...

But when I run the installation script that realtek provides I get the following error

```
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/matt/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```


Can anyone help me with this... I've gotten tough love here from the start, maybe someone can shed some light on this for me.

---

### Post by wildmanne39 on 2012-11-24
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by mthwgrn on 2012-11-24
Ty for the response Wildman

In order for me to stay online I have to use my old belkin adapter. What I am trying to do is install a new wireless usb adapter (the one I mentioned above), so the information I send to you is all going to be information on my old belkin wireless adapter. Do you still want this info even though it has nothing to do with the On Networks adapter i'm trying to get installed.

---

### Post by wildmanne39 on 2012-11-24
Hi, hold off on the information as long as you are sure that this is your new device?
```
 Bus 001 Device 007: ID 0846:f001 NetGear, Inc.
```
Thanks

---

### Post by wildmanne39 on 2012-11-24
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by mthwgrn on 2012-11-24
> **Wild Man said:**
> Hi, hold off on the information as long as you are sure that this is your new device?
```
 Bus 001 Device 007: ID 0846:f001 NetGear, Inc.
```Thanks

This is my new device

---

### Post by mthwgrn on 2012-11-24
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux Home-ET1331 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```


```
Bus 001 Device 010: ID 0fce:315b Sony Ericsson Mobile Communications AB 
Bus 001 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 009: ID 0846:f001 NetGear, Inc. 
Bus 002 Device 002: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 006: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Green"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 30:17:C8:FB:EC:F3   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
matt@Home-ET1331:~$ rfkill list all
matt@Home-ET1331:~$ 
```


```
Module                  Size  Used by
r8712u                187895  0 
nls_iso8859_1          12713  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  0 
ppdev                  17073  0 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  6 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         130279  5 
nouveau               895609  7 
snd_usbmidi_lib        24953  1 snd_usb_audio
snd_hwdep              13602  2 snd_hda_codec,snd_usb_audio
snd_pcm                96580  4 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    83595  1 nouveau
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         46784  1 nouveau
drm                   275528  9 nouveau,ttm,drm_kms_helper
snd                    78734  32 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm_amd                55604  0 
kvm                   414070  1 kvm_amd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
soundcore              15047  1 snd
psmouse                95552  0 
i2c_nforce2            13013  0 
i2c_algo_bit           13413  1 nouveau
edac_core              52451  0 
serio_raw              13215  0 
joydev                 17457  0 
k10temp                13126  0 
edac_mce_amd           23303  0 
mxm_wmi                12979  1 nouveau
microcode              22803  0 
video                  19335  1 nouveau
mac_hid                13205  0 
wmi                    19070  2 nouveau,mxm_wmi
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
uas                    17844  0 
usb_storage            48838  0 
pata_amd               14118  0 
sata_nv                31830  2 
forcedeth              67156  0 

```


Keep in mind, I have my belkin adapter plugged in as well as the new adapter.

---

### Post by wildmanne39 on 2012-11-24
I have tried to compile the driver on 12.04 because that is what you said you are using but it looks like 12.10.

I think my good friend chili555 is going to give it a try and he is the master at it, I have to leave for a couple of hours.
Thanks

---

### Post by mthwgrn on 2012-11-24
OMG, my mistake, I am using .10 sorry for the mistake. Thank you very much, all of you for the help..

---

### Post by wildmanne39 on 2012-11-24
Hi, just wanted to let you know that I am working on your issue but it is taking quite a bit of time and I am not sure it will work.
Thanks

---

### Post by chili555 on 2012-11-24
Which version of compat-wireless are you working with, Wild Man? My versions don't build cu; only *ce*.

This won't build at all:> rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201204 05.tar.gzndiswrapper, anyone??

---

### Post by wildmanne39 on 2012-11-24
Hi chili555, here it is.

It is 3.6 compat.
Thanks

---

### Post by wildmanne39 on 2012-11-24
We may have found a solution but it is getting late we are going to wait until tomorrow to work out the details.
Thanks

---

### Post by mthwgrn on 2012-11-25
> **Wild Man said:**
> We may have found a solution but it is getting late we are going to wait until tomorrow to work out the details.
Thanks

I can't wait to see it, regardless if it works or not you have been great and thank you very much!

---

### Post by wildmanne39 on 2012-11-25
Hi, it compiled and shows up in modinfo thanks to the help of chili555 so here are the directions.

Please be sure you are connected to the internet and do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Now go here and download compat-wireless-3.6 stable release to your desktop. [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
When you have the file on your desktop, right-click it and select Extract Here. Now click on the folder it extracted and click on drivers>net>wireless>rtlwifi>rtl8192cu>sw.c.

Now go down to > /****** 8192CU ********/
	{RTL_USB_DEVICE(0x050d, 0x1004, rtl92cu_hal_cfg)}, /*Belcom-SurfN300*/
	{RTL_USB_DEVICE(0x050d, 0x2102, rtl92cu_hal_cfg)}, /*Belcom-Sercomm*/
	{RTL_USB_DEVICE(0x050d, 0x2103, rtl92cu_hal_cfg)}, /*Belcom-Edimax*/
	{RTL_USB_DEVICE(0x0586, 0x341f, rtl92cu_hal_cfg)}, /*Zyxel -Abocom*/
	{RTL_USB_DEVICE(0x07aa, 0x0056, rtl92cu_hal_cfg)}, /*ATKK-Gemtek*/
	{RTL_USB_DEVICE(0x07b8, 0x8178, rtl92cu_hal_cfg)}, /*Funai -Abocom*/
	{RTL_USB_DEVICE(0x0846, 0x9021, rtl92cu_hal_cfg)}, /*Netgear-Sercomm*/
        [COLOR="Red"]{RTL_USB_DEVICE(0x0846, 0xf001, rtl92cu_hal_cfg)}, /*Netgear Wild Mans Experiment*/[/COLOR]
	{RTL_USB_DEVICE(0x0b05, 0x17ab, rtl92cu_hal_cfg)}, /*ASUS-Edimax*/
	{RTL_USB_DEVICE(0x0bda, 0x8186, rtl92cu_hal_cfg)}, /*Realtek 92CE-VAU*/
	{RTL_USB_DEVICE(0x0df6, 0x0061, rtl92cu_hal_cfg)}, /*Sitecom-Edimax*/
	{RTL_USB_DEVICE(0x0e66, 0x0019, rtl92cu_hal_cfg)}, /*Hawking-Edimax*/
	{RTL_USB_DEVICE(0x2001, 0x3307, rtl92cu_hal_cfg)}, /*D-Link-Cameo*/
	{RTL_USB_DEVICE(0x2001, 0x3309, rtl92cu_hal_cfg)}, /*D-Link-Alpha*/
	{RTL_USB_DEVICE(0x2001, 0x330a, rtl92cu_hal_cfg)}, /*D-Link-Alpha*/
	{RTL_USB_DEVICE(0x2019, 0xab2b, rtl92cu_hal_cfg)}, /*Planex -Abocom*/
	{RTL_USB_DEVICE(0x20f4, 0x624d, rtl92cu_hal_cfg)}, /*TRENDNet*/
	{RTL_USB_DEVICE(0x7392, 0x7822, rtl92cu_hal_cfg)}, /*Edimax -Edimax*/
	{}
};
Copy and paste the line in red exactly as it is and put it in the same place as it is then save and close the file.

Now open the terminal:
```
cd Desktop/compat-wireless-3.6.6-1
sudo su
./scripts/driver-select rtlwifi
make
make install
exit
```
Watch for errors, after it is done if there are now errors shutdown the computer and remove your usb adapter and attach the netgear adapter.

Then boot computer and run the following command:
```
sudo modprobe rtl8192cu
```
When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-3.6.6-1
sudo su
./scripts/driver-select restore
./scripts/driver-select rtlwifi
make clean
make
make install
exit
```
Thanks

---

### Post by mthwgrn on 2012-11-25
I am going to attempt this just as soon as I get my daughter too bed (she's 2 so it can be tough) and I will let you know how it goes. I need to get in touch with chili555 so I can thank him as well you guys have been extremely helpful I can not thank you enough regardless if this works or not!

---

### Post by chili555 on 2012-11-25
I'm subscribed so I appreciate your thanks. I am on the same schedule as your daughter so I'm off to bed. I'll look forward to your good report tomorrow.

---

### Post by wildmanne39 on 2012-11-25
Your very welcome! Good Luck!!!
That driver is problematic so we may have to tweak it some.

If you have any questions please ask before continuing.
Thanks

---

### Post by mthwgrn on 2012-11-26
I just got to it, here is what .. reads

    {RTL_USB_DEVICE(0x0586, 0x341f, rtl92cu_hal_cfg)}, /*Zyxel -Abocom*/
    {RTL_USB_DEVICE(0x07aa, 0x0056, rtl92cu_hal_cfg)}, /*ATKK-Gemtek*/
    {RTL_USB_DEVICE(0x07b8, 0x8178, rtl92cu_hal_cfg)}, /*Funai -Abocom*/
    {RTL_USB_DEVICE(0x0846, 0x9021, rtl92cu_hal_cfg)}, /*Netgear-Sercomm*/  
    {RTL_USB_DEVICE(0x0b05, 0x17ab, rtl92cu_hal_cfg)}, /*ASUS-Edimax*/
    {RTL_USB_DEVICE(0x0bda, 0x8186, rtl92cu_hal_cfg)}, /*Realtek 92CE-VAU*/
    {RTL_USB_DEVICE(0x0df6, 0x0061, rtl92cu_hal_cfg)}, /*Sitecom-Edimax*/
    {RTL_USB_DEVICE(0x0e66, 0x0019, rtl92cu_hal_cfg)}, /*Hawking-Edimax*/

It is missing the one highlighted in red, anything I might have did wrong?

---

### Post by wildmanne39 on 2012-11-26
Hi, did you add this line >  {RTL_USB_DEVICE(0x0846, 0xf001, rtl92cu_hal_cfg)}, /*Netgear Wild Mans Experiment*/by copy and pasting it into that file right below >  {RTL_USB_DEVICE(0x0846, 0x9021, rtl92cu_hal_cfg)}, /*Netgear-Sercomm*/
then save and close?
Thanks

---

### Post by mthwgrn on 2012-11-26
Ok, I re-read the directions... Took me a second but I did what you said and here is where I am at

matt@Home-ET1331:~/Desktop/compat-wireless-3.6.6-1$ sudo su
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: net/wireless/Makefile.bk
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make
make -C /lib/modules/3.5.0-17-generic/build M=/home/matt/Desktop/compat-wireless-3.6.6-1 modules
make[1]: Entering directory `/lib/modules/3.5.0-17-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [modules] Error 2
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1#

So, I'm assuming with the errors somewhere down the line something went wrong

---

### Post by wildmanne39 on 2012-11-26
Hi, try this command again then try the build process again.```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Then do:
```
cd Desktop/compat-wireless-3.6.6-1
sudo su
./scripts/driver-select restore
./scripts/driver-select rtlwifi
make clean
make
make install
exit
```
I am about to go to bed so I will check on you tomorrow.
Thanks

---

### Post by mthwgrn on 2012-11-26
```
matt@Home-ET1331:~$ cd Desktop/compat-wireless-3.6.6-1
matt@Home-ET1331:~/Desktop/compat-wireless-3.6.6-1$ sudo su
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select restore
Restored makefile: ./Makefile (and removed backup)
Restored makefile: ./drivers/net/wireless/Makefile (and removed backup)
Restored makefile: ./net/wireless/Makefile (and removed backup)
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make clean
make[1]: Entering directory `/lib/modules/3.5.0-17-generic/build'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [clean] Error 2
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# 
```

i'm not sure what the problem is, have a good night and thanks again

---

### Post by chili555 on 2012-11-26
Wild Man and I are very interested in the result of this previously requested command. Please run it again and show us:```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```

---

### Post by mthwgrn on 2012-11-26
This is what I got when I ran it right now:

```
matt@Home-ET1331:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/1,025 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 155301 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu3 (using .../build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1.1ubuntu1 (using .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.5.0-17-generic 3.5.0-17.28 (using .../linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb) ...
Unpacking replacement linux-headers-3.5.0-17-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu3) ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
Setting up linux-headers-3.5.0-17-generic (3.5.0-17.28) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
matt@Home-ET1331:~$ 

```

Let me know if you gentlemen have any ideas!

---

### Post by chili555 on 2012-11-26
> 1 not upgraded.The Wild Man wonders what this is. Please do:```
sudo apt-get update && sudo apt-get -y upgrade
```Please tell us what was upgraded.

---

### Post by mthwgrn on 2012-11-26
this is what I got:

```
The following packages have been kept back:
  linux-image-generic
The following packages will be upgraded:
  activity-log-manager-common activity-log-manager-control-center at-spi2-core
  busybox-initramfs busybox-static gir1.2-atspi-2.0 gnome-games-data
  gnome-mahjongg gnome-sudoku gnomine im-switch libatspi2.0-0 libssh-4
  mountall

```

Do you think that might have helped? do you think linux-image-generic might be preventing make from working?

---

### Post by mthwgrn on 2012-11-26
tried the make again, here are the results (same as before)

```
matt@Home-ET1331:~/Desktop/compat-wireless-3.6.6-1$ sudo su
[sudo] password for matt: 
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select restore
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make clean
make[1]: Entering directory `/lib/modules/3.5.0-17-generic/build'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [clean] Error 2
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make
make -C /lib/modules/3.5.0-17-generic/build M=/home/matt/Desktop/compat-wireless-3.6.6-1 modules
make[1]: Entering directory `/lib/modules/3.5.0-17-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [modules] Error 2
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# 
```

---

### Post by chili555 on 2012-11-26
> do you think linux-image-generic might be preventing make from working?Maybe, but possibly not directly. I'd go ahead and run the upgrade and then try:```
sudo apt-get install linux-image-generic
```It may give an error or clue as to what's going wrong. 

Weird!

---

### Post by wildmanne39 on 2012-11-26
Strange indeed!

---

### Post by chili555 on 2012-11-26
Here is your 'make clean:'> root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make clean
make[1]: [COLOR="Red"]Entering directory `/lib/modules/3.5.0-17-generic/build'[/COLOR]
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-17-generic/build'
make: *** [clean] Error 2Here is my similar:> root@LAPTOP410:/home/chili/compat-wireless-3.5.4-1-snpc# make clean
make[1]: [COLOR="Red"]Entering directory `/usr/src/linux-headers-3.5.0-18-generic'[/COLOR]
  CLEAN   /home/chili/compat-wireless-3.5.4-1-snpc/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
Until we effect a repair, you system doesn't recognize or use the headers *you've only installed two or three times!!!*

---

### Post by wildmanne39 on 2012-11-26
Hi, try:
```
./configure
```in the driver directory
it should tell us if you have any missing dependcies but I not believe that is the issue and after looking at the driver file I do not believe this command is included in it so I do not think it will even run, I am researching it but chili555 is a lot better at compiling issues then I am.

---

### Post by wildmanne39 on 2012-11-26
Hi, did you make any changes to the make file? will you please post the file here.
Thanks

---

### Post by mthwgrn on 2012-11-26
Nothing is working :(
 
Thanks anyways guys!

---

### Post by mthwgrn on 2012-11-26
Give me ten minutes, I made no changes to the Makefile..

---

### Post by chili555 on 2012-11-26
> **mthwgrn said:**
> Nothing is working :(
 
Thanks anyways guys!What was the result of this?```
sudo apt-get install linux-image-generic
```It may give an error or clue as to what's going wrong.

---

### Post by mthwgrn on 2012-11-26
In the patches directory of compat-wireless this file is there 06-header-changes.patch do you think that might help, and how would I execute it if so?

---

### Post by chili555 on 2012-11-26
Please try my step above.

---

### Post by mthwgrn on 2012-11-27
Hi Guys,

You'll have to excuse me, my daughter is 2.5 and I am a single parent. Usually I get a couple weekends off here and there but my responses may be delayed a bit.

```
matt@Home-ET1331:~$ sudo apt-get install linux-image-generic
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

so I ran this

```
matt@Home-ET1331:~$ sudo apt-get update && sudo apt-get -y upgrade
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://extras.ubuntu.com quantal InRelease 
Ign http://security.ubuntu.com quantal-security InRelease
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]  
Ign http://us.archive.ubuntu.com quantal-backports InRelease                 
Hit http://us.archive.ubuntu.com quantal Release.gpg                         
Get:3 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://us.archive.ubuntu.com quantal Release                               
Get:4 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Get:5 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal-backports Release                     
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://us.archive.ubuntu.com quantal/main Sources                 
Get:6 http://security.ubuntu.com quantal-security/main Sources [13.1 kB]
Hit http://us.archive.ubuntu.com quantal/restricted Sources                   
Hit http://extras.ubuntu.com quantal/main i386 Packages                       
Hit http://us.archive.ubuntu.com quantal/universe Sources
Hit http://us.archive.ubuntu.com quantal/multiverse Sources
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages               
Get:7 http://security.ubuntu.com quantal-security/restricted Sources [14 B]
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages    
Get:8 http://security.ubuntu.com quantal-security/universe Sources [5,417 B]
Get:9 http://security.ubuntu.com quantal-security/multiverse Sources [695 B]   
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Get:10 http://security.ubuntu.com quantal-security/main amd64 Packages [41.4 kB]
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Get:11 http://security.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Get:12 http://security.ubuntu.com quantal-security/universe amd64 Packages [14.7 kB]
Get:13 http://us.archive.ubuntu.com quantal-updates/main Sources [43.4 kB]     
Get:14 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,151 B]
Get:15 http://us.archive.ubuntu.com quantal-updates/restricted Sources [889 B] 
Get:16 http://us.archive.ubuntu.com quantal-updates/universe Sources [18.7 kB] 
Get:17 http://security.ubuntu.com quantal-security/main i386 Packages [41.5 kB]
Get:18 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [2,940 B]
Get:19 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [111 kB]
Get:20 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Get:21 http://security.ubuntu.com quantal-security/universe i386 Packages [14.7 kB]
Get:22 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,394 B]
Get:23 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [1,970 B]
Get:24 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [55.8 kB]
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Get:25 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [7,956 B]
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Get:26 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [111 kB]
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Get:27 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [1,979 B]
Get:28 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [56.2 kB]
Get:29 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [8,121 B]
Get:30 http://us.archive.ubuntu.com quantal-updates/main Translation-en [54.5 kB]
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en     
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Get:31 http://us.archive.ubuntu.com quantal-updates/universe Translation-en [32.2 kB]
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US   
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Hit http://us.archive.ubuntu.com quantal-backports/main Sources                
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US     
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources          
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources            
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com quantal-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en     
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Fetched 743 kB in 24s (30.0 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils coreutils libapt-inst1.5 libapt-pkg4.12
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,439 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main coreutils amd64 8.13-3.2ubuntu2.1 [2,212 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libapt-pkg4.12 amd64 0.9.7.5ubuntu5.1 [799 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main apt amd64 0.9.7.5ubuntu5.1 [1,157 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libapt-inst1.5 amd64 0.9.7.5ubuntu5.1 [70.3 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main apt-utils amd64 0.9.7.5ubuntu5.1 [185 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main apt-transport-https amd64 0.9.7.5ubuntu5.1 [15.8 kB]
Fetched 4,439 kB in 1min 17s (57.2 kB/s)                                       
(Reading database ... 159604 files and directories currently installed.)
Preparing to replace coreutils 8.13-3.2ubuntu2 (using .../coreutils_8.13-3.2ubuntu2.1_amd64.deb) ...
Unpacking replacement coreutils ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up coreutils (8.13-3.2ubuntu2.1) ...
(Reading database ... 159604 files and directories currently installed.)
Preparing to replace libapt-pkg4.12:amd64 0.9.7.5ubuntu5 (using .../libapt-pkg4.12_0.9.7.5ubuntu5.1_amd64.deb) ...
Unpacking replacement libapt-pkg4.12:amd64 ...
Setting up libapt-pkg4.12:amd64 (0.9.7.5ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 159604 files and directories currently installed.)
Preparing to replace apt 0.9.7.5ubuntu5 (using .../apt_0.9.7.5ubuntu5.1_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.9.7.5ubuntu5.1) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 159604 files and directories currently installed.)
Preparing to replace libapt-inst1.5:amd64 0.9.7.5ubuntu5 (using .../libapt-inst1.5_0.9.7.5ubuntu5.1_amd64.deb) ...
Unpacking replacement libapt-inst1.5:amd64 ...
Preparing to replace apt-utils 0.9.7.5ubuntu5 (using .../apt-utils_0.9.7.5ubuntu5.1_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace apt-transport-https 0.9.7.5ubuntu5 (using .../apt-transport-https_0.9.7.5ubuntu5.1_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Processing triggers for man-db ...
Setting up libapt-inst1.5:amd64 (0.9.7.5ubuntu5.1) ...
Setting up apt-utils (0.9.7.5ubuntu5.1) ...
Setting up apt-transport-https (0.9.7.5ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Any ides?

---

### Post by mthwgrn on 2012-11-27
I ran this, and look, it's different now!

```
matt@Home-ET1331:~$ cd Desktop/compat-wireless-3.6.6-1
matt@Home-ET1331:~/Desktop/compat-wireless-3.6.6-1$ sudo su
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select restore
Restored makefile: ./Makefile (and removed backup)
Restored makefile: ./drivers/net/wireless/Makefile (and removed backup)
Restored makefile: ./net/wireless/Makefile (and removed backup)
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make clean
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# make
./scripts/gen-compat-autoconf.sh /home/matt/Desktop/compat-wireless-3.6.6-1/.config /home/matt/Desktop/compat-wireless-3.6.6-1/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-18-generic/build M=/home/matt/Desktop/compat-wireless-3.6.6-1 modules
make: *** /lib/modules/3.5.0-18-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
root@Home-ET1331:/home/matt/Desktop/compat-wireless-3.6.6-1# 

```

make clean just went to another line, and make didn't return error 1

---

### Post by mthwgrn on 2012-11-27
This is what my directory looks like, do you have any other files? am I missing any?

root@Home-ET1331:/lib/modules/3.5.0-18-generic# ls
initrd               modules.dep          modules.order
kernel               modules.dep.bin      modules.pcimap
modules.alias        modules.devname      modules.seriomap
modules.alias.bin    modules.ieee1394map  modules.softdep
modules.builtin      modules.inputmap     modules.symbols
modules.builtin.bin  modules.isapnpmap    modules.symbols.bin
modules.ccwmap       modules.ofmap        modules.usbmap

keep in mind when I run lsusb this is the device I want to configure (yes I've had it unplugged I just plugged it in for this info)

Bus 001 Device 006: ID 0846:f001 NetGear, Inc. 

This is an On Networks model n300ma not a NetGear adapter

Do you think I should use an older stable kernel?

---

### Post by chili555 on 2012-11-27
> You'll have to excuse me, my daughter is 2.5 and I am a single parent.I've been there, although my daughter was 15 at the time. My heart and empathy goes out to you. Don't worry too much about your computer and certainly not about us. Your daughter and your relationship are most important. > make: *** [COLOR="Red"]/lib/modules/3.5.0-18-generic/build[/COLOR]: No such file or directory.  Stop.This ***still*** indicates that the kernel headers are not installed or at least not correctly. If I were the type to curse, I might start now! Here is the result from a successful make:> root@LAPTOP410:/home/chili/compat-wireless-3.5.4-1-snpc# make clean
make[1]: [COLOR="Red"]Entering directory `/usr/src/linux-headers-3.5.0-18-generic'[/COLOR]
CLEAN /home/chili/compat-wireless-3.5.4-1-snpc/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic' Your 'make' tries /lib/modules; mine tries and succeeds in /usr/src/linux-headers.

Please do these steps exactly in order, one at a time to completion before you start the next. Reboot. Next, do:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~. When it's done, do:```
sudo apt-get install --reinstall linux-headers-`uname -r`
```When it's done, do:```
sudo apt-get install --reinstall linux-headers-generic
```Reboot and try 'make clean' and if successful, the remaining process on compat-wireless.

---

### Post by mthwgrn on 2012-11-27
EVERYTHING WORKS GREAT!!!!

If Ubuntu wasn't free, I would have to write a letter to the developers and recommend that they pay both you (Chili555) and WildMan. You guys did an excellent job and helped someone completely new to Linux with a very difficult thing. I can't thank you enough. You guys are both "The Man"!!!!

I hope this thread can in the future help others I am going to mark it solved!

I am using the On Networks adapter to type this last reply :)

---

### Post by wildmanne39 on 2012-11-27
Hi, that is great, I am glad to hear it worked and it was fun working on this driver.

Chili555 is my mentor and friend he has taught me everything I know, but I still have a lot to learn.
Enjoy!!!

---

### Post by chili555 on 2012-11-28
> EVERYTHING WORKS GREAT!!!!I just had all the payday I ever expect or need. Thank you both for your very kind comments. Have fun!

---

### Post by maffiakillen on 2012-11-28
By curiousness I found this thread.
 
> **mthwgrn said:**
> EVERYTHING WORKS GREAT!!!!
 
If Ubuntu wasn't free, I would have to write a letter to the developers and recommend that they pay both you (Chili555) and WildMan. You guys did an excellent job and helped someone completely new to Linux with a very difficult thing. I can't thank you enough. You guys are both "The Man"!!!!
 
I hope this thread can in the future help others I am going to mark it solved!
 
I am using the On Networks adapter to type this last reply :)
Do you know what exactly solved the problem?? :-k
 
I have the same usb micro adapter (not expensive, new to market I think. My first problem was that the niswrapper had a bug, I downloaded separately outside propisitory, next problem was that I took driver WNA3100m.inf and the other one with same name but ending with .dll. But the windows driver didnt work so I opened .inf with an texteditor and changed 0846:9021 >> to the new 0846:f001 and the it worked. 
 
It was getting me crasy, first the bug and then the missmatch with originaldriver and the vendor:ID missmatch.
 
Anyway it works but I am still not pleased. It worked on Mint and I want it to work on backtrack5 R2 x32 with monitor-mode (airmon-n).
 
I downloaded the original-Driver from realtek [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 
 
But I dont really know how to put it in /usr/local or /usr/src/linux-source-3.2.6/firmware/drivers. I want to use original chipset RTL8192CU and not ndiswrapper. I have the "Makefile and others. if you download the [link]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") and choose Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.8. You will se those files included. Wich of them should I put where in system folders??? I know this is ubuntu-forum but both Mint and BT5 are ubuntu-based so it will be applied on Ubuntu too.
 
How to put this in kernel or whatever. Thanks in advance.
I would be happy for solidation.

---

### Post by wildmanne39 on 2012-11-28
Hi, we were not able to get the realtek driver to work so we used the one from compat as listed in this thread if you want to use it just follow the directions posted in the thread and if you have questions please ask.

We do not support airmon-n in the ubuntu forum so for exact directions on it you should ask in the backtrack forum.

The driver from compat may support it but since it is not supported on the forum I did not look to see for sure and we can not discuss it here.
Thanks

---

### Post by maffiakillen on 2012-11-29
> **Wild Man said:**
> Hi, we were not able to get the realtek driver to work so we used the one from compat as listed in this thread if you want to use it just follow the directions posted in the thread and if you have questions please ask.
 
 
The driver from compat may support it but since it is not supported on the forum I did not look to see for sure and we can not discuss it here.
Thanks
 Thankyou! I just wanted the native driver support, and will give the compat a try. My next question is for later, I will do my search first.  I'm feeling that it also have been answered before in the forum. Enjoy the coffe, I'm doing it.

---

### Post by TakuyaMK on 2012-11-29
It works on my PC too!, thanks a lot! :D

---

### Post by truckbytes on 2012-12-01
I also bought a On Networks N300 and need to get it working. I am using the current version of Linux Mint which uses Ubuntu. will these instructions work for me too? I am very green with Linux and don't understand much of the terminology so any basic step by step for newbies like me would be greatly appreciated! BTW - my machine is partitioned and the only internet access I have is wireless since I travel all across US & Canada for work.

---

### Post by chili555 on 2012-12-01
> **truckbytes said:**
> I also bought a On Networks N300 and need to get it working. I am using the current version of Linux Mint which uses Ubuntu. will these instructions work for me too? I am very green with Linux and don't understand much of the terminology so any basic step by step for newbies like me would be greatly appreciated! BTW - my machine is partitioned and the only internet access I have is wireless since I travel all across US & Canada for work.The instructions at post #18 is pretty much all you need. 

Be sure you have an ethernet connection before you start and you can just copy and paste the instructions into a terminal. The only possible hitch is that the selected compat-wireless package might not compile against your Mint kernel, whatever that is. These instructions were written for Ubuntu 12.10, using the 3.5.0-xx kernel. I don't have Mint installed anyplace so I'm unable to check for you.

I'd just amend one tiny part:```
sudo apt-get install linux-headers-generic build-essential dkms
```Post back if you get stuck.

---

### Post by truckbytes on 2012-12-01
Thank you! Printing thread now for reference. I'll be sure to check the Kernel before I start. Sounds like I'll be shopping for a hotel with Ethernet available if there are any still out there!

---

### Post by truckbytes on 2012-12-01
Got the Kernel info. 3.2.0-23-generic (i686)

Also says Default C Compiler Gnu C Compiler Version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)

---

### Post by chili555 on 2012-12-01
> **truckbytes said:**
> Got the Kernel info. 3.2.0-23-generic (i686)

Also says Default C Compiler Gnu C Compiler Version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)Using a live CD running 3.2.0-23-generic, I built this version without error or a single warning. It should build for you just as well. Be sure to *carefully* make the changes Wild Man outlines in post #18.

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1.tar.bz2)

Post back if you get stuck. kompile R us.

---

### Post by truckbytes on 2012-12-01
Thanks Chili! I found a Hampton Inn that has Ethernet :-) So I'm checking in tomorrow and gonna get this finished. I'll post my success or any challenges I have.

---

### Post by chili555 on 2012-12-01
I'm fairly confident it will go smoothly but post back if you need help. I'll be around.

---

### Post by truckbytes on 2012-12-02
OK, I'm having a small challenge. In #18 Wildman says....

When you have the file on your desktop, right-click it and select Extract Here. Now click on the folder it extracted and click on drivers>net>wireless>rtlwifi>rtl8192cu>sw.c.

I can only get as far as the wireless folder and then my folders & files are different. Any suggetsions? (Would attach a screen shot if I could figure out how!)

---

### Post by truckbytes on 2012-12-02
Ah, I can give you the list though!

/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/ath
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/b43
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/b43legacy
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/brcm80211
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/ipw2x00
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/iwlegacy
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/iwlwifi
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/iwmc3200wifi
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/libertas
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/libertas_tf
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/mwifiex
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/orinoco
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/p54
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rt2x00
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtl818x
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/ti
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/zd1211rw
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/adm8211.c
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/adm8211.h
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/at76c50x-usb.c
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/at76c50x-usb.h
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/mac80211_hwsim.c
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/mac80211_hwsim.h
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/Makefile
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/mwl8k.c
/home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rndis_wlan.c

---

### Post by truckbytes on 2012-12-02
Making progress but not finding the line in mine that wildman identifies. Here is what mine has...

/****** 8188CU ********/
	{RTL_USB_DEVICE(0x050d, 0x1102, rtl92cu_hal_cfg)}, /*Belkin - Edimax*/
	{RTL_USB_DEVICE(0x06f8, 0xe033, rtl92cu_hal_cfg)}, /*Hercules - Edimax*/
	{RTL_USB_DEVICE(0x07b8, 0x8188, rtl92cu_hal_cfg)}, /*Abocom - Abocom*/
	{RTL_USB_DEVICE(0x07b8, 0x8189, rtl92cu_hal_cfg)}, /*Funai - Abocom*/
	{RTL_USB_DEVICE(0x0846, 0x9041, rtl92cu_hal_cfg)}, /*NetGear WNA1000M*/
	{RTL_USB_DEVICE(0x0bda, 0x5088, rtl92cu_hal_cfg)}, /*Thinkware-CC&C*/
	{RTL_USB_DEVICE(0x0df6, 0x0052, rtl92cu_hal_cfg)}, /*Sitecom - Edimax*/
	{RTL_USB_DEVICE(0x0df6, 0x005c, rtl92cu_hal_cfg)}, /*Sitecom - Edimax*/
	{RTL_USB_DEVICE(0x0eb0, 0x9071, rtl92cu_hal_cfg)}, /*NO Brand - Etop*/
	{RTL_USB_DEVICE(0x4856, 0x0091, rtl92cu_hal_cfg)}, /*NetweeN - Feixun*/

---

### Post by truckbytes on 2012-12-02
I tried this.....

/****** 8188CU ********/
	{RTL_USB_DEVICE(0x050d, 0x1102, rtl92cu_hal_cfg)}, /*Belkin - Edimax*/
	{RTL_USB_DEVICE(0x06f8, 0xe033, rtl92cu_hal_cfg)}, /*Hercules - Edimax*/
	{RTL_USB_DEVICE(0x07b8, 0x8188, rtl92cu_hal_cfg)}, /*Abocom - Abocom*/
	{RTL_USB_DEVICE(0x07b8, 0x8189, rtl92cu_hal_cfg)}, /*Funai - Abocom*/
	{RTL_USB_DEVICE(0x0846, 0x9041, rtl92cu_hal_cfg)}, /*NetGear WNA1000M*/
	{RTL_USB_DEVICE(0x0846, 0xf001, rtl92cu_hal_cfg)}, /*Netgear Wild Mans Experiment*/
	{RTL_USB_DEVICE(0x0bda, 0x5088, rtl92cu_hal_cfg)}, /*Thinkware-CC&C*/
	{RTL_USB_DEVICE(0x0df6, 0x0052, rtl92cu_hal_cfg)}, /*Sitecom - Edimax*/
	{RTL_USB_DEVICE(0x0df6, 0x005c, rtl92cu_hal_cfg)}, /*Sitecom - Edimax*/
	{RTL_USB_DEVICE(0x0eb0, 0x9071, rtl92cu_hal_cfg)}, /*NO Brand - Etop*/
	{RTL_USB_DEVICE(0x4856, 0x0091, rtl92cu_hal_cfg)}, /*NetweeN - Feixun*/

re-booted but no luck yet. So I'm at a stand still.

---

### Post by truckbytes on 2012-12-02
Oh, I did try this part too,....

joel@joel-Latitude-D630 ~ $ cd Desktop/ compat-witeless-3.5.4-1
joel@joel-Latitude-D630 ~/Desktop $ sudo su
[sudo] password for joel: 
joel-Latitude-D630 Desktop # ./scripts/driver-select rtlwifi
bash: ./scripts/driver-select: No such file or directory
joel-Latitude-D630 Desktop # cd compat-wireless3.4.5-1
bash: cd: compat-wireless3.4.5-1: No such file or directory
joel-Latitude-D630 Desktop # ./scripts/driver-select rtlwifi make
bash: ./scripts/driver-select: No such file or directory
joel-Latitude-D630 Desktop # ./scripts/driver-select rtlwifi
bash: ./scripts/driver-select: No such file or directory
joel-Latitude-D630 Desktop #

---

### Post by chili555 on 2012-12-02
> joel@joel-Latitude-D630 ~ $ cd Desktop/[COLOR="Red"]X[/COLOR]compat-witeless-3.5.4-1
joel@joel-Latitude-D630 ~/Desktop $ sudo su
[sudo] password for joel:
joel-Latitude-D630 Desktop # ./scripts/driver-select rtlwifiSee that little space in there, where I put the X? It doesn't belong there. Please try again. Also, it's not 'witeless.'

You will know you have a problem when you press Enter and it doesn't actually change directories to where you commanded. You said:> $ cd Desktop/ compat-witeless-3.5.4-1  [COLOR="Red"]<--with a space[/COLOR]Then you pressed Enter and you got:> joel@joel-Latitude-D630 ~/Desktop $  [COLOR="Red"]<--*NOT* in compat-wireless![/COLOR]When you try again, it should read:> joel@joel-Latitude-D630 ~/Desktop/compat-wi[COLOR="Red"]r[/COLOR]eless-3.5.4-1 $Moreover, your driver-select will succeed.

By the way, I know all this stuff because I've made the same mistake many times!

---

### Post by truckbytes on 2012-12-02
Oops... Thanks! I am this far now....

joel-Latitude-D630 compat-wireless-3.5.4-1 # ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
joel-Latitude-D630 compat-wireless-3.5.4-1 # ^C
joel-Latitude-D630 compat-wireless-3.5.4-1 #

---

### Post by truckbytes on 2012-12-02
Do I now reboot and run....

sudo modprobe rtl8192cu

from a terminal?

---

### Post by chili555 on 2012-12-02
> **truckbytes said:**
> Do I now reboot and run....

sudo modprobe rtl8192cu

from a terminal?Nope. This is what post #18 says:> Now open the terminal:
Code:

cd Desktop/compat-wireless-3.6.6-1
sudo su
./scripts/driver-select rtlwifi
[COLOR="Red"]make
make install
exit[/COLOR]

Please proceed. You are doing fine so far.

---

### Post by truckbytes on 2012-12-02
Running the last commands now.... I didn't realize those were each commands to be ran independantly. Thanks Chili! Ireally appreciate your help :-)

---

### Post by truckbytes on 2012-12-02
Done and now rebooting

joel-Latitude-D630 Desktop # ./scripts/driver-select rtlwifi
bash: ./scripts/driver-select: No such file or directory
joel-Latitude-D630 Desktop # cd compat-wireless-3.5.4-1
joel-Latitude-D630 compat-wireless-3.5.4-1 # ./scripts/driver-select rtlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
joel-Latitude-D630 compat-wireless-3.5.4-1 # ^C
joel-Latitude-D630 compat-wireless-3.5.4-1 # make
./scripts/gen-compat-autoconf.sh /home/joel/Desktop/compat-wireless-3.5.4-1/.config /home/joel/Desktop/compat-wireless-3.5.4-1/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-23-generic/build M=/home/joel/Desktop/compat-wireless-3.5.4-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/main.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat-3.3.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat-3.4.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat_atomic.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_fq_codel_core.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/flow_dissector.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_codel.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_fq_codel.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/base.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/cam.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/core.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/debug.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/efuse.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/ps.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rc.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/regd.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/pci.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/usb.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtlwifi.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/main.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/hw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/led.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/phy.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/rf.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/sw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/table.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/trx.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/dm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/hw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/led.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/mac.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/phy.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/rf.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/sw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/table.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/trx.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/dm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/fw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/hw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/led.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/phy.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/rf.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/sw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/table.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/trx.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/dm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/fw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/hw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/led.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/phy.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/rf.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/sw.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/table.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/trx.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/main.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/status.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/sta_info.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/wep.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/wpa.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/scan.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/offchannel.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/ht.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/agg-tx.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/agg-rx.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/ibss.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/work.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/iface.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rate.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/michael.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/tkip.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/aes_ccm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/aes_cmac.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/cfg.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rx.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/spectmgmt.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/tx.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/key.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/util.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/wme.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/event.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/chan.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mlme.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/driver-trace.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/led.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/debugfs.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/debugfs_sta.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/debugfs_netdev.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/debugfs_key.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mesh.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mesh_plink.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mesh_hwmp.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mesh_sync.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/pm.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mac80211.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/rfkill/rfkill-regulator.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/core.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/sysfs.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/radiotap.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/util.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/reg.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/scan.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/nl80211.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/mlme.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/ibss.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/sme.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/chan.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/ethtool.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/mesh.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/debugfs.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/wext-compat.o
  CC [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/wext-sme.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 12 modules
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_codel.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_codel.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_fq_codel.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_fq_codel.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mac80211.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/rfkill/rfkill-regulator.ko
  CC      /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
joel-Latitude-D630 compat-wireless-3.5.4-1 # make install

make -C /lib/modules/3.2.0-23-generic/build M=/home/joel/Desktop/compat-wireless-3.5.4-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  Building modules, stage 2.
  MODPOST 12 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make -C /lib/modules/3.2.0-23-generic/build M=/home/joel/Desktop/compat-wireless-3.5.4-1 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/compat/compat.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_codel.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/compat/sch_fq_codel.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/net/mac80211/mac80211.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/net/rfkill/rfkill-regulator.ko
  INSTALL /home/joel/Desktop/compat-wireless-3.5.4-1/net/wireless/cfg80211.ko
  DEPMOD  3.2.0-23-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'

Note: iwl4965 detected, we're going to disable it. If you would like to enable it later you can run:
    sudo iwl-load iwl4965

Running iwl-enable iwlagn...
Disabling iwl4965 ...	[OK]	Module disabled:
kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

joel-Latitude-D630 compat-wireless-3.5.4-1 # exit
exit
joel@joel-Latitude-D630 ~/Desktop $

---

### Post by chili555 on 2012-12-02
Hmmm. Do you have an internal Intel wireless device? Why did you need the micro USB, aside from its cuteness?> Note: [COLOR="Red"]iwl4965[/COLOR] detected, we're going to disable it. If you would like to enable it later you can run:
sudo iwl-load iwl4965


---

### Post by truckbytes on 2012-12-02
And this iswhat I have...

joel@joel-Latitude-D630 ~ $ sudo modprobe rtl8192cu
[sudo] password for joel: 
joel@joel-Latitude-D630 ~ $ 

Success!!!!!!!!!!!!!!!!!

Thank you very much Chili!!!!!!!!!!!! I hope you have a great Sunday :-)

---

### Post by truckbytes on 2012-12-02
Dumb question.... Can I delete the compat-wireless folder onthedesktop now?

---

### Post by truckbytes on 2012-12-02
WE got it Chili!!!!!!!!! Thank you very much :-)

Dumb question.... can I delete the compat-wireless folder on the desktop now?

---

### Post by truckbytes on 2012-12-02
Yeah, that's a long story.... in a nut shell the broadcom I have won't work even when I used the additional drivers for it. So it was a lot easier to get a USB device. I killed my last one the other day and had to replace it which is what led me to all this.

Sorry about the multiple posts..... they didn't show in my browser at first.

---

### Post by chili555 on 2012-12-02
> **truckbytes said:**
> Dumb question.... Can I delete the compat-wireless folder onthedesktop now?No. When a later kernel version is installed by Update Manager, you will need to re-compile for the later kernel:```
cd Desktop/compat-wireless-3.5.4-1
sudo su
./scripts/driver-select restore 
./scripts/driver-select rtlwifi
make clean
make
make install
exit
```Please retain the folder and these instructions.

---

### Post by chili555 on 2012-12-02
>  in a nut shell the broadcom I have won't work even when I used the additional drivers for it. I suspect it didn't work with the Broadcom additional drivers because its an Intel.

If you want to troubleshoot, start a new thread and we'll try to fix it. At the very least, its driver should be blacklisted.

---

### Post by nmstewart on 2013-02-03
You guys are awesome!!! Post 18 worked like a charm. Only I didn't need to do the last modprobe step. It worked immediately after the re-boot.

Again, Thanks Thanks Thanks
Neil

---

### Post by voit2 on 2013-08-18
The only solution that worked for me (kernel 3.5 and 3.8 ) was a deb package. ( I modified it a bit)
it works for "on networks n300ma wifi adapter"
[URL="http://forum.ubuntu-fr.org/viewtopic.php?pid=13755671#p13755671"]http://forum.ubuntu-fr.org/viewtopic.php?pid=13755671#p13755671

deb:

[http://www.4shared.com/file/grM4CEFU/rtl8192cu-tjp-dkms_16_all.html](http://www.4shared.com/file/grM4CEFU/rtl8192cu-tjp-dkms_16_all.html)

[/URL]

---

### Post by praseodym on 2013-08-18
[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

The same

---

### Post by mattfromwales on 2013-10-07
Hi Guys,

I have been trying to install from post 18 but straight away after running the first command:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```

```
matthew@mgsrv:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  module-assistant thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,098 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 195009 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2.1 (using .../build-essential_11.5ubuntu2.1_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1ubuntu3.1 (using .../dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.8.0-31-generic 3.8.0-31.46~precise1 (using .../linux-headers-3.8.0-31-generic_3.8.0-31.46~precise1_amd64.deb) ...
Unpacking replacement linux-headers-3.8.0-31-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu2.1) ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Setting up linux-headers-3.8.0-31-generic (3.8.0-31.46~precise1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Error! Bad return status for module build on kernel: 3.8.0-31-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
matthew@mgsrv:~$ 

```

The contents of the make.log look like:

```

DKMS make.log for ndiswrapper-1.57 for kernel 3.8.0-31-generic (x86_64)
Mon Oct  7 20:32:57 BST 2013


Cannot find kernel build files in /usr/src/linux-headers-3.8.0-31-generic
Please give the path to kernel build directory with
the KBUILD=<path> argument to make


make: *** [config_check] Error 1

```

It's driving me insane, i've been trying to get this to work all night now. I'm using the same adaptor (n300ma) as the other posters in this thread.

Thanks for an help.
matt

---

### Post by praseodym on 2013-10-07
Hi,

uninstall ndiswrapper and install the driver via:
```

sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by mattfromwales on 2013-10-07
Hi,

Thanks for your assistance. I ran those commands and received no errors back but unfortunately it is still not working. Is there anything I can run to point us in the right direction?

thanks

---

