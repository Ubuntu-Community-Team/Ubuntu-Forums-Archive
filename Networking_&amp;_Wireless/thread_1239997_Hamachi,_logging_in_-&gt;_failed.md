---
title: "Hamachi, logging in -&gt; failed"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by #Peter on 2009-08-14
Hello!
I'm using ubuntu 9.04 and I'm trying to get my hamachi working. Everything works fine until I'm going to log in. This is the output I get from debug:
```
14 12:04:15.002 [  23] [ 4006] ipc: login 
14 12:04:15.002 [  23] [ 4006] ses: set_reconn(no)
14 12:04:15.002 [  23] [ 4006] ses: go_online
14 12:04:15.002 [  23] [ 4006] ses: state 1.1 -> 2.0
14 12:04:15.013 [  24] [ 4006] ses: resolved bibi.hamachi.cc -> 77.242.193.229
14 12:04:15.013 [  24] [ 4006] ses: state 2.0 -> 2.1
14 12:04:15.013 [  24] [ 4006] ses: state 2.1 -> 3.0
14 12:04:15.013 [  24] [ 4006] ses: connecting to 77.242.193.229:12975 ..
14 12:04:15.092 [  25] [ 4006] ses: io_ready -- 192.168.0.122:47910
14 12:04:15.092 [  25] [ 4006] ses: state 3.0 -> 3.1
14 12:04:15.092 [  25] [ 4006] ses: state 3.1 -> 4.0
14 12:04:15.093 [  25] [ 4006] ses: sending helo ..
14 12:04:15.214 [  26] [ 4006] ses: received helo.ok
14 12:04:15.255 [  26] [ 4006] ses: state 4.0 -> 4.1
14 12:04:15.255 [  26] [ 4006] ses: state 4.1 -> 6.0
14 12:04:15.271 [  26] [ 4006] ses: sending auth 5.85.30.33 ..
14 12:04:15.688 [  29] [ 4006] ses: error 6  0 9
14 12:04:15.689 [  29] [ 4006] ses: set_reconn(no)
14 12:04:15.689 [  29] [ 4006] ses: go_offline
14 12:04:15.689 [  29] [ 4006] ses: state 6.0 -> 1.0
14 12:04:15.689 [  29] [ 4006] ipc: socket_send() failed with 32
14 12:04:15.689 [  29] [ 4006] ses: state 1.0 -> 1.1
14 12:04:15.689 [  29] [ 4006] ses: purging state ..
```

This is the output from ifconfig about ham0:
```
ham0      Link encap:Ethernet  HWaddr ae:d3:ab:25:02:b1  
          inet addr:5.85.30.33  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
I do not have any firewall on my computer, and it works perfectly on XP (I dual-boot). Any ideas? I've been searching for days for a solution, but everyone else seems to get different errors :(.

---

### Post by #Peter on 2009-08-14
Tried to reinstall it today, and to my surprise it worked!

Admin can close this thread or whatever..

---

