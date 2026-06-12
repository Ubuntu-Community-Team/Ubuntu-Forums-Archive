---
title: "no wireless on clean install, Realtek RTL8192CU"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by gps123 on 2011-12-29
I just did a clean install of Kubuntu 11.10.  I'm coming from Ubuntu 10.10, where the wireless was working fine.  

lsusb shows **RTL8188CUS **is there.  I can see the wireless routers in my neighborhood, but can't connect.  I hang up on "configuring interface."

Any help will be appreciated.

---

### Post by inobe on 2011-12-30
with pc shut down, plug in usb wireless card.

startup make sure wireless is enabled, open terminal and run this

```
nm-tool
```

highlight, copy and paste the terminal output here after hitting enter.

---

### Post by gps123 on 2011-12-31
Here is the return for nm-tool.  Thank you!

```
                      p { margin-bottom: 0.08in; }  NetworkManager Tool
 

 State: connecting
 

 - Device: eth0 -----------------------------------------------------------------
   Type:              Wired
   Driver:            e100
   State:             unavailable
   Default:           no
   HW Address:        00:12:3F:B6:02:E6
 

   Capabilities:
     Carrier Detect:  yes
     Speed:           10 Mb/s
 

   Wired Properties
     Carrier:         off
 

 

 - Device: wlan0  [linksys] -----------------------------------------------------
   Type:              802.11 WiFi
   Driver:            rtl8192cu
   State:             connecting (configuring)
   Default:           no
   HW Address:        00:A1:B0:83:35:3F
 

   Capabilities:
 

   Wireless Properties
     WEP Encryption:  yes
     WPA Encryption:  yes
     WPA2 Encryption: yes
 

   Wireless Access Points  
     linksys:         Infra, 00:18:F8:E4:25:19, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
     2WIRE560:        Infra, 00:26:50:04:D4:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
     verbal:          Infra, 00:1B:63:2C:5E:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
 
```

---

### Post by gdselzer on 2011-12-31
The driver provided in the distribution appears to be broken.  In order to get this to work, follow the instructions here:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

The most recent version of the driver no longer requires Step 3 of the instructions in the linked page.  I've got mine up and running.  However, I can't figure out how to get the bitrate above 72Mb/s.  Has anyone figured out how to get the full 150Mb/s?

---

### Post by gdselzer on 2011-12-31
Just realized the link in that page does not work.  Here is the place to download the driver:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS")

---

### Post by inobe on 2011-12-31
go into network manager> manage connections> hit wireless tab> delete all your connections> restart> attempt to connect to just one access point.

---

### Post by gps123 on 2011-12-31
This is promising.  But here are my returns for the install and gedit in Kubuntu.

