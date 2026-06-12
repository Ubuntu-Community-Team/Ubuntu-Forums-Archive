---
title: "Wireless access point stuck while obtaining IP address"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by kdqg on 2011-09-30
I have set up a wireless access point using hostapd on my 11.04 laptop to share internet with my Android device. It worked brilliantly for a few days, but no more - I'm not sure what has changed, but the Android device seems to be stuck on "Obtaining IP address...". 

Output of ifconfig:

> br0       Link encap:Ethernet  HWaddr AA:AA:AA:AA:AA:AA
          inet addr:172.26.25.56  Bcast:172.26.25.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fe59:c438/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14372 (14.3 KB)  TX bytes:21385 (21.3 KB)

eth0      Link encap:Ethernet  HWaddr AA:AA:AA:AA:AA:AA
          inet6 addr: fe80::725a:b6ff:fe59:c438/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172529 errors:0 dropped:65 overruns:0 frame:0
          TX packets:93151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91443257 (91.4 MB)  TX bytes:13449185 (13.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1114409 (1.1 MB)  TX bytes:1114409 (1.1 MB)

mon.wlan0 Link encap:UNSPEC  HWaddr AA-AA-AA-AA-AA-AA-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2136 (2.1 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr AA:AA:AA:AA:AA:AA
          inet6 addr: fe80::924c:e5ff:fec7:a98d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133082 (133.0 KB)  TX bytes:2376958 (2.3 MB)the eth0 interface does not have an assigned IP address - I'm not sure if that has something to do with the problem?

My hostapd.conf looks like:

> driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=1
ssid=BRIDGE
hw_mode=g
channel=9
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346
macaddr_acl=0
auth_algs=3
ignore_broadcast_ssid=0
wmm_enabled=1
eapol_key_index_workaround=0
eap_server=0
own_ip_addr=127.0.0.1

---

