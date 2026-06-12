---
title: "[SOLVED] Wifi with r780 samsung"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by yeojbf516vtd on 2011-10-03
on a
samsung r780, under kubuntu 10.04 
with rtl8192e as chipset

--------------------
with /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
--------------------
& with no supplicant.conf file        (/etc/wpa_supplicant/wpa_supplicant.conf)
--------------------

so after a long search, very long I must say, I've discovered that the problem came with wicd, uninstall all components of wicd (command line or with synaptic) 
  install networkmanager with the kde or gnome applet 
  
reboot & normally you've got wifi 


thanks for the poster 
[https://wiki.archlinux.org/index.php/Wireless_Setup#rtl8192e](https://wiki.archlinux.org/index.php/Wireless_Setup#rtl8192e)
rtl8192e
The driver is part of the current kernel package. It can be configured using the standard wpa_supplicant and iwconfig tools.

Note: wicd may cause excessive dropped connections with this driver, while NetworkManager appears to work better.
...[https://wiki.archlinux.org/index.php/NetworkManager#Base_install](https://wiki.archlinux.org/index.php/NetworkManager#Base_install)

PS: just for the notice in linux mint, the wifi is ready to use with no modifications

---

### Post by yeojbf516vtd on 2011-10-22
apparently you need to recompile kernel after every kernel update, don't know why 
  in the driver directory type commands :
  sudo su 
  make
  make install
  reboot
  
I use the driver rtl8192e linux 2.6.0015.1013.2010, works fine

---

