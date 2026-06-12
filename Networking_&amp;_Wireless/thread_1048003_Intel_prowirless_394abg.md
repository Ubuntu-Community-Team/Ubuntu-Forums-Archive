---
title: "Intel pro/wirless 394abg"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by uni on 2009-01-23
EDI: Intel pro/wireless 3945abg* sorry for mistake.


Im very new to ubuntu so please bear with me. :)

Ok so i originally got my wireless to work when i was using hardy using this tutorial. [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

Then i installed intrepid ibex and my wireless was still working fine, but i couldnt see a list of any wireless connections around me. So i go messing around trying to fix it when i ended up messing it up more. I followed the tutorial that helped me set it up the first time and it worked. It recognized my wireless as "wlan0" instead of "lo". I dont know if that has anything to do with anything. 

But unfortunatly everytime i restarted my computer it would stop working and i would have to go trough the steps above. 

Im going to post a log of what it tells me in the terminal. 

> justin@justin-laptop:~/compat-wireless-2009-01-05$ make
make -C /lib/modules/2.6.27-11-generic/build M=/home/justin/compat-wireless-2009-01-05 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  Building modules, stage 2.
  MODPOST 43 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
justin@justin-laptop:~/compat-wireless-2009-01-05$ sudo make install

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.27-11-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/adm8211.ko
/lib/modules/2.6.27-11-generic/updates/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/ath9k.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/wireless/at76/at76_usb.ko
/lib/modules/2.6.27-11-generic/updates/b43.ko
/lib/modules/2.6.27-11-generic/updates/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/ssb.ko
/lib/modules/2.6.27-11-generic/updates/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko
/lib/modules/2.6.27-11-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/updates/p54pci.ko
/lib/modules/2.6.27-11-generic/updates/p54usb.ko
/lib/modules/2.6.27-11-generic/updates/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/zd1211rw.ko

make -C /lib/modules/2.6.27-11-generic/build M=/home/justin/compat-wireless-2009-01-05 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  Building modules, stage 2.
  MODPOST 43 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make -C /lib/modules/2.6.27-11-generic/build M=/home/justin/compat-wireless-2009-01-05 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/misc/eeprom_93cx6.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/b44.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/usb/cdc_ether.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/usb/rndis_host.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/usb/usbnet.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/adm8211.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/b43/b43.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/drivers/ssb/ssb.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/mac80211/mac80211.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/wireless/cfg80211.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/wireless/lib80211.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/justin/compat-wireless-2009-01-05/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.27-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

Currently detected wireless subsystem modules:

/lib/modules/2.6.27-11-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/adm8211.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/wireless/at76/at76_usb.ko
/lib/modules/2.6.27-11-generic/updates/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/ath9k.ko
/lib/modules/2.6.27-11-generic/updates/b43.ko
/lib/modules/2.6.27-11-generic/updates/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/ssb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko
/lib/modules/2.6.27-11-generic/updates/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/zd1211rw.ko
justin@justin-laptop:~/compat-wireless-2009-01-05$ sudo make unload
Unloading ieee80211_crypt...
FATAL: Module ieee80211_crypt is in use.
Unloading ieee80211...
Unloading ssb...
Unloading rtl8180...
Unloading rtl8187...
Unloading at76_usb...
Unloading rndis_wlan...
justin@justin-laptop:~/compat-wireless-2009-01-05$ sudo make load
Unloading ieee80211_crypt...
FATAL: Module ieee80211_crypt is in use.
Unloading ieee80211...
Loading ipw2100...
FATAL: Error inserting ipw2100 (/lib/modules/2.6.27-11-generic/updates/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading ipw2200...
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading libertas_cs...
WARNING: Error inserting libertas (/lib/modules/2.6.27-11-generic/updates/libertas.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting libertas_cs (/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading usb8xxx...
WARNING: Error inserting libertas (/lib/modules/2.6.27-11-generic/updates/libertas.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting usb8xxx (/lib/modules/2.6.27-11-generic/updates/usb8xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting p54common (/lib/modules/2.6.27-11-generic/updates/p54common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54pci (/lib/modules/2.6.27-11-generic/updates/p54pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting p54common (/lib/modules/2.6.27-11-generic/updates/p54common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54usb (/lib/modules/2.6.27-11-generic/updates/p54usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading adm8211...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting adm8211 (/lib/modules/2.6.27-11-generic/updates/adm8211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading zd1211rw...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting zd1211rw (/lib/modules/2.6.27-11-generic/updates/zd1211rw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting p54common (/lib/modules/2.6.27-11-generic/updates/p54common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54pci (/lib/modules/2.6.27-11-generic/updates/p54pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting p54common (/lib/modules/2.6.27-11-generic/updates/p54common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54usb (/lib/modules/2.6.27-11-generic/updates/p54usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading iwl3945...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.27-11-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading iwl4965...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.27-11-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.27-11-generic/updates/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2400pci (/lib/modules/2.6.27-11-generic/updates/rt2400pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500pci (/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt61pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt61pci (/lib/modules/2.6.27-11-generic/updates/rt61pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.27-11-generic/updates/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500usb (/lib/modules/2.6.27-11-generic/updates/rt2500usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt73usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.27-11-generic/updates/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt73usb (/lib/modules/2.6.27-11-generic/updates/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath5k (/lib/modules/2.6.27-11-generic/updates/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43 (/lib/modules/2.6.27-11-generic/updates/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43legacy (/lib/modules/2.6.27-11-generic/updates/b43legacy.ko): Unknown symbol in module, or unknown parameter (see dmesg)
b43 loaded successfully
b43legacy loaded successfully



ok now if anyone can tell me what this means and how to fix it i would gladly appreciate it. 

And if its not too much to ask...why couldn't i see available wireless networks in the first place when upgrading to ibex? 

***Ihave followed countless tutorials and i just cant get it to work :( this is my last resort***

---

### Post by uni on 2009-01-23
bump, can someone please help :(

---

### Post by uni on 2009-01-23
thanks for the help guys, really appreciate it.

---

### Post by fendora on 2009-03-25
do u manage to get it work uni?

---

### Post by sefs on 2010-01-25
Was just having this same exact problem.

I found this on google, 

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/294667](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/294667)

and like they say removed my backports modules, and the wireless was back.  Not sure why backports broke it.

This was with RTL8187 chipset though for me.

---

