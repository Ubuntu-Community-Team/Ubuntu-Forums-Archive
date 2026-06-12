---
title: "rtl8723ae and ubuntu 13.04"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by tsviatko on 2013-07-08
I have a Toshiba Sattelite with this wlan chipset. It used to work on Ubuntu 12.04 with the custom driver mentioned in a topic here. 

Then I upgraded to 13.04 where supposedly the kernel supports this chip out of the box. I can see an rtl8723ae module loaded. Also, the wlan0 interface is there. I cannot see any wireless networks though nor can I connect to any. Here's the wireless_script ([http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)) output.



*************** info trace ***************


***** uname -a *****


Linux SATELLITE 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
	Kernel driver in use: rtl8723ae
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fb37]
	Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0930:021d Toshiba Corp. 


***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.138
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     No scan results




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** dmesg *****


[   12.985074] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   13.209254] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.209451] rtlwifi: wireless switch is on
[   15.970381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.970643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1207.399214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************

---

### Post by rogervn on 2013-10-03
I'm also having a lot of problems with this adapter. The official drivers seem to be very primitive and the kernel drivers based on the official ones.

Right now I'm having a lot of trouble to connect to my router from my bedroom, the signal and the packet drops are very unstable while the Windows drivers keep it just fine in the same bedroom.

The most recent drivers (downloaded from realtek when looking dor rtl8188ce) seem to work better, but are still not that good. I would like to know if any progress is made in these drivers, because I'm almost opting to change my wifi model due to the lack of support.

---

