---
title: "Injection problem because of driver"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by best4u on 2013-03-09
Recently i bought a Realtek USB wireless card with RTL8187L chipset. Backtrack 5 R3 kde installed and 3.2.6 is kernel version.

I tried to use injection with this card it's work but after 15 second will stop and disconnect. I ask seller to know about this matter, he said should be install exactly RTL8187L driver (not rtl8187 & etc...)
Found a driver in [Realtek website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") and try to install it :
```
apt-get install build-essential linux-headers-`uname -r`
cd Downloads/rtl8187L_linux_1041.0209.2012
make
make install
```
But error showing:
```
root@bt:~# apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 cryptsetup
  libecryptfs0 reiserfsprogs rdate bogl-bterm ecryptfs-utils libdebconfclient0
  dmraid
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.2.6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,352kB of archives.
After this operation, 56.9MB of additional disk space will be used.
Get:1 http://32.repository.backtrack-linux.org/ revolution/testing linux-headers-3.2.6 3.2.6-10.00.Custom [7,352kB]
Fetched 7,352kB in 1min 15s (97.4kB/s)                                         
Selecting previously deselected package linux-headers-3.2.6.
(Reading database ... 259600 files and directories currently installed.)
Unpacking linux-headers-3.2.6 (from .../linux-headers-3.2.6_3.2.6-10.00.Custom_i386.deb) ...
Setting up linux-headers-3.2.6 (3.2.6-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
```
```
root@bt:~/rtl8187L_linux_1041.0209.2012# make
make[1]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_93cx6.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225z2.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_led.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_pm.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_dm.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.mod.o
  LD [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.ko
make[1]: Leaving directory `/usr/src/linux-source-3.2.6'
```
```
root@bt:~/rtl8187L_linux_1041.0209.2012# make install
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
cp: cannot create regular file `/etc/acpi/events/': No such file or directory
make: *** [install] Error 1
```
In windows 7 no problem but Backtrack automatically load rtl8187 not RTL8187L.
```
root@bt:~# airmon-ng

Interface  Chipset  Driver

wlan1  Broadcom  b43 - [phy1]
wlan0  Realtek RTL8187L  rtl8187 - [phy0]
```
Should be install exactly RTL8187L
Any help, appreciated

---

### Post by haqking on 2013-03-09
> **best4u said:**
> Recently i bought a Realtek USB wireless card with RTL8187L chipset. Backtrack 5 R3 kde installed and 3.2.6 is kernel version.

I tried to use injection with this card it's work but after 15 second will stop and disconnect. I ask seller to know about this matter, he said should be install exactly RTL8187L driver (not rtl8187 & etc...)
Found a driver in [Realtek website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") and try to install it :
```
apt-get install build-essential linux-headers-`uname -r`
cd Downloads/rtl8187L_linux_1041.0209.2012
make
make install
```
But error showing:
```
root@bt:~# apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 cryptsetup
  libecryptfs0 reiserfsprogs rdate bogl-bterm ecryptfs-utils libdebconfclient0
  dmraid
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.2.6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,352kB of archives.
After this operation, 56.9MB of additional disk space will be used.
Get:1 http://32.repository.backtrack-linux.org/ revolution/testing linux-headers-3.2.6 3.2.6-10.00.Custom [7,352kB]
Fetched 7,352kB in 1min 15s (97.4kB/s)                                         
Selecting previously deselected package linux-headers-3.2.6.
(Reading database ... 259600 files and directories currently installed.)
Unpacking linux-headers-3.2.6 (from .../linux-headers-3.2.6_3.2.6-10.00.Custom_i386.deb) ...
Setting up linux-headers-3.2.6 (3.2.6-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
```
```
root@bt:~/rtl8187L_linux_1041.0209.2012# make
make[1]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_93cx6.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225z2.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_led.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_pm.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_dm.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.mod.o
  LD [M]  /root/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.ko
make[1]: Leaving directory `/usr/src/linux-source-3.2.6'
```
```
root@bt:~/rtl8187L_linux_1041.0209.2012# make install
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
cp: cannot create regular file `/etc/acpi/events/': No such file or directory
make: *** [install] Error 1
```
In windows 7 no problem but Backtrack automatically load rtl8187 not RTL8187L.
```
root@bt:~# airmon-ng

Interface  Chipset  Driver

wlan1  Broadcom  b43 - [phy1]
wlan0  Realtek RTL8187L  rtl8187 - [phy0]
```
Should be install exactly RTL8187L
Any help, appreciated

Use BT or Aircrack forums, injection and associated tools are not supported here.

Peace

---

### Post by oldos2er on 2013-03-09
Backtrack forums are [here]("http://www.backtrack-linux.org/forums/forum.php").

Closed.

---

### Post by Old_Grey_Wolf on 2013-03-09
backtrack site [http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

Thread closed. Not supported here.

---

