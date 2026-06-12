---
title: "LENOVO T400 (with Ubuntu 8.10) wireless doesn't work"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by runningpig001 on 2009-01-28
Hello, I am new at linux. Any help is appreciated!
My OS is Ubuntu 8.10. The GNOME version is 2.24.1. The version of NetworkManager Applet is 0.7.0

1. After running: lspci -nn | grep 'Wireless'
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x  802.11abg Wireless PCI Express Adapter [168c:001a] (rev 01)

2. After running: iwconfig
lo    no wireless extensions
eth0    no wireless extensions
pan0    no wireless extensions

3. After running: lsmod | grep 'wlan'
no responce

4. After running: dmesg | grep 'wlan'
no responce

5. After running: sudo lshw -C network
There are 3 '*-network' in all.
    *-network
          description: Ethernet interface
          product: 82567LM Gigabit Network Connection
          vendor: Intel Corporation
          Physical Id: 19
          bus info: pci@0000:00:19.0
          logical name: eth0
          version: 03
(There are many words left.Is it Ok if I continue with the second one?)
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR242x 802.1abg Wireless PCI Express Adapter
          vendor: Atheros Communications Inc. 
          Physical Id: 0
          bus info: pci@0000:03:00.0
          version: 03
(There are many words left.Is it Ok if I continue with the third one?)
     *-network DISABLED
          description: Ethernet interface
          Physical Id: 2
          logical name: pan0
          serial: ea:9f:bf:22:82:85
and there are some words left too (too tired to type so many words)

6. After running: iwlist scan
lo   Interface doesn't support scanning.

eth0   Interface doesn't support scanning.

pan0   Interface doesn't support scanning.

7. After running: uname -mr
2.6.7-11-generic i686

8. After running: sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...

So, that's my problem. I tried to fix it this afternoon. 
I have read and tried this: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
and also some 'blacklist ath_pci blacklist ath_???' thing, I forgot.

Some suggestions???  Thanks a lot! 
I am really tired of this problem.....

---

### Post by icheyne on 2009-01-29
[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#ThinkPad_11b.2Fg_Wireless_LAN_mini_PCI_Express_Adapter_III_.28Atheros_AR5007EG.2FAR2425_Chipset.29](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#ThinkPad_11b.2Fg_Wireless_LAN_mini_PCI_Express_Adapter_III_.28Atheros_AR5007EG.2FAR2425_Chipset.29)
[http://www.thinkwiki.org/wiki/Intel_WiFi_Link_5100/5300_WLAN_controller](http://www.thinkwiki.org/wiki/Intel_WiFi_Link_5100/5300_WLAN_controller)
[http://www.thinkwiki.org/wiki/Category:T400](http://www.thinkwiki.org/wiki/Category:T400)

---

### Post by runningpig001 on 2009-01-29
> **icheyne said:**
> [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#ThinkPad_11b.2Fg_Wireless_LAN_mini_PCI_Express_Adapter_III_.28Atheros_AR5007EG.2FAR2425_Chipset.29](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#ThinkPad_11b.2Fg_Wireless_LAN_mini_PCI_Express_Adapter_III_.28Atheros_AR5007EG.2FAR2425_Chipset.29)
[http://www.thinkwiki.org/wiki/Intel_WiFi_Link_5100/5300_WLAN_controller](http://www.thinkwiki.org/wiki/Intel_WiFi_Link_5100/5300_WLAN_controller)
[http://www.thinkwiki.org/wiki/Category:T400](http://www.thinkwiki.org/wiki/Category:T400)

Many many thanks, the first website fixed my problem  :p

---

### Post by qwana20 on 2009-02-23
Hi i cant get my wireless to work on a lenovo t400. got it to work yesterday, and it took a dump for some reason today. any assistance is greatly appreciated.
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

access point is not associated.

---

### Post by icheyne on 2009-02-23
All I can do is point you to the original installation instructions - [http://sn.im/t400wifi](http://sn.im/t400wifi)

---

### Post by binbash on 2009-02-23
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

