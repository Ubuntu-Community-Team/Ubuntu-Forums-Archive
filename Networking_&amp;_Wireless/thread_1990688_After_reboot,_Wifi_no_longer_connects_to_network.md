---
title: "After reboot, Wifi no longer connects to network"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by mkozlows on 2012-05-29
I've been running 12.04 on my ThinkPad T410s, and everything's been working perfectly.  I've been running apt-get update followed by apt-get upgrade regularly, and after noticing that I hadn't rebooted for 32 days, I decided on a whim to reboot.

After the reboot, my Wifi no longer works properly.  Specifically, instead of showing a list of networks, it just shows "disconnected", and when I use "Connect to Hidden Wireless Network..." to put in the name and connection information for my network, it will give me a "Connecting" status for a long time, pop up periodically with a prompt asking me to enter the network's password, and then ultimately fail after a long, long timeout.

Below is debugging output I've seen people ask for in similar questions.  Any help would be greatly appreciated.

**iwconfig**:

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

**lspci -nn** relevant line:

Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev ff)

**lsmod | grep 'rtl'**:

rtl8192se              99989  0 
rtlwifi               111202  1 rtl8192se
mac80211              506816  2 rtl8192se,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211

**dmesg | grep 'wlan1'**:

[    3.839426] udevd[447]: renamed network interface wlan0 to wlan1
[    4.045871] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    4.078572] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  413.759515] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  568.474739] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  580.944431] ADDRCONF(NETDEV_UP): wlan1: link is not ready


**ifconfig**:

eth0      Link encap:Ethernet  HWaddr f0:de:f1:3f:33:7b  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe3f:337b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31554808 (31.5 MB)  TX bytes:4020151 (4.0 MB)
          Interrupt:20 Memory:fc600000-fc620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:423602 (423.6 KB)  TX bytes:423602 (423.6 KB)

wlan1     Link encap:Ethernet  HWaddr 00:e0:4c:81:92:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mkozlows on 2012-05-29
So as I continue to investigate this, I'm hoping I can narrow down the experimenting that I have to do.   

Because I can see the wlan1 interface, does that mean it's not a driver issue?  Or do I still need to try doing stuff with that? 

Is there any way for me to easily roll back my apt-gotten installs over the last 32 days, verify that it works, and then try to incrementally re-apply them to see what broke it?

Is there any place I can look for error messages when the Wifi is trying to connect and failing? It must be logging SOMETHING there.

---

### Post by mkozlows on 2012-05-30
Well, I guess this problem is solved, sort of.  I rebooted again, and the wireless didn't show up at all, as if it didn't exist.  I rebooted again, and it came up working perfectly fine.  

Lesson learned: Never reboot.

---

