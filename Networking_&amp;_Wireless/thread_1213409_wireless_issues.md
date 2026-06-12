---
title: "wireless issues"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by tony241 on 2009-07-14
I have installed the newest edition of ubuntu, and downloaded all new updates. I have a netgear usb wireless adapter, and it worked great for the first day or so. Now I can connect to the network but I cannot get on the internet or get to any of my other computers shared on the network, all of which I was able to do initially. I have tried removing the adapter and deleting the connection then reinstalling, but I get the same results. I can ping the router address and it averages 10ms. Any help would be greatly appreciated.

---

### Post by superprash2003 on 2009-07-15
post output of
1)ifconfig
2)iwconfig

---

### Post by tony241 on 2009-07-15
Sorry, but I have no way of getting a screen shot at the moment, so I typed what I got: 
tony24@garage:~$ ifconfig
wlan0 Link encap:Ethernet HWaddr 00:1e:2a:37:43:0f
inet addr:192.168.2.8 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80: :21e:2aff:fe37:430f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1492 METRIC:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets: 71 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3341 (3.3 KB) TX bytes:12277 (12.2 KB)
&#12288;
tony24@garage:~$ iwconfig
wlan0 IEEE 802.11bg ESSID:" "
Mode:Managed Frequency:2.427 GHz Access Point: 00:17:3F:7D:98:7C
Bit Rate=1 Mb/s Tx-Power=20 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management:off
Link Quality=60/100 Signal level:-41dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
Thanks for the response!

---

### Post by superprash2003 on 2009-07-17
it doesnt seem to be connecting to any network according to the iwconfig output.. please post output of **sudo iwlist scanning** . you could use the copy paste method and maybe copy it to a file and transfer it instead of typing the whole thign

---

