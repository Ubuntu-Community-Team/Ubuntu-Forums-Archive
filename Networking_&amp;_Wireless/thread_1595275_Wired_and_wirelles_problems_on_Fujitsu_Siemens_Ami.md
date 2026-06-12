---
title: "Wired and wirelles problems on Fujitsu Siemens Amilo PA 2510"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by SerafeimG on 2010-10-13
Hallo to everybody!
I will share my problem with you...

My laptop is Fujitsu Siemens Amilo PA 2510. I have successfully upgraded to Ubuntu 10.10 64 bit. The general impression is good but I have severe problems with my Internet connections.

My chipset must be atheros ath5k.

_When I try to connect wired_: I can successfully connect in my home wired connection but the connection is extremely slow. Most of the times I can not even browse to websites, although without loosing the connection.

_When I try to connect wireless_: Here we have 3 cases:
1. It cannot recognise that I have the wireless activated. As a result, I cannot find any network to connect. 
2. It can recognise that the wireless is activated and find possible networks although it cannot connect.
3. It can recognise that the wireless is activated, find possible networks and connect successfully. However, during the time, in can be in 5 minutes or in 2 and 5 hours!, it disconnects and we go back to the previous 2 cases.

It worths to mention that if I do not activate wireless from scratch, before ubuntu boots the first case is inevitable.

I opened the Log File Viewer and clicked on the syslog section to view the log files in order recognise the problem. Being unexperienced, I couldn't understand the issue. My syslogs are:


When I am connected wired:

ep 27 15:02:19 Serafeim-Linux kernel: [ 8442.620262] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=94.159.154.242 DST=192.168.2.5 LEN=95 TOS=0x00 PREC=0x00 TTL=114 ID=3455 PROTO=UDP SPT=52461 DPT=6881 LEN=75
Sep 27 15:02:19 Serafeim-Linux kernel: [ 8442.630101] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=94.159.154.242 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=114 ID=3463 PROTO=UDP SPT=52461 DPT=6881 LEN=38
Sep 27 15:02:19 Serafeim-Linux kernel: [ 8442.987652] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=86.51.125.218 DST=192.168.2.5 LEN=131 TOS=0x00 PREC=0x00 TTL=111 ID=22367 PROTO=UDP SPT=56371 DPT=6881 LEN=111
Sep 27 15:02:24 Serafeim-Linux kernel: [ 8447.342290] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=94.159.154.242 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=114 ID=3911 PROTO=UDP SPT=52461 DPT=6881 LEN=38
Sep 27 15:02:30 Serafeim-Linux kernel: [ 8453.762092] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=94.159.154.242 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=114 ID=4594 PROTO=UDP SPT=52461 DPT=6881 LEN=38
Sep 27 15:02:33 Serafeim-Linux kernel: [ 8456.490203] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=82.234.11.58 DST=192.168.2.5 LEN=131 TOS=0x00 PREC=0x00 TTL=113 ID=27046 PROTO=UDP SPT=50898 DPT=6881 LEN=111
Sep 27 15:02:48 Serafeim-Linux kernel: [ 8471.377699] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=88.203.68.116 DST=192.168.2.5 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=27287 PROTO=UDP SPT=53010 DPT=6881 LEN=75
Sep 27 15:02:48 Serafeim-Linux kernel: [ 8471.395083] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=88.203.68.116 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=27291 PROTO=UDP SPT=53010 DPT=6881 LEN=38
Sep 27 15:02:51 Serafeim-Linux kernel: [ 8474.806261] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=88.203.68.116 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=27410 PROTO=UDP SPT=53010 DPT=6881 LEN=38
Sep 27 15:02:58 Serafeim-Linux kernel: [ 8481.527071] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=109.76.107.45 DST=192.168.2.5 LEN=131 TOS=0x00 PREC=0x00 TTL=115 ID=19735 PROTO=UDP SPT=59553 DPT=6881 LEN=111
Sep 27 15:03:27 Serafeim-Linux kernel: [ 8510.471730] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=78.149.57.239 DST=192.168.2.5 LEN=131 TOS=0x00 PREC=0x00 TTL=113 ID=5876 PROTO=UDP SPT=27704 DPT=6881 LEN=111
Sep 27 15:03:27 Serafeim-Linux kernel: [ 8510.657447] __ratelimit: 4 callbacks suppressed
Sep 27 15:03:27 Serafeim-Linux kernel: [ 8510.657455] ath5k phy0: gain calibration timeout (2412MHz)
Sep 27 15:03:27 Serafeim-Linux kernel: [ 8511.048003] ath5k phy0: gain calibration timeout (2417MHz)
Sep 27 15:03:28 Serafeim-Linux kernel: [ 8511.434703] ath5k phy0: gain calibration timeout (2422MHz)
Sep 27 15:03:28 Serafeim-Linux kernel: [ 8511.830906] ath5k phy0: gain calibration timeout (2427MHz)
Sep 27 15:03:29 Serafeim-Linux kernel: [ 8512.227138] ath5k phy0: gain calibration timeout (2432MHz)
Sep 27 15:03:29 Serafeim-Linux kernel: [ 8512.616482] ath5k phy0: gain calibration timeout (2437MHz)
Sep 27 15:03:29 Serafeim-Linux kernel: [ 8513.005867] ath5k phy0: gain calibration timeout (2442MHz)
Sep 27 15:03:30 Serafeim-Linux kernel: [ 8513.334324] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=41.235.70.115 DST=192.168.2.5 LEN=303 TOS=0x00 PREC=0x00 TTL=114 ID=12921 PROTO=UDP SPT=52140 DPT=6881 LEN=283
Sep 27 15:03:30 Serafeim-Linux kernel: [ 8513.394297] ath5k phy0: gain calibration timeout (2447MHz)
Sep 27 15:03:30 Serafeim-Linux kernel: [ 8513.784017] ath5k phy0: gain calibration timeout (2452MHz)
Sep 27 15:03:30 Serafeim-Linux kernel: [ 8514.175883] ath5k phy0: gain calibration timeout (2457MHz)
Sep 27 15:03:42 Serafeim-Linux kernel: [ 8525.317602] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=188.22.143.148 DST=192.168.2.5 LEN=95 TOS=0x00 PREC=0x00 TTL=116 ID=31282 PROTO=UDP SPT=56783 DPT=6881 LEN=75
Sep 27 15:03:42 Serafeim-Linux kernel: [ 8525.318218] [UFW BLOCK] IN=eth0 OUT= MAC=00:03:0d:6d:e0:5d:00:1a:2a:8a:1d:c6:08:00 SRC=188.22.143.148 DST=192.168.2.5 LEN=58 TOS=0x00 PREC=0x00 TTL=116 ID=31283 PROTO=UDP SPT=56783 DPT=6881 LEN=38


