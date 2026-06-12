---
title: "wireless constantly on and off eee pc ath5k driver?"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by thunderman73 on 2010-05-23
Cannot get wireless to work.  Hostapd.conf had nothing inserted in it so I put the following in which I found @ [http://ubuntuforums.org/showthread.php?t=1488953](http://ubuntuforums.org/showthread.php?t=1488953)   interface=wlan0 driver=nl80211 ssid=Testnet channel=1 hw_mode=g auth_algs=1 wpa=2 wpa_passphrase="My router password"
wpa_key_mgmt=WPA-PSK wpa_pairwise=TKIP CCMP rsn_pairwise=CCMP  So it connected right away and then disconnected after opening one of my tabs.  I went back into hostapd.conf and it had erased all the info I put in there.
Is there a way to keep it from deleting this info every time.  Because it worked great for a brief second.  Otherwise it just keeps going on, then going off.  It stays off most of the time though.  Right now this is what my iwconfig reads:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WIN_613"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

if config is:
eth0      Link encap:Ethernet  HWaddr 00:23:54:23:78:37  
          inet addr:192.168.254.106  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe23:7837/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2262 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2109557 (2.1 MB)  TX bytes:420611 (420.6 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:ec:70:2a  
          inet6 addr: fe80::215:afff:feec:702a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24864 (24.8 KB)  TX bytes:5621 (5.6 KB)

Don't know if this helps.  And I'm sorry if this is a redundant post, I tried to find something on it, but could not.  Also the card is an atheros.. the exact number on the card is aw-ge780 but I cannot find a linux driver for it.  Although I know it already works, just need to tweak the system a little.... Please help.

---

### Post by sgosnell on 2010-05-23
Try this:  

[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

It might help you.

---

### Post by thunderman73 on 2010-05-23
Thanks for the link, I followed all the steps with ndiswrapper on that link because I tried madwifi and it didn't work.  ndiswrapper works great  so far.  If anyone else sees this and needs a walkthrough you cant do on the link I can send you my folder.  I took notes on every step I made for any future reference I may need or anyone else may need for that matter.

---

