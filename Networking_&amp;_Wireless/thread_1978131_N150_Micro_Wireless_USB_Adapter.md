---
title: "N150 Micro Wireless USB Adapter"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by unixlike on 2012-05-11
Hi,
I have Ubuntu 12.04 and this wireless adapter:
N150 Micro Wireless USB Adapter
[http://www.belkin.com/IWCatProductPage.process?Product_Id=543959](http://www.belkin.com/IWCatProductPage.process?Product_Id=543959)

The problem is that I am not be able to connect my desktop to the wireless home network.
Ubuntu ask me network password always and it never connects. (password is correct)

I read that is a compatibility problem.....
Anyone can help me?

Thank you so much.

---

### Post by kc1di on 2012-05-11
> **unixlike said:**
> Hi,
I have Ubuntu 12.04 and this wireless adapter:
N150 Micro Wireless USB Adapter
[http://www.belkin.com/IWCatProductPage.process?Product_Id=543959](http://www.belkin.com/IWCatProductPage.process?Product_Id=543959)

The problem is that I am not be able to connect my desktop to the wireless home network.
Ubuntu ask me network password always and it never connects. (password is correct)

I read that is a compatibility problem.....
Anyone can help me?

Thank you so much.
here is a similar thread and it seems that you may have to blacklist rt2800usb driver. 
and use wep 128bit security.  anyway take a look.

[http://ubuntuforums.org/showthread.php?t=1482382]("http://ubuntuforums.org/showthread.php?t=1482382")

---

### Post by unixlike on 2012-05-11
Hmm,
don't work for me and I have to use wpa2 security.

---

### Post by kurt18947 on 2012-05-11
Hi

My usual source for checking chipset is being reluctant right now.  Could you run the command "lsusb" and copy the output?  I suspect your Belkin uses a RealTek 8188Cus chipset; most adapters using that form factor seem to use the same chipset.  I had the same problem with a Edimax EW-7811UN adapter, it was active but wouldn't connect with  WPA2 encryption.  My solution was to download the driver from Realtek.  The file includes an install script which has been perfect on 3 different machines for me.  Here's a link:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

This is a recent version, I'm using a prior.  If this doesn't work I can upload the version I'm using.  

[CENTER][COLOR=Blue]Disregard this part if you're familiar with installing from the command line[/COLOR]
[/CENTER]

This has to be done from an account with sudo privileges.  To install RealTek's driver, download it, unpack it in a location you can find again.  I installed it on my desktop.  Now open a terminal, type "cd Desktop", "dir" should show the newly created folder. cd to that folder and type "dir" again.  One of the entries should be  "install.sh".  Type "sudo bash install" press enter.  It'll run a number of lines then offer a choice of 2 items.  Select 1 and watch the lines of text scroll by.  You should get a 'success' message and a flashing light.

You may or may not have to blacklist the default driver.  I did have to blacklist in 11.10, didn't have to blacklist in 12.04 so YMMV I guess.  I hope this makes sense.

---

### Post by unixlike on 2012-05-11
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external 
gfx0 port A)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI 
express gpp port E)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI 
express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA 
Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE 
Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 
40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host 
controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI 
bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB 
EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport 
Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous 
Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit 
Ethernet controller (rev 06)
02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI 
Controller (rev c0)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
05:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GTS 450] (rev a1)
05:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
michele@HomeDesktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[COLOR="Red"]Bus 001 Device 003: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless 
Adapter v1000 [Realtek RTL8188CE-VAU][/COLOR]
Bus 005 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 002: ID 046d:08f6 Logitech, Inc. QuickCam Messenger Plus
```

Suggestions?
Thanks.

---

### Post by unixlike on 2012-05-11
I have installed what you say...
At the end of installation I have this message:
Note I have tried with option 1 and 2.
```
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic' 
################################################## 
Compile make driver ok!! 
################################################## 
Authentication requested [root] for remove driver: 
ERROR: Module 8192cu does not exist in /proc/modules 
Authentication requested [root] for insert driver: 
insmod: error inserting '8192cu.ko': -1 Device or resource busy 
Authentication requested [root] for install driver: 
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/ 
/sbin/depmod -a 3.2.0-23-generic 
################################################## 
The Setup Script is completed ! 
################################################## 
```
is correct?

Now lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless 
Adapter v1000 [Realtek RTL8188CE-VAU]
Bus 003 Device 003: ID 0951:1643 Kingston Technology DataTraveler G3 4GB
Bus 005 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 002: ID 046d:08f6 Logitech, Inc. QuickCam Messenger Plus
```

