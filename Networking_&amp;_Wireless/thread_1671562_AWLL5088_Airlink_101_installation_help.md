---
title: "AWLL5088 Airlink 101 installation help"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by dBuster on 2011-01-20
I have searched the forums and followed the directions for the other airlink usb adapters and still no luck getting this one up and running.

Here is my dmesg after inserting these are the new lines.

[ 4632.987427] usb 2-3: USB disconnect, address 2
[ 4638.608035] usb 2-3: new high speed USB device using ehci_hcd and address 4
[ 4638.741909] usb 2-3: configuration #1 chosen from 1 choice

lsusb gives me this:

david@david-laptop:~$ lsusb
Bus 002 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device


I have tried the [HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101) and followed those directions but still nothing.

Any help would be appreciated.

---

### Post by dBuster on 2011-01-20
Okay so I have downloaded the realtek drivers and did the make, and sudo make install and then all went to garbage...

KERNEL Panic!!  Rebooted same kernel panic! 

Took out the USB wifi airlink101 and rebooted, my built in atheros card now is not working, compiled and installed those drivers, rebooted and now I am back at least with the atheros G wifi.

So I am back now to not having the new wireless N functioning...  Any ideas?

Oh and by the way the lsusb -v output shows the wireless N adapter as shown here

> Bus 002 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8176 
  bcdDevice            2.00
  iManufacturer           1 Realtek
  iProduct                2 Wireless N USB Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


---

### Post by dBuster on 2011-02-06
After almost giving up I decided to go to the "[Supported wireless cards list and procedure to get help.](http://ubuntuforums.org/showthread.php?t=370108)" thread once again and try one more time.

Went to the [wiki](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) of supported cards and selected [Airlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101).  It still lists "Download kernel module sources from 'Realtek' (current filename: 'RTL8188CUS_v2.0.1212.zip'), extract to /usr/src , and run install.sh" for this super nano N usb adapter.  However, after going to the [Realtek](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742) page I noticed that there is a different version now available!  

**NOTE THE WIKI has been updated with the new current version and the link as well.**

> 	Version	Update
Linux driver for Kernel 2.6.x	2.0.1324	2011/1/28	2226k

