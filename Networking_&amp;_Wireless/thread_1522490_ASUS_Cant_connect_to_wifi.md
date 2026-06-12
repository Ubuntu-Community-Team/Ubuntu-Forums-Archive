---
title: "ASUS Cant connect to wifi"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by Mavericker on 2010-07-02
Hi i just installed my new laptop Asus and i have strange issues with wifi. I installed driver for 802.11bgn wifi trough ndiswrapper iwconfig returns
[PHP]
wlan0 IEEE 802.11bgn ESSID:none
etc ....
[/PHP]
when i try iwlist scan it returns me names of AP correctly i compared it with my windows laptop , but i cant connect to any network. When i try configure network via knetworkmanager and press button scan the radar doesnt show any vlans , but in terminal wlist does. i dont know so i tried configure it trough[PHP] iwconfig wlan0 essid "myVlan" key s:password mode managed[/PHP]
and [PHP]dhclient wlan0 [/PHP]then [PHP]/etc/networking restart[/PHP] but im not connected and im 100% sure that myVlan and password for WPA is correct. Can someone help me? thanks

---

