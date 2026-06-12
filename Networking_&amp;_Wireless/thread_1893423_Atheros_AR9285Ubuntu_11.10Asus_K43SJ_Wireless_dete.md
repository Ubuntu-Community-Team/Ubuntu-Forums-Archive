---
title: "Atheros AR9285/Ubuntu 11.10/Asus K43SJ Wireless detected but doesn't connect"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by NickDrapeau on 2011-12-10
Hi,

I am relatively new to Linux, I searched the boards for hours but I haven't been able to find a solution to this problem. Any help would really be appreciated. My Atheros AR9285 wireless card on my new Asus K43S series notebook won't work with Ubuntu 11.10. My computer detects wireless connections and cycles but times out every time without connecting.

Also, when the green wireless light near my trackpad is off my computer detects wireless signals, but when I hit [Fn] F2 to enable wireless, the green light comes on, but then under "Wireless Networks" it says "Device Not Ready". 

Here's some more info about my system that might help :

> >iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
> lspci | grep Network
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Additionally, I checked out this link: [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285) but it only contains the drivers for Ubuntu 10.1. Anyway I don't even know if it's a driver problem or not. Is there any more info you need from me to help me solve this issue? Please help! Thanks. 

-Nick

---