When I am connected wireless and disconnects later on:

Sep  2 16:28:37 Serafeim-Linux kernel: [  125.564378] ath5k phy0: gain calibration timeout (2412MHz)
Sep  2 16:28:37 Serafeim-Linux kernel: [  125.972539] ath5k phy0: gain calibration timeout (2417MHz)
Sep  2 16:28:38 Serafeim-Linux kernel: [  126.362151] ath5k phy0: gain calibration timeout (2422MHz)
Sep  2 16:28:38 Serafeim-Linux kernel: [  126.754883] ath5k phy0: gain calibration timeout (2427MHz)
Sep  2 16:28:38 Serafeim-Linux kernel: [  127.144903] ath5k phy0: gain calibration timeout (2432MHz)
Sep  2 16:28:39 Serafeim-Linux kernel: [  127.534500] ath5k phy0: gain calibration timeout (2437MHz)
Sep  2 16:28:39 Serafeim-Linux kernel: [  127.935029] ath5k phy0: gain calibration timeout (2442MHz)
Sep  2 16:28:40 Serafeim-Linux kernel: [  128.321446] ath5k phy0: gain calibration timeout (2447MHz)
Sep  2 16:28:40 Serafeim-Linux kernel: [  128.714731] ath5k phy0: gain calibration timeout (2452MHz)
Sep  2 16:28:40 Serafeim-Linux kernel: [  129.114551] ath5k phy0: gain calibration timeout (2457MHz)
Sep  2 16:28:47 Serafeim-Linux kernel: [  135.835329] __ratelimit: 4 callbacks suppressed
Sep  2 16:28:47 Serafeim-Linux kernel: [  135.835339] ath5k phy0: gain calibration timeout (2412MHz)
Sep  2 16:28:47 Serafeim-Linux kernel: [  136.233080] ath5k phy0: gain calibration timeout (2417MHz)
Sep  2 16:28:48 Serafeim-Linux kernel: [  136.625393] ath5k phy0: gain calibration timeout (2422MHz)
Sep  2 16:28:48 Serafeim-Linux kernel: [  137.012124] ath5k phy0: gain calibration timeout (2427MHz)
Sep  2 16:28:49 Serafeim-Linux kernel: [  137.412186] ath5k phy0: gain calibration timeout (2432MHz)
Sep  2 16:28:49 Serafeim-Linux kernel: [  137.802252] ath5k phy0: gain calibration timeout (2437MHz)
Sep  2 16:28:49 Serafeim-Linux kernel: [  138.197153] ath5k phy0: gain calibration timeout (2442MHz)
Sep  2 16:28:50 Serafeim-Linux kernel: [  138.584979] ath5k phy0: gain calibration timeout (2447MHz)
Sep  2 16:28:50 Serafeim-Linux kernel: [  138.981469] ath5k phy0: gain calibration timeout (2452MHz)
Sep  2 16:28:51 Serafeim-Linux kernel: [  139.372540] ath5k phy0: gain calibration timeout (2457MHz)
Sep  2 16:28:57 Serafeim-Linux kernel: [  146.096966] __ratelimit: 4 callbacks suppressed
Sep  2 16:28:57 Serafeim-Linux kernel: [  146.096976] ath5k phy0: gain calibration timeout (2412MHz)
Sep  2 16:28:58 Serafeim-Linux kernel: [  146.491479] ath5k phy0: gain calibration timeout (2417MHz)
Sep  2 16:28:58 Serafeim-Linux kernel: [  146.884331] ath5k phy0: gain calibration timeout (2422MHz)
Sep  2 16:28:59 Serafeim-Linux kernel: [  147.284862] ath5k phy0: gain calibration timeout (2427MHz)
Sep  2 16:28:59 Serafeim-Linux kernel: [  147.674367] ath5k phy0: gain calibration timeout (2432MHz)
Sep  2 16:28:59 Serafeim-Linux kernel: [  148.064312] ath5k phy0: gain calibration timeout (2437MHz)
Sep  2 16:29:00 Serafeim-Linux kernel: [  148.461692] ath5k phy0: gain calibration timeout (2442MHz)
Sep  2 16:29:00 Serafeim-Linux kernel: [  148.872555] ath5k phy0: gain calibration timeout (2447MHz)
Sep  2 16:29:00 Serafeim-Linux kernel: [  149.266952] ath5k phy0: gain calibration timeout (2452MHz)
Sep  2 16:29:01 Serafeim-Linux kernel: [  149.661545] ath5k phy0: gain calibration timeout (2457MHz)
Sep  2 16:29:08 Serafeim-Linux kernel: [  156.374341] __ratelimit: 4 callbacks suppressed
Sep  2 16:29:08 Serafeim-Linux kernel: [  156.374351] ath5k phy0: gain calibration timeout (2412MHz)
Sep  2 16:29:08 Serafeim-Linux kernel: [  156.774316] ath5k phy0: gain calibration timeout (2417MHz)
Sep  2 16:29:08 Serafeim-Linux kernel: [  157.184383] ath5k phy0: gain calibration timeout (2422MHz)
Sep  2 16:29:09 Serafeim-Linux kernel: [  157.581593] ath5k phy0: gain calibration timeout (2427MHz)
Sep  2 16:29:09 Serafeim-Linux kernel: [  157.984332] ath5k phy0: gain calibration timeout (2432MHz)
Sep  2 16:29:10 Serafeim-Linux kernel: [  158.384369] ath5k phy0: gain calibration timeout (2437MHz)
Sep  2 16:29:10 Serafeim-Linux kernel: [  158.783188] ath5k phy0: gain calibration timeout (2442MHz)
Sep  2 16:29:10 Serafeim-Linux kernel: [  159.184398] ath5k phy0: gain calibration timeout (2447MHz)
Sep  2 16:29:11 Serafeim-Linux kernel: [  159.581462] ath5k phy0: gain calibration timeout (2452MHz)
Sep  2 16:29:11 Serafeim-Linux kernel: [  159.984548] ath5k phy0: gain calibration timeout (2457MHz)
Sep  2 16:29:18 Serafeim-Linux kernel: [  166.731135] __ratelimit: 4 callbacks suppressed
Sep  2 16:29:18 Serafeim-Linux kernel: [  166.731145] ath5k phy0: gain calibration timeout (2412MHz)
Sep  2 16:29:18 Serafeim-Linux kernel: [  167.138590] ath5k phy0: gain calibration timeout (2417MHz)
Sep  2 16:29:19 Serafeim-Linux kernel: [  167.539912] ath5k phy0: gain calibration timeout (2422MHz)
Sep  2 16:29:19 Serafeim-Linux kernel: [  167.941643] ath5k phy0: gain calibration timeout (2427MHz)
Sep  2 16:29:20 Serafeim-Linux kernel: [  168.344353] ath5k phy0: gain calibration timeout (2432MHz)
Sep  2 16:29:20 Serafeim-Linux kernel: [  168.754333] ath5k phy0: gain calibration timeout (2437MHz)
Sep  2 16:29:20 Serafeim-Linux kernel: [  169.144633] ath5k phy0: gain calibration timeout (2442MHz)
Sep  2 16:29:21 Serafeim-Linux kernel: [  169.554365] ath5k phy0: gain calibration timeout (2447MHz)
Sep  2 16:29:21 Serafeim-Linux kernel: [  169.960364] ath5k phy0: gain calibration timeout (2452MHz)
Sep  2 16:29:22 Serafeim-Linux kernel: [  170.361462] ath5k phy0: gain calibration timeout (2457MHz)
Sep  2 16:29:27 Serafeim-Linux NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Sep  2 16:29:27 Serafeim-Linux NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep  2 16:29:27 Serafeim-Linux NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Sep  2 16:29:27 Serafeim-Linux NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected


Thank you all in advance! Any idea will be useful and appreciated as Internet connection is frequently used and a strong connection is undoubtedly essential.

---

### Post by SerafeimG on 2010-10-31
I also tried the madwifi as well as the windows driver but with no result. The problems are still there.

---

