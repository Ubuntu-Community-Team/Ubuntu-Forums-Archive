---
title: "Vuze slow in Ubuntu."
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by bhishan on 2009-03-15
I use two identical Dell Inspiron 1525s. One has Ubuntu 8.10 and the other has Windows Vista. I have Vuze in both my machines. They have the same internet connections. But when I download a same torrent the Ubuntu one takes more than twice the time than that in Vista. Can anyone help?

---

### Post by 98cwitr on 2010-03-27
bump. I'm having the same problem. With vuze running, my internet connection is slow...like dialup slow (7Mbps conn. otherise). 

***Ping stats while vuze is running:***

Local Gateway
--- 192.168.x.x ping statistics ---
4265 packets transmitted, 4190 received, 1% packet loss, time 4269109ms
rtt min/avg/max/mdev = 1.006/3.259/1042.655/30.023 ms, pipe 2

Yahoo
--- any-fp.wa1.b.yahoo.com ping statistics ---
2289 packets transmitted, 2086 received, 8% packet loss, time 6011032ms
rtt min/avg/max/mdev = 24.881/1715.974/3792.611/1105.598 ms, pipe 4

Google
--- [www.l.google.com](www.l.google.com) ping statistics ---
2315 packets transmitted, 2093 received, 9% packet loss, time 6013195ms
rtt min/avg/max/mdev = 19.578/1699.686/3713.597/1104.221 ms, pipe 4


***Ping stats without Vuze running:***
Local Gateway
--- 192.168.x.x ping statistics ---
359 packets transmitted, 359 received, 0% packet loss, time 358409ms
rtt min/avg/max/mdev = 1.051/1.353/7.720/0.727 ms

Google
--- [www.l.google.com](www.l.google.com) ping statistics ---
360 packets transmitted, 359 received, 0% packet loss, time 359527ms
rtt min/avg/max/mdev = 24.574/28.214/45.627/3.220 ms

Yahoo
--- any-fp.wa1.b.yahoo.com ping statistics ---
352 packets transmitted, 352 received, 0% packet loss, time 355401ms
rtt min/avg/max/mdev = 24.498/29.930/84.005/5.689 ms

Info regarding Vuze:
UPnP is disabled
Encryption is set
Network (under Connections) is set to not use my external IP (anonymous).

PC connected to gateway modem (4 port switch built in).

---

### Post by 98cwitr on 2010-03-28
Screw it. Uninstalled Vuze, reinstalled transmission. Working great now and everything is running up to par.

---

### Post by JohnnyC35 on 2010-05-20
I think Vuze is designed to be slow. I just got Deluge back up and running and I am getting 400 avg kbps rather than 200 on my torrents and my radio stream isn't stuttering. the 400mb RAM being used by Java for Vuze prolly had a hand in this.

---

