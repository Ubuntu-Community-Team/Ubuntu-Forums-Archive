---
title: "Problems with AR5008E-3NX"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Filipe C on 2009-04-24
[SIZE="4"]Hello, i have a problem with this wireless card,
Before i installed ubuntu jaunty i have run livecd and the wireless worked great!!
And then i installed ubuntu jaunty and the wireless didn't worked again :(
Before this i used opensuse 11.1 and the wireless worked fine but i prefer ubuntu so i tried but... no wireless....

My laptop is a PackardBell[/SIZE]
[SIZE="4"]

Here is the wireless card that i use:[/SIZE]
[HTML]http://www.atheros.com/pt/bulletins/AR5008E-3NXBulletin.pdf[/HTML]


```
lipec@bell-laptop:~$ uname -a
Linux bell-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

```
lipec@bell-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
[COLOR="Red"]_03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)_[/COLOR]
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

```
lipec@bell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```

```
lipec@bell-laptop:~$ dmesg | grep Atheros 
[   13.095631] phy0: Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81: mem=0xf83c0000, irq=17

```

```
lipec@bell-laptop:~$ dmesg | grep ath
[    2.308467] device-mapper: multipath: version 1.0.5 loaded
[    2.308474] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.487919] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.512717] ath9k 0000:03:00.0: setting latency timer to 64
[   12.650598] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.095476] Registered led device: ath9k-phy0::radio
[   13.095525] Registered led device: ath9k-phy0::assoc
[   13.095574] Registered led device: ath9k-phy0::tx
[   13.095622] Registered led device: ath9k-phy0::rx

```

[SIZE="3"]I'm new user on ubuntu and it appears that it's everything ok but the wireless dosen't work....

In opensuse 11.1 i didn't have to do nothing just installed the the wireless worked just fine.

In livecd of ubuntu jaunty the same thing the wireless worked just fine, but when i installed a fresh copy of jaunty the wireless didn't worked.

Can anyone help me please!!!!!!!!

Thanks...[/SIZE]

---

### Post by Filipe C on 2009-04-27
[SIZE="3"][SIZE="4"][COLOR="Black"]


I see a diference on one comand that i make:

ubuntu@ubuntu:/etc$ dmesg | grep ath
[    2.340448] device-mapper: multipath: version 1.0.5 loaded
[    2.340451] device-mapper: multipath round-robin: version 1.0.0 loaded
[   71.309816] ath9k: 0.1
[   71.309888] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   71.309909] ath9k 0000:03:00.0: setting latency timer to 64
[   71.448723] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   71.721668] Registered led device: ath9k-phy0:radio
[   71.721718] Registered led device: ath9k-phy0:assoc
[   71.721770] Registered led device: ath9k-phy0:tx
[   71.721818] Registered led device: ath9k-phy0:rx

This line appears on livecd but on the sistem installed does not appears 
[   71.309816] ath9k: 0.1
Is there any diference???[/COLOR][/SIZE][/SIZE]

---

### Post by Filipe C on 2009-04-29
Once more...
Does anyone can help me on this?
It´s the only problem that i have with ubuntu jaunty....

Thanks...

---

### Post by t0mppa on 2009-04-29
Looks like the LiveCD is wise enough to try using ath9k (Atheros driver with 802.11N support), while ath5k (main driver for all the other cards) is installed by default on Jaunty.

[See here]("http://wireless.kernel.org/en/users/Drivers/ath9k") about installing ath9k. If you run into some trouble, feel free to post back and me or someone else will help you through the install steps.

---

### Post by Filipe C on 2009-04-29
> **t0mppa said:**
> Looks like the LiveCD is wise enough to try using ath9k (Atheros driver with 802.11N support), while ath5k (main driver for all the other cards) is installed by default on Jaunty.

[See here]("http://wireless.kernel.org/en/users/Drivers/ath9k") about installing ath9k. If you run into some trouble, feel free to post back and me or someone else will help you through the install steps.


Thanks for the help that you are given to me
Really Thanks!!!!     :P

I have see the link that you have posted, but i'm a newbie on ubuntu  and the problem is that i don't now how to make the things that they have there....

[SIZE="3"][COLOR="DarkRed"][B]Sorry about my ignorance but


[/B][/COLOR][/SIZE]Where do i go to make or how do i do this:

```
 
Enabling ath9k

To enable ath9k, you must first enable mac80211:

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)
```


```

You can then enable ath9k in the kernel configuration under


Device Drivers  --->
  [*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 802.11n wireless cards support
```




Another thing i have see on the net one comand:
modeprobe and i tried this:


lipec@bell-laptop:~$ sudo modprobe ath*
[sudo] password for lipec: 
FATAL: Module ath* not found.
For me i understand that i don't have the module working....


Sorry but like i sayd before i'm a newbie on this........
Can you explain to me???

---

### Post by t0mppa on 2009-04-29
Modprobing is just turning the drivers functional after you've installed them. It won't help you before though, since it can't probe something that doesn't exist.