Link to driver:  [RTL8188CUS - Linux driver](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

Downloaded that version and followed the directions to extract it to the /usr/src folder and then ran the install.sh and to my shock and awe the wireless adapter sprung to life!

Sure then I had a little conflict with the internal wifi still being on and trying to keep control.  Both by the way would connect and work at the same time.  But for my sake of sanity I hit the wifi button on the laptop that is supposed to turn off the internal and although the light kept going the internal shut off.  Now several boots later and I am solely using this new N adapter!

I must say it is stronger to connect to my home wifi however it doesn't see as many access points in the neighborhood as the internal wifi had.  Not sure why but as long as I can connect to my home setup I am ecstatic!

So for anyone looking into the [Airlink101 AWLL5088]("http://www.amazon.com/AirLink101-AWLL5088-Wireless-Ultra-Adapter/dp/B003X26PMO/ref=sr_1_2?ie=UTF8&qid=1296994300&sr=8-2") adapter It is a great way of adding N for those who are looking at running N but have an antiquated internal card that can't be upgraded.  Especially for only $16.00!

---

### Post by ibootindos on 2011-03-20
> **dBuster said:**
> After almost giving up I decided to go to the "[Supported wireless cards list and procedure to get help.](http://ubuntuforums.org/showthread.php?t=370108)" thread once again and try one more time.

Went to the [wiki](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) of supported cards and selected [Airlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101).  It still lists "Download kernel module sources from 'Realtek' (current filename: 'RTL8188CUS_v2.0.1212.zip'), extract to /usr/src , and run install.sh" for this super nano N usb adapter.  However, after going to the [Realtek](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742) page I noticed that there is a different version now available!  

**NOTE THE WIKI has been updated with the new current version and the link as well.**



Link to driver:  [RTL8188CUS - Linux driver](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

Downloaded that version and followed the directions to extract it to the /usr/src folder and then ran the install.sh and to my shock and awe the wireless adapter sprung to life!

Sure then I had a little conflict with the internal wifi still being on and trying to keep control.  Both by the way would connect and work at the same time.  But for my sake of sanity I hit the wifi button on the laptop that is supposed to turn off the internal and although the light kept going the internal shut off.  Now several boots later and I am solely using this new N adapter!

I must say it is stronger to connect to my home wifi however it doesn't see as many access points in the neighborhood as the internal wifi had.  Not sure why but as long as I can connect to my home setup I am ecstatic!

So for anyone looking into the [Airlink101 AWLL5088]("http://www.amazon.com/AirLink101-AWLL5088-Wireless-Ultra-Adapter/dp/B003X26PMO/ref=sr_1_2?ie=UTF8&qid=1296994300&sr=8-2") adapter It is a great way of adding N for those who are looking at running N but have an antiquated internal card that can't be upgraded.  Especially for only $16.00!

I downloaded the driver, and put it in the usr/src directory, but I'm not sure how to install it correctly? could somebody walk me through it?

---

### Post by dBuster on 2011-03-23
> **ibootindos said:**
> I downloaded the driver, and put it in the usr/src directory, but I'm not sure how to install it correctly? could somebody walk me through it?

According to the directions you were to have :

> extract to /usr/src , and run install.sh

So you have extracted to the /usr/src folder, but have you ran install.sh file???  You may have to right click on the folder and change it to be an executable file first.  

That install script was what did the trick for me!

---

### Post by wgarider on 2011-05-01
Thanks to ibootindos and everyone for the solution - that worked great!

---

### Post by ralfarof on 2011-05-02
This doesn't work anymore with Natty :(

I get this output:

```
root@RICARDO-UBUNTU:/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402# bash install.sh
		Auto install for 8192cu
		September, 1 2010 v 1.0.0
rtl8192CU_linux_v2.0.1502.20110402/
rtl8192CU_linux_v2.0.1502.20110402/autoconf_rtl8192c_usb_linux.h
rtl8192CU_linux_v2.0.1502.20110402/clean
rtl8192CU_linux_v2.0.1502.20110402/core/
rtl8192CU_linux_v2.0.1502.20110402/core/efuse/
rtl8192CU_linux_v2.0.1502.20110402/core/efuse/rtl8712_efuse.c
rtl8192CU_linux_v2.0.1502.20110402/core/ieee80211.c
rtl8192CU_linux_v2.0.1502.20110402/core/led/
rtl8192CU_linux_v2.0.1502.20110402/core/led/rtl8192c_led.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_cmd.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_debug.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_eeprom.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_io.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_ioctl_query.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_ioctl_rtl.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_ioctl_set.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mlme.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mlme_ext.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mp.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mp_ioctl.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_pwrctrl.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_recv.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_rf.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_security.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_sta_mgt.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_wlan_util.c
rtl8192CU_linux_v2.0.1502.20110402/core/rtw_xmit.c
rtl8192CU_linux_v2.0.1502.20110402/hal/
rtl8192CU_linux_v2.0.1502.20110402/hal/hal_init.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_dm.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_halinit.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c_d_hal_init.c
rtl8192CU_linux_v2.0.1502.20110402/ifcfg-wlan0
rtl8192CU_linux_v2.0.1502.20110402/include/
rtl8192CU_linux_v2.0.1502.20110402/include/autoconf.h
rtl8192CU_linux_v2.0.1502.20110402/include/basic_types.h
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/big_endian.h
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/generic.h
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/little_endian.h
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/swab.h
rtl8192CU_linux_v2.0.1502.20110402/include/byteorder/swabb.h
rtl8192CU_linux_v2.0.1502.20110402/include/circ_buf.h
rtl8192CU_linux_v2.0.1502.20110402/include/cmd_osdep.h
rtl8192CU_linux_v2.0.1502.20110402/include/drv_conf.h
rtl8192CU_linux_v2.0.1502.20110402/include/drv_types.h
rtl8192CU_linux_v2.0.1502.20110402/include/drv_types_ce.h
rtl8192CU_linux_v2.0.1502.20110402/include/drv_types_linux.h
rtl8192CU_linux_v2.0.1502.20110402/include/drv_types_xp.h
rtl8192CU_linux_v2.0.1502.20110402/include/ethernet.h
rtl8192CU_linux_v2.0.1502.20110402/include/farray.h
rtl8192CU_linux_v2.0.1502.20110402/include/h2clbk.h
rtl8192CU_linux_v2.0.1502.20110402/include/Hal8192CPhyCfg.h
rtl8192CU_linux_v2.0.1502.20110402/include/Hal8192CPhyReg.h
rtl8192CU_linux_v2.0.1502.20110402/include/Hal8192CUHWImg.h
rtl8192CU_linux_v2.0.1502.20110402/include/HalRf.h
rtl8192CU_linux_v2.0.1502.20110402/include/hal_init.h
rtl8192CU_linux_v2.0.1502.20110402/include/ieee80211.h
rtl8192CU_linux_v2.0.1502.20110402/include/ieee80211_ext.h
rtl8192CU_linux_v2.0.1502.20110402/include/if_ether.h
rtl8192CU_linux_v2.0.1502.20110402/include/ip.h
rtl8192CU_linux_v2.0.1502.20110402/include/mlme_osdep.h
rtl8192CU_linux_v2.0.1502.20110402/include/mp_custom_oid.h
rtl8192CU_linux_v2.0.1502.20110402/include/nic_spec.h
rtl8192CU_linux_v2.0.1502.20110402/include/osdep_ce_service.h
rtl8192CU_linux_v2.0.1502.20110402/include/osdep_intf.h
rtl8192CU_linux_v2.0.1502.20110402/include/osdep_service.h
rtl8192CU_linux_v2.0.1502.20110402/include/recv_osdep.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_cmd.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_dm.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_event.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_hal.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_recv.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_spec.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8192c_xmit.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_bitdef.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_cmd.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_efuse.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_event.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_hal.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_recv.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_regdef.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_rf.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_spec.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtl8712_xmit.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_byteorder.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_cmd.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_debug.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_eeprom.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_event.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_ht.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_io.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_ioctl.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_ioctl_query.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_ioctl_rtl.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_ioctl_set.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_led.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_mlme.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_mlme_ext.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_mp.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_mp_ioctl.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_mp_phy_regdef.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_pwrctrl.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_qos.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_recv.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_rf.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_security.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_version.h
rtl8192CU_linux_v2.0.1502.20110402/include/rtw_xmit.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_hal.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_ops.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_ops_ce.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_ops_linux.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_ops_xp.h
rtl8192CU_linux_v2.0.1502.20110402/include/sdio_osintf.h
rtl8192CU_linux_v2.0.1502.20110402/include/sta_info.h
rtl8192CU_linux_v2.0.1502.20110402/include/usb_hal.h
rtl8192CU_linux_v2.0.1502.20110402/include/usb_ops.h
rtl8192CU_linux_v2.0.1502.20110402/include/usb_osintf.h
rtl8192CU_linux_v2.0.1502.20110402/include/usb_vendor_req.h
rtl8192CU_linux_v2.0.1502.20110402/include/version.h
rtl8192CU_linux_v2.0.1502.20110402/include/wifi.h
rtl8192CU_linux_v2.0.1502.20110402/include/wlan_bssdef.h
rtl8192CU_linux_v2.0.1502.20110402/include/xmit_osdep.h
rtl8192CU_linux_v2.0.1502.20110402/Kconfig
rtl8192CU_linux_v2.0.1502.20110402/Makefile
rtl8192CU_linux_v2.0.1502.20110402/os_dep/
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/ioctl_linux.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/mlme_linux.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/os_intfs.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/recv_linux.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/sdio_intf.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/xmit_linux.c
rtl8192CU_linux_v2.0.1502.20110402/os_dep/osdep_service.c
rtl8192CU_linux_v2.0.1502.20110402/runwpa
rtl8192CU_linux_v2.0.1502.20110402/wlan0dhcp
rtl8192CU_linux_v2.0.1502.20110402/wpa1.conf
rtl8192CU_linux_v2.0.1502.20110402
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.38-8-generic/build M=/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_cmd.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_security.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_debug.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_io.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_ioctl_query.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_ioctl_set.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/ieee80211.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mlme.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_mlme_ext.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_wlan_util.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_pwrctrl.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_rf.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_recv.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_sta_mgt.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/rtw_xmit.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/efuse/rtl8712_efuse.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/core/led/rtl8192c_led.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/hal_init.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c_d_hal_init.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.o
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.c: In function ‘SetFwRsvdPagePkt’:
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.c:2105:3: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.c: In function ‘set_FwJoinBssReport_cmd’:
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/hal/rtl8192c/usb/rtl8192c_cmd.c:2184:2: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/osdep_service.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/os_intfs.o
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.o
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.c: In function ‘rtw_drv_init’:
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.c:1038:23: error: ‘struct usb_device’ has no member named ‘autosuspend_delay’
make[2]: *** [/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.o] Error 1
make[1]: *** [_module_/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg

```

---

### Post by ralfarof on 2011-05-02
I send an email to Realtek support, if I get an answer I'll post it here.

---

### Post by eternicode on 2011-05-04
dBuster, did you get this working on 32-bit or 64-bit?  I'm having a hard time finding a mini usb wifi adapter that will work on 64-bit.  Last one I bought worked great on 32-bit, but is all sorts of fail on 64-bit, unfortunately.

ralfarof, Natty (and its 2.6.38 kernel) have made changes that cause old drivers to fail the build process -- if you have the know-how, you can probably hunt the errors down and get it to build, but it's not easy :/

---

### Post by freewindster on 2011-05-04
Onieric Driver:[AWLL5088 Onieric 32/64bit v3.0.2590 Driver]("https://docs.google.com/leaf?id=0B0KPZ5M7yZxQMjdmYWY3YzMtYWFkYS00MzE0LWFmNzAtMWZhOTE0YzZmMTI3&hl=en_US") 

The latest sources from Realtek will compile for Natty.
The driver package is for RTL8188CUS.
[Realtek wireless NIC Drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

OR

Below is link to latest driver package that will automatically update with each new kernel update.
Link to driver:[Airlink AWLL5088 Natty 32/64bit v3.0.2164 Driver]("https://docs.google.com/leaf?id=0B0KPZ5M7yZxQZDNjN2UwZWEtMjg3My00MjZkLWJkNmEtMjU3YzkwMWY2YzI0&hl=en_US")
Previous Versions:
[version 2.0.1502]("https://docs.google.com/leaf?id=0B0KPZ5M7yZxQYjE0MWM2ZjQtYWUzNC00ZDViLTgwYmUtMDg2Y2JkM2YzNGM1&hl=en_US")
[version 3.0.1590]("https://docs.google.com/leaf?id=0B0KPZ5M7yZxQOWNmNzJhN2EtZDJiNC00MTNkLWEzYWItZTY3ZmYyNTEwNjUw&hl=en_US")


Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

(Be sure to substitute file name below with the version you downloaded.)

	sudo apt-get install dkms linux-headers-generic 
	tar xvf Airlink_AWLL5088_Natty_Driver-v_3.0.2164.tar.gz
	cd  Airlink_AWLL5088_Natty_Driver-v_3.0.2164/
	./install-with-dkms.sh

To remove from dkms use:
	./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.

---

### Post by eternicode on 2011-05-04
> **freewindster said:**
> This one should compile for Natty.

Awesome, that worked for the other card I mentioned (it was an 8192cu, while the Airlink is, afaik, an 8192cus), thanks!

---

### Post by ralfarof on 2011-05-05
> **eternicode said:**
> dBuster, did you get this working on 32-bit or 64-bit?  I'm having a hard time finding a mini usb wifi adapter that will work on 64-bit.  Last one I bought worked great on 32-bit, but is all sorts of fail on 64-bit, unfortunately.

ralfarof, Natty (and its 2.6.38 kernel) have made changes that cause old drivers to fail the build process -- if you have the know-how, you can probably hunt the errors down and get it to build, but it's not easy :/

that's what I suspected :)

---

### Post by ralfarof on 2011-05-05
> **freewindster said:**
> This one should compile for Natty.

Link to driver:[Airlink AWLL5088 Natty 32/64bit Driver]("http://ubuntuone.com/p/qhv/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

	sudo apt-get install dkms linux-headers-generic 
	tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
	cd  Airlink_AWLL5088_Natty_Driver/
	./install-with-dkms.sh

To remove from dkms use:
	./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.  

There is an autosuspend-changes.txt file inside archive that details what I changed to get it to 
compile. I may have did it wrong but it does work.


I owe you a beer!!! it worked like a charm :guitar:

---

### Post by JohnnyLongarms on 2011-05-10
> **freewindster said:**
> This one should compile for Natty.

Link to driver:[Airlink AWLL5088 Natty 32/64bit Driver]("http://ubuntuone.com/p/qhv/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

    sudo apt-get install dkms linux-headers-generic 
    tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
    cd  Airlink_AWLL5088_Natty_Driver/
    ./install-with-dkms.sh

To remove from dkms use:
    ./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.  

There is an autosuspend-changes.txt file inside archive that details what I changed to get it to 
compile. I may have did it wrong but it does work.

Did you ever knooooooow that you're my heeeeeeeroooooooooo?

Thanks so much for this, I have been at this for hours.

---

### Post by twister65 on 2011-05-12
> **freewindster said:**
> This one should compile for Natty.

Link to driver:[Airlink AWLL5088 Natty 32/64bit Driver]("http://ubuntuone.com/p/qhv/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

	sudo apt-get install dkms linux-headers-generic 
	tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
	cd  Airlink_AWLL5088_Natty_Driver/
	./install-with-dkms.sh

To remove from dkms use:
	./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.  

There is an autosuspend-changes.txt file inside archive that details what I changed to get it to 
compile. I may have did it wrong but it does work.

hi!

this also works on Ubuntu 11.04 with the Digitus Wireless 150N USB 2.0 Adapter DN-7042 with Realtek 8188CUS chip

Thanks!

---

### Post by igor24 on 2011-05-20
> **freewindster said:**
> This one should compile for Natty.

Link to driver:[Airlink AWLL5088 Natty 32/64bit Driver]("http://ubuntuone.com/p/qhv/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

    sudo apt-get install dkms linux-headers-generic 
    tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
    cd  Airlink_AWLL5088_Natty_Driver/
    ./install-with-dkms.sh

To remove from dkms use:
    ./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.  

There is an autosuspend-changes.txt file inside archive that details what I changed to get it to 
compile. I may have did it wrong but it does work.


IT WORKS!!! Thanks for your help man. That's my very first time using Linux, so it took me a bit to figure everything out (since I'm not familiar with UNIX at all...) but I made it. Installed it on my old IBM Thinkpad T23, decided to give Ubuntu a try and I'm glad I did it. My Airlink now works and everything runs much faster than on Windows7. 
Greetings from Brazil.

---

### Post by dBuster on 2011-05-23
> **eternicode said:**
> dBuster, did you get this working on 32-bit or 64-bit?  I'm having a hard time finding a mini usb wifi adapter that will work on 64-bit.  Last one I bought worked great on 32-bit, but is all sorts of fail on 64-bit, unfortunately.

ralfarof, Natty (and its 2.6.38 kernel) have made changes that cause old drivers to fail the build process -- if you have the know-how, you can probably hunt the errors down and get it to build, but it's not easy :/

It compiled on 64bit for me without a problem...

I know though that when trying to keep both the internal on and the mini usb together I have issues.  As long as only one is one there is no problem...

---

### Post by freewindster on 2011-05-23
The latest sources from Realtek will compile for Natty.
The driver package is for RTL8188CUS version 3.0.2164.
[Realtek wireless NIC Drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by Amish_Gramish on 2011-05-25
After forcing my computer to unzip in /usr/src/ (I had to find the way to forcefully change the file permissions, as apparently I didn't have the proper authority), I ran install.sh, but wireless still doesn't work.

(I ran install.sh [after navigating with cd /usr/src/Realtekfoldername] with "sudo sh ./install.sh)

I have a Compaq Presario F572US, 64-bit, running 11.04.

It will recognize the access points, but when I try to connect (after putting in the password), it just keeps spinning and after a while it says, "Wireless disconnected."

I first installed the Airlink driver, then when it had the aforementioned problem, I installed the latest Realtek driver, but it kept doing the same thing.

Is there another way to get it working, amidoinitwrong, or is there some step I'm missing?

---

### Post by ralfarof on 2011-05-25
> **Amish_Gramish said:**
> After forcing my computer to unzip in /usr/src/ (I had to find the way to forcefully change the file permissions, as apparently I didn't have the proper authority), I ran install.sh, but wireless still doesn't work.

(I ran install.sh [after navigating with cd /usr/src/Realtekfoldername] with "sudo sh ./install.sh)

I have a Compaq Presario F572US, 64-bit, running 11.04.

It will recognize the access points, but when I try to connect (after putting in the password), it just keeps spinning and after a while it says, "Wireless disconnected."

I first installed the Airlink driver, then when it had the aforementioned problem, I installed the latest Realtek driver, but it kept doing the same thing.

Is there another way to get it working, amidoinitwrong, or is there some step I'm missing?

When I installed mine, a single "sudo ./install.sh" didn't worked, I used "sudo -s" instead of "sudo" and then "./install.sh" as root.

Please correct me if I'm wrong.

---

### Post by Amish_Gramish on 2011-05-26
> **ralfarof said:**
> When I installed mine, a single "sudo ./install.sh" didn't worked, I used "sudo -s" instead of "sudo" and then "./install.sh" as root.

Please correct me if I'm wrong.

It looked like everything went as it was supposed to when I used "sudo sh ./install.sh," but that could have been the problem.

I'm not able to use "sudo -s ./install.sh" because the files are protected.  (11.04 is truly turning out to be Ubuntu Vista.)  And the only way I can run the ./install.sh file is by "sudo sh ./install".

I also don't know that much about running Ubuntu, so I could very well be doing something wrong.

It looks like other people aren't having any troubles with this in 10.04, and it doesn't really matter to me much if I downgrade.  So, can anyone confirm that this works on a 10.04 64-bit computer?  Or is this a problem with all 64-bit computers?

---

### Post by freewindster on 2011-05-26
Try going back to version 2.0.1502. I've been having problems with the latest version from realtek. It Keeps my dell mini 9 from resuming after suspend.

[2.0.1502 driver]("http://ubuntuone.com/p/vkh/")

---

### Post by dBuster on 2011-05-27
> **Amish_Gramish said:**
> It looked like everything went as it was supposed to when I used "sudo sh ./install.sh," but that could have been the problem.

I'm not able to use "sudo -s ./install.sh" because the files are protected.  (11.04 is truly turning out to be Ubuntu Vista.)  And the only way I can run the ./install.sh file is by "sudo sh ./install".

I also don't know that much about running Ubuntu, so I could very well be doing something wrong.

It looks like other people aren't having any troubles with this in 10.04, and it doesn't really matter to me much if I downgrade.  So, can anyone confirm that this works on a 10.04 64-bit computer?  Or is this a problem with all 64-bit computers?

I was able to compile and run with just the sudo ./install.sh so I am not sure why you were not able to.  

I am not having any issues with running this driver in 10.04 64 bit what so ever.  Where I do run into problems is when I have the internal wireless enabled that is when I have problems.  If it is disabled the Airlink 101 mini usb functions amazing!

You could, if you are having issues, try a prior version as what was recommended.  Might be something about the hardware your using that is causing issues...  Hence try a prior version...

---

### Post by Amish_Gramish on 2011-06-01
> **freewindster said:**
> Try going back to version 2.0.1502. I've been having problems with the latest version from realtek. It Keeps my dell mini 9 from resuming after suspend.

[2.0.1502 driver]("http://ubuntuone.com/p/vkh/")

I installed this version of the driver with 11.04, then downgraded to 10.04.2, then installed the most current Realtek version and it didn't work.

It still identifies the signal, but never connects.  It always just runs around in a circle.

And the wireless card in the Compaq F572US is defective, so I can't use the internal wireless card.

I'm going to try to use 10.04.2 32 Bit to see if it finally works.

EDIT:

Oh yeah!  I'm so excited!
It finally works!
Ubuntu 10.04.2 32 bit using the latest Realtek driver works!

I pretty much did this:
sudo -i (because my laptop never lets me edit anything unless I run it as Terminal as root)
unzip /home/USERNAME/Desktop/RTL8188CUS_linux_v3.0.1590.20110511.zip -d /usr/src/
cd /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/
sudo sh ./install.sh

And then it worked perfectly!

From what I've read, the D-Link DWA 160 runs automatically without having to do any messing around inside Ubuntu, but this one is much harder to break in two.  And it costs about $35 less on Amazon.com.

---

### Post by jaideepn on 2011-06-04
I installed the driver exactly as specified. I also get the "Network Disconnected" popup when I remove the usb adapter, but Network Manager still says that hardware switch is off and the wireless options are greyed out.

I'm using 11.04 64-bit system.

Thanks!

---

### Post by slowcoffee on 2011-06-13
> **freewindster said:**
> The latest sources from Realtek will compile for Natty.
The driver package is for RTL8188CUS.
[Realtek wireless NIC Drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

OR

Below is link to latest driver package that will automatically update with each new kernel update.
Link to driver:[Airlink AWLL5088 Natty 32/64bit v3.0.1590 Driver]("http://ubuntuone.com/p/vCY/")
Previous Version:[version 2.0.1502]("http://ubuntuone.com/p/vkh/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

    sudo apt-get install dkms linux-headers-generic 
    tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
    cd  Airlink_AWLL5088_Natty_Driver/
    ./install-with-dkms.sh

To remove from dkms use:
    ./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.

Awesome! As a new Ubuntu user, this was extremely useful for me. Thank you.

---

### Post by paulyxx9 on 2011-06-16
I am a newbie here and to Ubuntu. When I tried to extract the files I get this message:

You don't have the right permissions to extract archives in the folder "file:///usr/src"

Am I missing something?

---

### Post by ralfarof on 2011-06-17
> **paulyxx9 said:**
> I am a newbie here and to Ubuntu. When I tried to extract the files I get this message:

You don't have the right permissions to extract archives in the folder "file:///usr/src"

Am I missing something?

you won't be able to extract the files in /usr/src unless you are using elevated privileges, try this:

- Extract the files somewhere in you home directory (/home/"YourUserName")
- Then open a Terminal window
- Copy the contents of the extracted files to the /usr/src directory

```
user@computer:~$ sudo cp -R ./Extracted-Driver-folder /usr/src
```

I'll prompt for your user password,

- Then follow freewindster's instructions on this thread

That's it! ;)

---

### Post by pussfeller on 2011-06-27
Hi, you can unload the module before the suspend by:

```
sudo vim /etc/pm/sleep.d/10_remove-troublesome-drivers

```
and paste the following, or something like it

```
#!/bin/sh
# remove 8192cu drivers and reload upon wake

case "$1" in 
	hibernate|suspend)
		rmmod 8192cu
		;;
	resume|thaw)
		modprobe 8192cu
		;;
esac
```

then 

```
sudo chmod +x /etc/pm/sleep.d/10_remove-troublesome-drivers
```

Verify by watching the pm-suspend log in /var/log

You can add 'service bluetooth stop' and 'service bluetooth restart', too, if you have probs with bluetooth after suspend.

That seems to have fixed my suspend probs using the latest driver, and I know there is a better way to do it, but I don't know exactly what it is, but hey it works

---

### Post by Eleaglesrock on 2011-07-02
Can some please help Me. I'm a total n00b to Linux and keep getting error messages after everything I try. I am running 10.10

---

### Post by Eleaglesrock on 2011-07-03
i ended up using windows driver through NDISwrapper. so far it works like a charm.

---

### Post by dark ariel7 on 2011-07-04
> **freewindster said:**
> The latest sources from Realtek will compile for Natty.
The driver package is for RTL8188CUS.
[Realtek wireless NIC Drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

OR

Below is link to latest driver package that will automatically update with each new kernel update.
Link to driver:[Airlink AWLL5088 Natty 32/64bit v3.0.1590 Driver]("http://ubuntuone.com/p/vCY/")
Previous Version:[version 2.0.1502]("http://ubuntuone.com/p/vkh/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

	sudo apt-get install dkms linux-headers-generic 
	tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
	cd  Airlink_AWLL5088_Natty_Driver/
	./install-with-dkms.sh

To remove from dkms use:
	./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.

I am an absolute linux noob please someone walk me through this. How do i install the driver after i downloaded it?

thanks in advance for any help:D

---

### Post by dark ariel7 on 2011-07-07
nvm on my last post, but i do need help installing it on lubuntu.

---

### Post by PeRKoniX on 2011-10-08
> **freewindster said:**
> The latest sources from Realtek will compile for Natty.
The driver package is for RTL8188CUS.
[Realtek wireless NIC Drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

OR

Below is link to latest driver package that will automatically update with each new kernel update.
Link to driver:[Airlink AWLL5088 Natty 32/64bit v3.0.1590 Driver]("http://ubuntuone.com/p/vCY/")
Previous Version:[version 2.0.1502]("http://ubuntuone.com/p/vkh/")

Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

	sudo apt-get install dkms linux-headers-generic 
	tar xvf Airlink_AWLL5088_Natty_Driver.tar.gz
	cd  Airlink_AWLL5088_Natty_Driver/
	./install-with-dkms.sh

To remove from dkms use:
	./remove-from-dkms.sh

The install.sh script from "Realtek" still works but wont recompile autmatically for each new kernel.


Someone still have this driver? Cannot seem to find it anywhere :(

---

### Post by freewindster on 2011-10-08
> **PeRKoniX said:**
> Someone still have this driver? Cannot seem to find it anywhere :(

I updated my post with links to latest driver.
[http://ubuntuforums.org/showpost.php?p=10766989&postcount=10]("http://ubuntuforums.org/showpost.php?p=10766989&postcount=10")

---

### Post by sgo. on 2011-10-19
Hi. I tried to install this driver on my girlfriends laptop. She's running Oneiric Ocelot (11.10) and we can't install it. It always exits with error message [2], doesn't matter if I use freewindster's script or the normal install.sh. I used the newest driver, 3.1.2590, from the Realtek homepage and modified freewindster's script.

I also tried installing the drivers on my machine, as I'm running a similar setup with Oneiric. I tried to instell freewindester's original script with his drivers, my modified script with the newest version of the driver, and installing the newest version manual from within /usr/src/, nothing worked. I always get Error 2 when compiling the driver. Here the error msg when I try to install it per install.sh:

```
Authentication requested [root] for make driver:
[: 18: unexpected operator
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.0.0-12-generic/build M=/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o
In file included from /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.c:24:0:
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg

```


Also, somehow the stick worked on my laptop when I disabled my internal Wifi card in the BIOS menu. I guess in the 3.x kernel are some opensource drivers that work with this chipset OOTB?! But I can't do that on my girlfriends laptop. Any suggestions how I could disable her internal card?


Anyway, hope you guys can help me somehow. Thanks in advance.

---

### Post by freewindster on 2011-10-19
I updated my post [http://ubuntuforums.org/showpost.php?p=10766989&postcount=10]("http://ubuntuforums.org/showpost.php?p=10766989&postcount=10") to include Onieric driver.

Have not fully tested.

---

### Post by ralfarof on 2011-10-19
> **sgo. said:**
> Hi. I tried to install this driver on my girlfriends laptop. She's running Oneiric Ocelot (11.10) and we can't install it. It always exits with error message [2], doesn't matter if I use freewindster's script or the normal install.sh. I used the newest driver, 3.1.2590, from the Realtek homepage and modified freewindster's script.

I also tried installing the drivers on my machine, as I'm running a similar setup with Oneiric. I tried to instell freewindester's original script with his drivers, my modified script with the newest version of the driver, and installing the newest version manual from within /usr/src/, nothing worked. I always get Error 2 when compiling the driver. Here the error msg when I try to install it per install.sh:

```
Authentication requested [root] for make driver:
[: 18: unexpected operator
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.0.0-12-generic/build M=/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o
In file included from /usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.c:24:0:
/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/usr/src/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg

```


Also, somehow the stick worked on my laptop when I disabled my internal Wifi card in the BIOS menu. I guess in the 3.x kernel are some opensource drivers that work with this chipset OOTB?! But I can't do that on my girlfriends laptop. Any suggestions how I could disable her internal card?


Anyway, hope you guys can help me somehow. Thanks in advance.

I think the problem is that 11.10 uses kernel 3.0, the driver install script makes reference to kernel 2.x.x, fixing it shouldn't be a problem

---

### Post by sgo. on 2011-10-19
It built on my laptop. Thanks a lot!!! :-)
Can't try if it actually works yet, gotta wait until I get a chance to try that on my gf's laptop or at least until I get her WiFi stick. I'll tell you asap. But as I said, now it built! Thanks again! :)

---

### Post by sgo. on 2011-10-20
Ok, following problems. Before I was able to install the driver on my gf's laptop, the latter all of a sudden didn't want to recognize any wifi card anymore. It always says "unavailable" and won't let you turn on the card anymore. Any ideas what could cause that?

Then, after installing the driver on my laptop I tried to use her Airlink stick today. It would find networks, but wouldn't connect. I disabled my internal Wifi card, so that is not the problem. And as it seems, some OSS drivers worked before (as I already mentioned, although I couldn't install the drivers, I was able to connect to networks and surf the web pretty good). Any suggestions what's the matter with that? The driver compiled without any errors this time and the Airlink finds networks. So what's wrong with it?

Thanks for your help!


//Update: I found out why both network cards were disabled. My GF has a dualboot with windows 7. There I disabled the internal wifi card. But this prevented ubuntu to use BOTH cards, the internal PCI and the external USB. Any ideas why?

---

### Post by sgo. on 2011-10-21
Ok, just to clarify some things.

To make the new USB wlan stick work at least in Windows (and Ubuntu), I now disabled the internal antenna in Windows 7 in the device manager. But I did NOT disable it by pressing the Wifi On/Off button on her laptop. Combined, that will deactivate both cards in Ubuntu. Go figure!

In Ubuntu, I blacklisted the driver for the internal antenna. There was no other possibility to get rid of it. ifdown and others wouldn't do anything or disable BOTH adapters, the internal and external. I tried blacklisting the internal adapter for the network manager, but still had problems with the connection.
Unfortunately, the Realtek driver still doesn't work (I had to blacklist that one too, so I'm using an opensource driver with just bad signal quality/strength). As I already described, it finds the networks, seems to have great signal strength but is not able to connect. It would just say "connect" and then sit there. Once I get this somehow to work (and your help/knowledge here is really appreciated and needed), I will try remove the internal driver from the blacklist again and hope it works. Why would I do that? Because I want to try to shut it down somehow, to save energy.

Ok, that said I hope someone can help with that driver issue. I'm pretty sad that my GF's first experience with Ubuntu is like that. ..

---

### Post by artshark on 2011-10-27
> **sgo. said:**
> Ok, just to clarify some things.

To make the new USB wlan stick work at least in Windows (and Ubuntu), I now disabled the internal antenna in Windows 7 in the device manager. But I did NOT disable it by pressing the Wifi On/Off button on her laptop. Combined, that will deactivate both cards in Ubuntu. Go figure!

In Ubuntu, I blacklisted the driver for the internal antenna. There was no other possibility to get rid of it. ifdown and others wouldn't do anything or disable BOTH adapters, the internal and external. I tried blacklisting the internal adapter for the network manager, but still had problems with the connection.
Unfortunately, the Realtek driver still doesn't work (I had to blacklist that one too, so I'm using an opensource driver with just bad signal quality/strength). As I already described, it finds the networks, seems to have great signal strength but is not able to connect. It would just say "connect" and then sit there. Once I get this somehow to work (and your help/knowledge here is really appreciated and needed), I will try remove the internal driver from the blacklist again and hope it works. Why would I do that? Because I want to try to shut it down somehow, to save energy.

Ok, that said I hope someone can help with that driver issue. I'm pretty sad that my GF's first experience with Ubuntu is like that. ..
How do I install the oneric tarball?
How do I blacklist the internal WLAN?
Thanks!
Art

---

### Post by hugo_koopmans on 2011-11-06
Hi Guys,

Thanks for the post, the install script seems to work for me... i did not copy to the usr/... location

just run the install script with sudo ./install.sh (make it executable first by changing permissions)

hugo

---

### Post by brec on 2011-12-23
Not SOLVED for me.

> **freewindster said:**
> Below is link to latest driver package that will automatically update with each new kernel update.
Link to driver:[Airlink AWLL5088 Natty 32/64bit v3.0.2164 Driver]("https://docs.google.com/leaf?id=0B0KPZ5M7yZxQZDNjN2UwZWEtMjg3My00MjZkLWJkNmEtMjU3YzkwMWY2YzI0&hl=en_US")
...


Driver automatically updates for each kernel.
You have to install dkms and header packages, first.

11.04 fresh install and update this evening (with /home on separate partition, so /home not fresh).  Installed dkms, then in the extracted download directory:  sudo install-with-dkms.sh

Install went OK, rebooted with USB device inserted, pop-up reported wireless connection, my SSID was in the menu, was asked for WPA2 key, then panel icon animated as the one on my Mac does when it's looking for SSIDs, then after a while: disconnected.  I've had this same problem with another USB device -- finds networks but doesn't connect.

I really need wireless.  I'm close to installing Windows 7 -- Amazon delivered the CD today [/whine]

---

### Post by brec on 2011-12-25
> **brec said:**
> Not SOLVED for me.
I really need wireless.  I'm close to installing Windows 7 -- Amazon delivered the CD today [/whine]

I DID install WIndows and ... had the same problem!

So I reinstalled Ubuntu 11.04 and ... my WIRED connection acted the same way and wouldn't connect!  Previously it had always connected instantly and been rock solid.

My wired LAN controller is built-in to my motherboard. How could Windows have corrupted my motherboard/BIOS/.../?  I was stumped.  I went to watch TV with my GF, during which ...  EUREKA!   I went back to my office and reset/rebooted the WiFi router/AP.  That was the solution!

I don't know exactly how the router got "tired" but my guess is that all the experimenting of the past couple of weeks, with many DHCP requests, filled an internal table in the router or something like that.

---

### Post by meatballhead on 2012-01-08
[center][COLOR="Red"]**I have an alternative way to install the driver and it works perfectly. I hope it helps any of you. :D**[/COLOR] [B]What I did is download [COLOR="Blue"][Windows driver]("http://www.mediafire.com/?arr7tgl2pfd1emx")[/COLOR]
Install ndisgtk
Install Windows driver through ndiswrapper. And that done the trick:D[/B][/center]

---

### Post by JigglyWiggly_ on 2012-03-17
does this work out of the box with 11.10?

---

### Post by knorquist on 2012-04-04
I know it's been marked as solved, but just thought I'd shed more light on this - yes, it's working out of the box, at least from my experience on 11.10 64-bit as of at least April 2012. So for anyone reading this who's having problems with it, before you start ripping apart your computer and scouring the internet trying to find the drivers, a clean install of 11.10 should yield you plug-and-play. I know because I just tried it on three separate machines.

---

### Post by Ashade on 2012-12-15
> **knorquist said:**
> I know it's been marked as solved, but just thought I'd shed more light on this - yes, it's working out of the box, at least from my experience on 11.10 64-bit as of at least April 2012. So for anyone reading this who's having problems with it, before you start ripping apart your computer and scouring the internet trying to find the drivers, a clean install of 11.10 should yield you plug-and-play. I know because I just tried it on three separate machines.

Not working for me out of the box on Lenovo Yoga with 12.10. Wierd thought... I think I am going to try with ndiskwrapper and the drivers for windows... If any one have an idea it will be very welcome.

---

