---
title: "Ubuntu 13.04 crashes Netgear WPN824 router"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by duncanka2 on 2013-05-20
I have had a problem with all versions of Ubuntu for the past 2 years: whenever I attempt to connect to my home wireless network from my laptop, the router crashes, disconnecting all devices. The router is a Netgear WPN824 (RangeMax), and the laptop is a Lenovo T420 with a RealTek RTL8188CE wireless card, currently running a fully up-to-date installation of Ubuntu 13.04. It used to be that an attempt to connect would require rebooting the router before any devices could reconnect to the network; recently (perhaps after updating to 13.04), the router comes back to life a minute or two after I turn off the laptop's wireless card. The laptop can connect just fine to the same network with the same password when booted into Windows, with no adverse effects on other devices.

I have tried downloading, compiling, and installing the latest RealTek drivers from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true), but it made no difference. (In case this may help any netizens trying the same, I had to add the following to pci.h to get the drivers to compile:
#ifdef CONFIG_HOTPLUG
#  define __devinit
#  define __devinitdata
#else
#  define __devinit __init
#  define __devinitdata __initdata
#endif
)

I've searched and found a couple of threads on similar-sounding issues, but none that was quite the same had any replies. Does anyone know what the solution might be?

Output from **lspci |  grep 802.11b**:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

Output from **iwconfig**:
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

Output from **modinfo rtl8192ce**:
filename:       /lib/modules/3.8.0-22-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8371CA3A9E899B11125FFDE
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.8.0-22-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

---

### Post by sanderj on 2013-05-21
Update the firmware in the Netgear WPN824 (RangeMax) router ...?

---