Results: don't work again.

---

### Post by kurt18947 on 2012-05-11
I think your procedure was correct but the driver I linked to was for the RTL8188Cus.  You have the RealTek RTL8188CE-VAU which I've never heard of.  When I put your model # into the deviwiki web site it returned RTL8188Cus.  You may have a new version #.  RealTek does have a driver for that chipset:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

It seems like it would be a good idea to remove the driver you installed first before installing the RTL8188CE-VAU driver.  Not being anything resembling a guru, I'm not sure how to remove the incorrect driver though I'm sure some searching would produce an answer.  Probably something like sudo apt-get purge (driver name) or sudo apt-get remove (driver name) but I'm not sure.  I'm assuming the install procedure would be the same as the driver you installed.

---

### Post by MrSchroeder13 on 2012-06-20
> **kurt18947 said:**
> I think your procedure was correct but the driver I linked to was for the RTL8188Cus.  You have the RealTek RTL8188CE-VAU which I've never heard of.  When I put your model # into the deviwiki web site it returned RTL8188Cus.  You may have a new version #.  RealTek does have a driver for that chipset:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

It seems like it would be a good idea to remove the driver you installed first before installing the RTL8188CE-VAU driver.  Not being anything resembling a guru, I'm not sure how to remove the incorrect driver though I'm sure some searching would produce an answer.  Probably something like sudo apt-get purge (driver name) or sudo apt-get remove (driver name) but I'm not sure.  I'm assuming the install procedure would be the same as the driver you installed.

I attempted the CE-VAU install for this device - appears to fail.  

```
schroeder@schroeder-u:~/Desktop$ cd Driver
bash: cd: Driver: No such file or directory
schroeder@schroeder-u:~/Desktop$ dir
driver
schroeder@schroeder-u:~/Desktop$ cd driver
schroeder@schroeder-u:~/Desktop/driver$ dir
android_reference_codes      hardware\ wps\ pbc  wireless_tools
android_reference_codes_ICS  install.sh		 wpa_supplicant
document		     readme.txt
driver			     ReleaseNotes.pdf
schroeder@schroeder-u:~/Desktop/driver$ sudo bash install.sh
[sudo] password for schroeder: 
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
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-25-generic/build M=/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  CC [M]  /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0,
                 from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type
In file included from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0,
                 from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type
make[2]: *** [/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/schroeder/Desktop/driver/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
schroeder@schroeder-u:~/Desktop/driver$ 

```

I think the simple fact of the matter is this damn N150 Micro Wireless adapter **only** works in WEP64 or open modes, which is strange because the box itself shows "WPA/WPA2" as well as 64/128 WEP.

---

### Post by MrSchroeder13 on 2012-06-20
Update:

- I've tried both options 1|2 while running the install.sh
- I've tried running the install manually, following the instructions including with the tar ball
- Meanwhile I have an old netgear 3" wifi adapter that is establishing a network correctly with no need for any drivers/updates - straight plug and play
- I'm super frustrated with this

More update:
It seems there is yet another updated driver [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE-VAU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE-VAU) specific to this device and I will attempt it again

Reupdate:
Grrr.  The above linked DL is exactly the same as the other ones, the Realtek site shows it's updated 5/7/2012 but in fact is the same version from 4/4/2012 as the others - meaning it is NOT for the 8188CE-VAU, but for the 8192C|D versions only.

---

### Post by MrSchroeder13 on 2012-06-20
Solved

The chipset for 8188CE that Realtek recommends *does not* work.

[http://ubuntuforums.org/showthread.php?p=12042944#post12042944](http://ubuntuforums.org/showthread.php?p=12042944#post12042944) 

Refer to that post, follow the link to a driver that does work.

Along with the steps followed, I covered my bases by following up with command $ make install

No need to blacklist original 8192ce driver as I mention in that thread.

---

