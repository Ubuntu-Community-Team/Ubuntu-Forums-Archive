---
title: "trouble setting up wireless connection (kubuntu 12.04)"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by hugocoolens on 2013-07-10
I'd like to configure my linuc(es) such that when I have a utp-cable  plugged in, the wired connection is used and when the utp-wire is  removed the wireless connection is used. 
I followed the instructions on this page: 
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration) 

My interfaces-file contains the following lines: 

auto lo 
iface lo inet loopback 
auto eth0 
iface eth0 inet static 
        address 192.168.1.14 
        netmask 255.255.255.0 
        gateway 192.168.1.1 
auto wlan0 
iface wlan0 inet dhcp 
        wireless-essid bbox2malec 
        pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf 
        post-down killall -q wpa_supplicant 


To test my configuration I entered the following command: 
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -d 

As you can see some error messages here below show it does not work: 

Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A' 
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf' 
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' 
ctrl_interface='/var/run/wpa_supplicant' 
ctrl_interface_group='root' 
Priority group 0 
   id=0 ssid='bbox2malec' 
WEXT: cfg80211-based driver detected 
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf 
  capabilities: key_mgmt 0xf enc 0xf flags 0x0 
netlink: Operstate: linkmode=1, operstate=5 
Own MAC address: 54:e6:fc:db:6a:6c 
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0 
ioctl[SIOCSIWENCODEEXT]: Invalid argument 
Driver did not support SIOCSIWENCODEEXT 
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0 
ioctl[SIOCSIWENCODEEXT]: Invalid argument 
Driver did not support SIOCSIWENCODEEXT 

Can someone here tell me how to solve this? 

thanks in advance 
hugo

---

