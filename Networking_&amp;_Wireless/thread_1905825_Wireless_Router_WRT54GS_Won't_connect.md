---
title: "Wireless Router WRT54GS Won't connect"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by stephanmir on 2012-01-07
**[COLOR=black]Hello,[/COLOR]**
 
**[COLOR=black]I am having WRT54GS - Router issues. I have multiple devices already connected to this router:[/COLOR]**
 
**Windows 7 PC**
**Windows 7 Laptop**
**2 IPhones**
**Ipad 2**
**Playstation 3**
 
**However, I am having issues connecting the ubuntu 11.10 to the router. Everything seems to be running normal on Ubuntu. I am able to detect the SSID and it asks for the password when connecting. I put in the password correctly and then press continue. It states that it is configuring to obtain an IP from the DHCP, however, after a long pause it does not connect and disconnects. **
 
**Originally I had my router set to filter MAC addresses and had all my MAC addresses detected and okay, including Ubuntu. But now it was giving me issues when I reinstalled to 11.10. I changed the router setting from filter to WEP key and set that up correctly. I am able to connect with my other devices properly, but not with Ubuntu.**
 
**Any assistance would be greatly appreciated.**
 
**Stephan**

---

### Post by stephanmir on 2012-01-07
**cat /etc/lsb-release;uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Stephan-Desktop 3.0.0-14-generic #23-Ubuntu SMP
 
**lspci -nnk | grep -iA2 net**
Network controller 0280: Atheros Communications
Subsystem: D-Link system inc DWA-552 802.11n Xtreme N Desktop Adapter 
Kernel driver in use: ath9k
Ethernet Controller 0200: Intel corp 82573L Gigabit Ethernet Controller
Subsystem ASUSTek Computer
Kernel driver in use: e1000e
 
**iwconfig**
wlan0  IEEE 802.11bgn  ESSID:off/any
mode: managed access point: not associated  tx-power-27 dBm
 
**rfkill list all**
1: phy1: Wireless LAN
Soft Blocked: No
Hard Blocked: No
 
**lsmod       **
Module     Used By
ath9k       0
bnep        2
rfcomm     0
bluetooth      10 bnep,rfcomm
binfmt_misc   1
adt7475       0
hwmon_vid       1 adt7475
snd_usb_audio     1
arc4           2
snd_hda_codec_realtek   1 (and more snd omitted)
nouveau    3
ttm       1  nouveau
ppdev   0
drm_kms_helper      1 nouveau
drm     5 nouveau,ttm,drm_kms_helper
mac80211    1 ath9k
parport _pc    1
asus_atk0110   0
ath9k_hw     2 ath9k, ath9k_common
ath   2 ath9k, ath9k_hw
lp   0
e1000e     0

---

### Post by stephanmir on 2012-01-08
bump

---

