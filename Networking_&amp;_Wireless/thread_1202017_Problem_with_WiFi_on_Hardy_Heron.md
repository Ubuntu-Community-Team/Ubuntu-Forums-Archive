---
title: "Problem with WiFi on Hardy Heron"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by chodrick on 2009-07-01
I can see all the local networks and I know the settings for my network, however, after making the settings I still cannot connect.  I cannot see my network in 'edit networks' either.  This is my output from dmesg:

charlie@charlie-desktop:~$ dmesg | grep -e ndis -e wlan  
 [   54.383813] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)  
 [   54.711142] ndiswrapper: driver wusb54g (The Cisco-Linksys, LLC.,01/12/2004, 1.0.8.0) loaded  
 [   56.507569] wlan0: ethernet device 00:0f:66:17:75:e5 using NDIS driver: wusb54g, version: 0x10008, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter', 1915:2234.F.conf  
 [   56.507613] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA  
 [   56.507665] usbcore: registered new interface driver ndiswrapper  
 [  112.674957] wlan0: no IPv6 routers present 

I would appreciate any help.  Thanks.  Oh, 1915:2234 is the chipset for my device, I verified that.

---