Ok. Step-by-step: download [this]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2"), then open up a terminal and go to the directory where you downloaded it into. Then enter these commands: ```
tar xvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2009-04-29/
make
sudo make install
sudo make unload
sudo make load
sudo modprobe ath9k
``` And then it should be working, if you didn't run into any errors during the compiling.

Oh and you'll have to have build-essential package installed to be able to do this, but you can install that through System / Administration / Synaptic Packet Manager. Just write build-essential to the Quick Search field, then click on the box before the package name and pick "Mark for installation" then click Apply.

---

### Post by Filipe C on 2009-04-29
> **t0mppa said:**
> Modprobing is just turning the drivers functional after you've installed them. It won't help you before though, since it can't probe something that doesn't exist.

Ok. Step-by-step: download [this]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2"), then open up a terminal and go to the directory where you downloaded it into. Then enter these commands: ```
tar xvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2009-04-29/
make
sudo make install
sudo make unload
sudo make load
sudo modprobe ath9k
``` And then it should be working, if you didn't run into any errors during the compiling.

Oh and you'll have to have build-essential package installed to be able to do this, but you can install that through System / Administration / Synaptic Packet Manager. Just write build-essential to the Quick Search field, then click on the box before the package name and pick "Mark for installation" then click Apply.






I made everething like you have told me to do i have done the comand: 
make and gives ok 

then i make:

[PHP]lipec@bell-laptop:~/Programas-Ubuntu/compat-wireless-2009-04-29$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
updates/lib80211.ko
updates/adm8211.ko
updates/at76c50x-usb.ko
updates/ath5k.ko
updates/ath9k.ko
updates/b43.ko
updates/b43legacy.ko
updates/b44.ko
updates/cdc_ether.ko
updates/eeprom_93cx6.ko
updates/ipw2100.ko
updates/ipw2200.ko
updates/iwl3945.ko
updates/iwlagn.ko
updates/iwlcore.ko
updates/lib80211_crypt_ccmp.ko
updates/lib80211_crypt_tkip.ko
updates/lib80211_crypt_wep.ko
updates/libertas.ko
updates/libertas_cs.ko
updates/libertas_sdio.ko
updates/libertas_tf.ko
updates/libertas_tf_usb.ko
updates/libipw.ko
updates/mac80211_hwsim.ko
updates/mwl8k.ko
updates/p54common.ko
updates/p54pci.ko
updates/p54usb.ko
updates/rndis_host.ko
updates/rndis_wlan.ko
updates/rt2400pci.ko
updates/rt2500pci.ko
updates/rt2500usb.ko
updates/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/rt61pci.ko
updates/rt73usb.ko
updates/rtl8180.ko
updates/rtl8187.ko
updates/ssb.ko
updates/usb8xxx.ko
updates/usbnet.ko
updates/zd1211rw.ko

make -C /lib/modules/2.6.28-11-generic/build M=/home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/b44.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/usb/cdc_ether.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/usb/rndis_host.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/usb/usbnet.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/adm8211.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ath/ath.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/b43/b43.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/mwl8k.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/drivers/ssb/ssb.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/mac80211/mac80211.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/wireless/cfg80211.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/wireless/lib80211.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/lipec/Programas-Ubuntu/compat-wireless-2009-04-29/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.28-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
volatile/ath_pci.ko

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/lib80211.ko
updates/adm8211.ko
updates/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath5k/ath5k.ko
updates/ath9k.ko
updates/b43.ko
updates/drivers/net/wireless/b43legacy/b43legacy.ko
updates/b44.ko
updates/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/ipw2100.ko
updates/ipw2200.ko
updates/iwl3945.ko
updates/iwlagn.ko
updates/iwlcore.ko
updates/lib80211_crypt_ccmp.ko
updates/lib80211_crypt_tkip.ko
updates/lib80211_crypt_wep.ko
updates/drivers/net/wireless/libertas/libertas.ko
updates/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/libipw.ko
updates/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/p54pci.ko
updates/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

lipec@bell-laptop:~/Programas-Ubuntu/compat-wireless-2009-04-29$ sudo make unload
MadWifi driver is loaded, going to try to unload it...
Unloading "ath_pci"
Unloading "wlan"
Unloading "ath_hal"
Unloading ath9k...
Unloading ath5k...
[/PHP]

but there appears errors:

[PHP]lipec@bell-laptop:~/Programas-Ubuntu/compat-wireless-2009-04-29$ sudo make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
FATAL: Error inserting libertas_cs (/lib/modules/2.6.28-11-generic/updates/libertas_cs.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading usb8xxx...
FATAL: Error inserting usb8xxx (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/libertas/usb8xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-11-generic/updates/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-11-generic/updates/p54usb.ko): Invalid module format
Loading adm8211...
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting adm8211 (/lib/modules/2.6.28-11-generic/updates/adm8211.ko): Invalid module format
Loading zd1211rw...
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting zd1211rw (/lib/modules/2.6.28-11-generic/updates/zd1211rw.ko): Invalid module format
Loading rtl8180...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-11-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-11-generic/updates/rtl8187.ko): Invalid module format
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-11-generic/updates/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-11-generic/updates/p54usb.ko): Invalid module format
Loading iwl3945...
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-11-generic/updates/iwlcore.ko): Invalid module format
FATAL: Error inserting iwl3945 (/lib/modules/2.6.28-11-generic/updates/iwl3945.ko): Invalid module format
Loading iwlagn...
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-11-generic/updates/iwlcore.ko): Invalid module format
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-11-generic/updates/iwlagn.ko): Invalid module format
Loading ath...
FATAL: Error inserting ath (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
Loading ar9170usb...
FATAL: Module ar9170usb not found.
Loading rtl8180...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-11-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-11-generic/updates/rtl8187.ko): Invalid module format
Loading rt2400pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-11-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2400pci (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Invalid module format
Loading rt2500pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-11-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2500pci (/lib/modules/2.6.28-11-generic/updates/rt2500pci.ko): Invalid module format
Loading rt61pci...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-11-generic/updates/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-11-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt61pci (/lib/modules/2.6.28-11-generic/updates/rt61pci.ko): Invalid module format
Loading rt2500usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-11-generic/updates/rt2x00usb.ko): Invalid module format
FATAL: Error inserting rt2500usb (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Invalid module format
Loading rt73usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-11-generic/updates/rt2x00usb.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-11-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt73usb (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Invalid module format
Loading rndis_wlan...
FATAL: Error inserting rndis_wlan (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rndis_wlan.ko): Invalid module format
Loading at76_usb...
Loading mwl8k...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting mwl8k (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/mwl8k.ko): Invalid module format
Loading mac80211_hwsim...
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting mac80211_hwsim (/lib/modules/2.6.28-11-generic/updates/mac80211_hwsim.ko): Invalid module format
Loading at76c50x_usb...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting at76c50x_usb (/lib/modules/2.6.28-11-generic/updates/at76c50x-usb.ko): Invalid module format
Module ath_pci not detected -- this is fine
WARNING: Error inserting ath (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ath5k (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko): Invalid module format
ath5k loaded successfully
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/updates/ath9k.ko): Invalid module format
ath9k loaded successfully
Module bcm43xx not detected -- this is fine
Disabling wl ...	[OK]	Module disabled:
volatile/wl.ko
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-11-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-11-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-11-generic/updates/b43.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.28-11-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-11-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-11-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43legacy (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Invalid module format
b43 loaded successfully
b43legacy loaded successfully
lipec@bell-laptop:~/Programas-Ubuntu/compat-wireless-2009-04-29$ sudo modprobe ath9k
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/updates/ath9k.ko): Invalid module format
[/PHP]

---

### Post by t0mppa on 2009-04-29
Mm.. Sorry, the unload was in a wrong place, but it least the kernel should now be clean of ath_pci, ath_hal and ath5k. Run the install command again and that should be it (although naturally you need the modprobe that you didn't run yet). Read the documentation again and the load command is only for loading specific modules.

---

### Post by Filipe C on 2009-04-29
Sorry but with compat-wireless nothing....
I had to uninstall compat-wireless because even the wlan0 had disappeared.
When i maked:
lipec@bell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

After i installed compat-wireless shows only this thats why i had to uninstall....

---

### Post by t0mppa on 2009-04-29
Mmm.. On their site, that's the package they recommended for installing ath9k, does include a bunch of other stuff too though. Strange that it doesn't work now and that it did work on the LiveCD.

Well, if that doesn't work, then I'm out of ideas on how to get all the performance out of that chip. Could try the original MadWifi or NDISwrapper to get at least 802.11a, b & g working, but I'm not sure if those will support the 802.11n standard.

---

### Post by Filipe C on 2009-04-29
> **t0mppa said:**
> Mmm.. On their site, that's the package they recommended for installing ath9k, does include a bunch of other stuff too though. Strange that it doesn't work now and that it did work on the LiveCD.

Well, if that doesn't work, then I'm out of ideas on how to get all the performance out of that chip. Could try the original MadWifi or NDISwrapper to get at least 802.11a, b & g working, but I'm not sure if those will support the 802.11n standard.

I appreceate the help that you give me really
Thanks for the help
:)

---

### Post by t0mppa on 2009-04-30
[Here's]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008") a tutorial for installing the original MadWifi driver that I found people had reported to work with their AR5008.

---

### Post by Filipe C on 2009-04-30
> **t0mppa said:**
> [Here's]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008") a tutorial for installing the original MadWifi driver that I found people had reported to work with their AR5008.


Thanks for your help i really appreceate your help the wireles now shows!!!!
:P:P

Now when i make:

lipec@bell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:22:2D:03:71:32
                    ESSID:"Filipe Costa"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-45 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:ath_ie=dd0900037f01010008ff7f

Now appears the my wireless!!!!!!!!

[SIZE="4"][COLOR="Black"]**Thanks t0mppa thanks for your help **[/COLOR][/SIZE]

---

### Post by t0mppa on 2009-04-30
Glad to see it worked. However as you can see the bit rates stop at 54 Mb/s, so you only have a/b/g access with this one. Getting the ath9k to work would've enabled n as well and that'd mean up to 300Mb/s speeds with a router that supports them. But if that doesn't bother you, then I guess it's case closed.

---

