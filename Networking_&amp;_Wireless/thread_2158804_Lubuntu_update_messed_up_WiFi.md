---
title: "Lubuntu update messed up WiFi"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by biomecanoid on 2013-06-30
Hi guys,

Yesterday i updated my Lubuntu instalation on my Acer Asprire ONE ZG5 to Version 13.04 hoping it improve my system providing new drivers software etc

**Image:**
[http://t0.gstatic.com/images?q=tbn:ANd9GcRM0K1-XtxGpgDfVQFTxMyO5BOF462y7Nu511PCsNqdwD4IVDvl](http://t0.gstatic.com/images?q=tbn:ANd9GcRM0K1-XtxGpgDfVQFTxMyO5BOF462y7Nu511PCsNqdwD4IVDvl)

**Specs:**
[http://gdgt.com/acer/aspire/one/zg5/specs/](http://gdgt.com/acer/aspire/one/zg5/specs/)

The update installed without a problem and the netbook rebooted fine. The computer works OK if you are a simple user but since i want to use my netbook for wardriving i have installed some tools like the aircrack suite, wash, rever etc and with the update when ever i try to use airodump-ng for example it said fixed channel -1 and the card doesnt change channel. 

**Fixed Channel Error:**
[http://t3.gstatic.com/images?q=tbn:ANd9GcR7ADM3eJSHfKlmPx-14678Up5s12q6bQ2LcEu2Zj5u2rFaeO3DKA](http://t3.gstatic.com/images?q=tbn:ANd9GcR7ADM3eJSHfKlmPx-14678Up5s12q6bQ2LcEu2Zj5u2rFaeO3DKA)

So i am stuck on channel -1 and i cant really used any of my WiFi wardriving tools.

From what i have read online i must install the Compat-Wireless drivers with some relevant patches to fixed the channel error from airodump and also  make reaver usable.

Sadly i was unable to install any Compat drivers cause i get all sorts of errors when trying to make and i have all the compilers. I have 2 WiFi cards the internal on the netbook ath5k and the Geetek Janus II rt2800 usb both are effected by the problem.

**Geetek:**
[https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsAHr2OQAQ_BFnl8RZHe3p4clL2lGZ1zgjpNqBFzj-9bXqfR3h](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsAHr2OQAQ_BFnl8RZHe3p4clL2lGZ1zgjpNqBFzj-9bXqfR3h)

I hope you guys have an idea on how to fix this cause i like using my Lubuntu for wardriving since its a bit more friendly looking than backtrack. For now i have Backtrack on a bootable USB.

Thanks
Chris

---

### Post by biomecanoid on 2013-06-30
Tried to install compat-Wireless on my own

root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2# make
Generating local configuration database from kernel ... done.
/--
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|  make oldconfig
|  make menuconfig
|
| To get defaults for certain drivers:
|  make defconfig-drm
|  make defconfig-iwlwifi
|  make defconfig-media
|  make defconfig-nfc
|  make defconfig-regulator
|  make defconfig-rtlwifi
\--
make[2]: *** [.config] Error 1
make[1]: *** [modules] Error 2
make: *** [default] Error 2
root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2#

[HR][/HR] root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2# make oldconfig
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
*
* Restart config...
*
*
* Linux Backports from "Linux" "v3.10-rc1-0-gf722406" (with backports "v3.10-rc1-2-0-gc918a4f")
*
codel (BACKPORT_USERSEL_NET_SCH_CODEL) [N/m] (NEW) 
FQ codel (BACKPORT_USERSEL_NET_SCH_FQ_CODEL) [N/m] (NEW) 
Build all compat code (BACKPORT_USERSEL_BUILD_ALL) [N/y/?] (NEW) 
cfg80211 - wireless configuration API (CFG80211) [N/m/?] (NEW) 
*
* CFG80211 needs to be enabled for MAC80211
*
*
* Bluetooth subsystem support
*
Bluetooth subsystem support (BT) [N/m/?] (NEW) 
*
* Wireless LAN
*
Wireless LAN (WLAN) [Y/n/?] (NEW) 
  *
  * TI Wireless LAN support
  *
  TI Wireless LAN support (WL_TI) [N/y/?] (NEW) 
*
* Ethernet driver support
*
Ethernet driver support (ETHERNET) [Y/n/?] (NEW) 
  Atheros devices (NET_VENDOR_ATHEROS) [Y/n/?] (NEW) 
    Atheros L2 Fast Ethernet support (ATL2) [N/m/?] (NEW) 
    Atheros/Attansic L1 Gigabit Ethernet support (ATL1) [N/m/?] (NEW) 
    Atheros L1E Gigabit Ethernet support (ATL1E) [N/m/?] (NEW) 
    Atheros L1C Gigabit Ethernet support (ATL1C) [N/m/?] (NEW) 
  Broadcom devices (NET_VENDOR_BROADCOM) [Y/n/?] (NEW) 
    Broadcom 440x/47xx ethernet support (B44) [N/m/?] (NEW) 
*
* USB Network Adapters
*
Multi-purpose USB Networking Framework (USB_USBNET) [N/m/?] (NEW) 
*
* Sonics Silicon Backplane
*
Sonics Silicon Backplane support (SSB) [N/m/?] (NEW) 
*
* Broadcom specific AMBA
*
BCMA support (BCMA) [N/m/?] (NEW) 
*
* Direct Rendering Manager (XFree86 4.1.0 and higher DRI support)
*
Direct Rendering Manager (XFree86 4.1.0 and higher DRI support) (DRM) [N/m/?] (NEW) 
*
* NFC subsystem support
*
NFC subsystem support (NFC) [N/m/?] (NEW) 
*
* Voltage and Current Regulator Support
*
Voltage and Current Regulator Support (REGULATOR) [N/y/?] (NEW) 
*
* Multimedia support
*
Multimedia support (MEDIA_SUPPORT) [N/m/?] (NEW) 
*
* X86 Platform Specific Device Drivers
*
X86 Platform Specific Device Drivers (X86_PLATFORM_DEVICES) [Y/n/?] (NEW) 
  Intel Intelligent Power Sharing (INTEL_IPS) [N/m/?] (NEW) 
#
# configuration written to .config
#
root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2#
[HR][/HR] root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2# make install
make[4]: `conf' is up to date.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/main.o
  CC [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/compat-3.9.o
  CC [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/backport-3.10.o
  CC [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/compat_atomic.o
  LD [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/compat.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC  /home/chris/Downloads/backports-3.10-rc1-2/compat/compat.mod.o
  LD [M]  /home/chris/Downloads/backports-3.10-rc1-2/compat/compat.ko
  INSTALL /home/chris/Downloads/backports-3.10-rc1-2/compat/compat.ko
Can't read private key
  DEPMOD  3.8.0-26-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

root@Tiny:/home/chris/Downloads/backports-3.10-rc1-2#
[HR][/HR] Rebooted and the problem is still there

---

### Post by wildmanne39 on 2013-06-30
Hi, aircrack is not supported on the forum your best option is backtrack forum or I believe aircrack has its own forum now.
Thanks

---

