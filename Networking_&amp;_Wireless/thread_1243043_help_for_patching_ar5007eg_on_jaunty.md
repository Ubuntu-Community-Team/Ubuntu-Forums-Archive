---
title: "help for patching ar5007eg on jaunty"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by noiz354 on 2009-08-17
hei
my wifi : ar5007eg
seem works
but i can't patch my wifi ,
it always seems like this ,
> norman@norman-laptop:~/Desktop$ patch -N -p 0 -i madwifi-ng-r4073.patch can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -dru madwifi-ng/ath/if_ath.c madwifi-ng-fixed/ath/if_ath.c
|--- madwifi-ng/ath/if_ath.c    2009-07-10 01:46:48.000000000 +0200
|+++ madwifi-ng-fixed/ath/if_ath.c    2009-07-10 01:59:58.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] 
Skipping patch.
3 out of 3 hunks ignored
can't find file to patch at input line 35
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Only in madwifi-ng-fixed/ath: if_ath.c.orig
|diff -dru madwifi-ng/ath_hal/ar5211/ar5211_reset.c madwifi-ng-fixed/ath_hal/ar5211/ar5211_reset.c
|--- madwifi-ng/ath_hal/ar5211/ar5211_reset.c    2009-07-10 01:46:38.000000000 +0200
|+++ madwifi-ng-fixed/ath_hal/ar5211/ar5211_reset.c    2009-07-10 01:52:18.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
1 out of 1 hunk ignored
can't find file to patch at input line 47
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -dru madwifi-ng/ath_hal/ar5212/ar5212_reset.c madwifi-ng-fixed/ath_hal/ar5212/ar5212_reset.c
|--- madwifi-ng/ath_hal/ar5212/ar5212_reset.c    2009-07-10 01:46:41.000000000 +0200
|+++ madwifi-ng-fixed/ath_hal/ar5212/ar5212_reset.c    2009-07-10 01:53:24.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
1 out of 1 hunk ignored
can't find file to patch at input line 59
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -dru madwifi-ng/net80211/ieee80211_scan_sta.c madwifi-ng-fixed/net80211/ieee80211_scan_sta.c
|--- madwifi-ng/net80211/ieee80211_scan_sta.c    2009-07-10 01:46:32.000000000 +0200
|+++ madwifi-ng-fixed/net80211/ieee80211_scan_sta.c    2009-07-10 01:56:57.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
2 out of 2 hunks ignored
can't find file to patch at input line 80
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -dru madwifi-ng/net80211/ieee80211_skb.c madwifi-ng-fixed/net80211/ieee80211_skb.c
|--- madwifi-ng/net80211/ieee80211_skb.c    2009-07-10 01:46:32.000000000 +0200
|+++ madwifi-ng-fixed/net80211/ieee80211_skb.c    2009-07-10 01:54:54.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
1 out of 1 hunk ignored
and this  is my iwconfig & ifconfig
> norman@norman-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

norman@norman-laptop:~/Desktop$ sudo ifconfig wifi0 up
norman@norman-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retryff   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

norman@norman-laptop:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:4f:dd:d4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe4f:ddd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18419036 (18.4 MB)  TX bytes:1575942 (1.5 MB)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.92.1  Bcast:172.16.92.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.184.1  Bcast:192.168.184.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-43-07-C7-D2-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:18860 (18.8 KB)
          Interrupt:17 

please help me to find how to patch my ar5007eg:confused:

---

