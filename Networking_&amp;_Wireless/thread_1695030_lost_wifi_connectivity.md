---
title: "lost wifi connectivity"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by dp42 on 2011-02-25
Hi all,

 I am running Ubuntu 10.10 Netbook Remix on a Toshiba Netbook NB300. After performing an upgrade I find myself unable to connect to my wirless network and have lost the wifi icon in the task bar. Ethernet connectivity is however working.

   iwconfig shows:

 wlan0     IEEE 802.11bgn  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm  
           Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:off

 ifconfig shows

 wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 wlan0:avahi Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
         inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:255.255.0.0
         UP BROADCAST MULTICAST  MTU:1500  Metric:1

  su -c 'iwlist wlan0 scan' lists my wifi network and several other local wireless networks.

 dmesg | grep wlan0 shows:

 [   43.520702] ADDRCONF(NETDEV_UP): wlan0: link is not ready

 Can anyone reccomend steps I need to take to bring back wireless connectivity to my netbook and restore the wifi icon to the task bar. I appreciate any thoughts or comments.

---

### Post by grahammechanical on 2011-02-25
1) Make sure that wireless is switched on by the keyboard key combination.

2) Make sure that Network Manager is on the list of Startup Applications. go to System>Preferences>Startup Applications.

3) To get the network icon showing in the top panel - right click the top panel and select Add to Panel and select Notification Area.

4) Reboot.

regards.

---

### Post by dp42 on 2011-02-25
Thank you Graham,

 It seems that network manager had been completely removed/uninstalled from my system. I believe this occured during a recent upgrade.

 Reinstalling Network Manager and configuring the tool to manage my networking has restored wifi.

 I appreciate your time and consideration!

 cheers

---

