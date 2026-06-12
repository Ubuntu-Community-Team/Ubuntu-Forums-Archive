---
title: "Can't make my USB RTL8192U to work"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by Abralibemu on 2012-10-16
Hello dear people of the Ubuntu community,

I'm all new here, and don't know much about terminal command lines and the such, so please bear with me :)

After installing 12.04, I could not connect to the internet vwirelessly via my USB realtek device. I looked around and it seems I cannot detect my wireless network.

Maybe I need the drivers, or something else for it. I would not know I'm no PC genius :)

Note :  If any downloads are required I have another PC from which I can download the needed files

Cheers

---

### Post by ahallubuntu on 2012-10-16
I have a couple of these cheap WiFi dongles.  They worked quite well in older versions of Ubuntu after installing the driver.  Kind of as a tease, the thing works in Ubuntu 12.04 on the live CD (when I was able to connect to my network) but not after installation.

So I downloaded the driver again from Realtek and made it work.

This link should get you to the Realtek downloads page:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

(Try the different mirrors if you can't successfully download on the first click.  It's a zip file; if you get redirected to another pop-up window, close that new window and try again.)

Copy the zip file to somewhere on your Ubuntu computer (for example, /home/YOURNAME/Downloads ).  Unzip the zip file on the target computer.   (Open a terminal in Ubuntu and type "unzip (filename)" ).

It should create a directory like "rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405"

in the terminal, type

```
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

One weird thing: you have to make the install file executable:

```
chmod 755 ./install.sh
```

Now type:

```
sudo ./install.sh
```

and that should do it.  You may have to add the name of the new module to the file /etc/modules so it is automatically loaded each time you start the computer.  Also, you may have to blacklist the old drivers (module names).

---

### Post by Abralibemu on 2012-10-16
Thank you ahallubuntu,

Everything worked as you said but at the end of the installation process, I got 2 error messages, and it's still not working

Here is the installation log:



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
 make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-29-generic-pae/build M=/home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules  
 make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'  
   CC [M]  /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o 
 In file included from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0, 
                  from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
 /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type  
 In file included from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0, 
                  from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
 /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type  
 In file included from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0, 
                  from /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
 /home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type  
 make[2]: *** [/home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1  
 make[1]: *** [_module_/home/salon/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2  
 make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'  
 make: *** [modules] Error 2  
 ################################################## 
 Compile make driver error: 2  
 Please check error Mesg  
 


Thank you so much for your help

Cheers

---

### Post by ahallubuntu on 2012-10-16
Are you sure you typed "sudo" in front of the "./install.sh" command?  Your log looks like it is asking for authentication several times, but if you type sudo in front it should only ask for it that one time.  Often these things fail due to not having permissions that "sudo" would grant.

---

### Post by Abralibemu on 2012-10-16
yes I did, sadly hehe. Then I entered my user account password when terminal prompt me to enter a password (since it's the only one I set for Ubuntu I figured this was the same for root password), and the install process started..with the above results.

---

### Post by ahallubuntu on 2012-10-20
OK, I tried it and got the same kinds of errors a couple of days ago with a fresh install of 12.04 and the Realtek drivers for this thing.

But I tried it again tonight and downloaded a fresh copy from Realtek's site from here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

(for the 8192cu which is the chipset my dongle shows)

And it worked.  Maybe Realtek's site was messed up? Not sure.

I did blacklist these three kernel modules in /etc/modprobe.d/blacklist.conf


```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

After the build was done, I added the new module name "8192cu" to the end of /etc/modules so it would be loaded at each startup.

---

### Post by Abralibemu on 2012-10-22
Oh thanks!
<
that worked!

Cheers mate for your time!

---

