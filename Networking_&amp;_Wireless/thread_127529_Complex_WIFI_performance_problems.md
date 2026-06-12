---
title: "Complex WIFI performance problems"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by mcframe on 2006-02-09
Hi, I'm using a HP notebook with built in ipw2100 under Kubuntu 10.5 Breezy with WPA encryption. (ipw2100 v1.1.2, wpa_supplicant v0.4.5) 

At home I have a D-Link 714P+ (IEEE 802.11b) accesspoint with which my wireless network configuration works flawlessly. 

In the office I have two WIFI access points (same ESSID and WPA-PSK) and with both certain connection problems appear: 
A Netgear WPN824 (Mimo, 802.11b&g, rangemax) to which connection works but the KDE signal quality indicator shows heavy fluctuations and 3 to 5 times an hour the connections drops completely and stays dead for some minutes. The second office router is a Dlink D-624 (802.11b&g) to which connections appaer with a constant signal quality, but a very strange bandwidth perfomance. Every transmission starts with acceptatble bandwidth (300k/s), but bandwidth declines rapidly until it reaches 50 Bit/s or lower, ending up that every transmission takes endlessly to complete. Additionally both office routers frequently lead to the following messages in /var/log/debug: ```
Feb 8 11:16:42 localhost kernel: [4302904.194000] TKIP: replay detected: STA=00:14:6c:24:b5:c0 previous TSC 000000000000 received TSC 000000000000 
``` but I dont know if this is related to the problems mentioned above. 
Although both office routers are b&g compliant could there be a minor incompatibility with the ipw2100? What could be a strategy to find out the real source of the problems? (e.g. if notebook or router configuration) (I should add that several other ipw2200 notebooks under windows do not have any connection probs.) THX in advance mcframe

---