```
                      p { margin-bottom: 0.08in; }  computer@computer-Dell-DXC051:~/Desktop/Realtek driver/RTL8188C_8192C_8192D_USB_linux_v3.3.1_3083.20111213$ sudo bash install.sh
 [sudo] password for computer:  
 ##################################################
 Realtek Wi-Fi driver Auto installation script
 Novembor, 21 2011 v1.1.0
 ##################################################
 Decompress the driver source tar ball:
         rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213.tar.gz
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/Kconfig
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/clean
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/autoconf_rtl8192c_usb_linux.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/wlan0dhcp
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_led.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/pci_ops.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_spec.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DEHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/drv_conf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_eeprom.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/drv_types_ce.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_xmit.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_qos.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/osdep_intf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_ioctl.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/osdep_ce_service.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/usb_vendor_req.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_mp.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/pci_hal.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_mp_phy_regdef.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/ieee80211_ext.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_sreset.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_ops_linux.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/mlme_osdep.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_recv.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DETestHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/drv_types_xp.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_event.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/mp_custom_oid.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_mp_ioctl.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_byteorder.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/if_ether.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/h2clbk.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_cmd.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_rf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_version.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_hal.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_hal.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/swab.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/little_endian.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/swabb.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/generic.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/byteorder/big_endian.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/usb_hal.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sta_info.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_br_ext.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_osintf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/wifi.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192CEHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192CUHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_led.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_recv.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_ht.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/xmit_osdep.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_recv.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/autoconf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_mlme.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_rf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DUTestHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_io.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DPhyReg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/drv_types_linux.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/nic_spec.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_dm.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/cmd_osdep.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192CPhyReg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_cmd.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/drv_types.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/ip.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_spec.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/pci_osintf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/ieee80211.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_efuse.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_ioctl_set.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_ops_ce.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_p2p.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_pwrctrl.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/wlan_bssdef.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_event.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_mlme_ext.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DUHWImg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_ops_xp.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_hal.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/circ_buf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/ethernet.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_debug.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192CPhyCfg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/usb_osintf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_dm.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192c_rf.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_led.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/basic_types.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_xmit.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/hal_init.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_ioctl_query.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtl8192d_xmit.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/usb_ops.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/farray.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_cmd.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_ioctl_rtl.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/sdio_ops.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/recv_osdep.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/Hal8192DPhyCfg.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_iol.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/rtw_security.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/include/osdep_service.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_phycfg.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_sreset.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_mp.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_cmd.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_rf6052.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_rxdesc.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/rtl8192cu_recv.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/usb_ops_xp.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/usb_ops_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/usb_halinit.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/usb_ops_ce.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/Hal8192CUHWImg.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/rtl8192cu_led.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/usb/rtl8192cu_xmit.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_dm.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192c/rtl8192c_hal_init.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/hal_init.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_cmd.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_mp.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_rxdesc.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_hal_init.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_rf6052.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/rtl8192du_recv.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/usb_ops_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/rtl8192du_led.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/usb_halinit.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/rtl8192du_xmit.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/Hal8192DUHWImg.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/usb/Hal8192DUTestHWImg.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_dm.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/hal/rtl8192d/rtl8192d_phycfg.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/ifcfg-wlan0
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/autoconf_rtl8192d_usb_linux.h
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/sdio_intf.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/os_intfs.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/usb_intf.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/xmit_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/pci_intf.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/ioctl_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/recv_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/linux/mlme_linux.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/os_dep/osdep_service.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_recv.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_ioctl_query.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_eeprom.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_mlme.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_ioctl_rtl.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_rf.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_br_ext.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_iol.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_mp_ioctl.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_debug.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_io.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_p2p.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_cmd.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/efuse/
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/efuse/rtw_efuse.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_ioctl_set.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_security.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_mlme_ext.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_mp.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_xmit.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_pwrctrl.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_wlan_util.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_sta_mgt.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/core/rtw_ieee80211.c
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/make_drv
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213/Makefile
 rtl8188C_8192C_8192D_usb_linux_v3.3.1_3083.20111213
 Please select card type(1/2):
 1) RTL8192cu
 2) RTL8192du
 #? 1
 You have selected RTL8192cu
 rtw_version.h has existed!
 Authentication requested [root] for make clean:
 bash: make: command not found
 Authentication requested [root] for make driver:
 bash: make: command not found
 ##################################################
 Compile make driver error: 127
 Please check error Mesg
 ##################################################
 computer@computer-Dell-DXC051:~/Desktop/Realtek driver/RTL8188C_8192C_8192D_USB_linux_v3.3.1_3083.20111213$ ^C
 computer@computer-Dell-DXC051:~/Desktop/Realtek driver/RTL8188C_8192C_8192D_USB_linux_v3.3.1_3083.20111213$  
 
```
```
computer@computer-Dell-DXC051:~$ sudo gedit /etc modprobe.d/blacklist.conf
 [sudo] password for computer:  
 sudo: gedit: command not found
     computer@computer-Dell-DXC051:~$

```
> **gdselzer said:**
> The driver provided in the distribution appears to be broken.  In order to get this to work, follow the instructions here:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

The most recent version of the driver no longer requires Step 3 of the instructions in the linked page.  I've got mine up and running.  However, I can't figure out how to get the bitrate above 72Mb/s.  Has anyone figured out how to get the full 150Mb/s?

---

### Post by gps123 on 2011-12-31
> **inobe said:**
> go into network manager> manage connections> hit wireless tab> delete all your connections> restart> attempt to connect to just one access point.

Just tried this, no dice.

---

### Post by gdselzer on 2011-12-31
gps, you need to install the compiling tools before running install.sh

> sudo apt-get install build-essential

Also, gedit is the editor in gnome.  With kubuntu you need to use kate.

---

### Post by gps123 on 2012-01-01
Okay, that makes sense (gedit:kate::gnome:KDE).  I tried to edit the blacklist using Kate, but I can't save the file...apparently I don't have permission, or the file is read only.  Any suggestions?

---

### Post by gdselzer on 2012-01-01
Did you use "sudo"?

> sudo kate /etc/modprobe.d/blacklist.conf

---

