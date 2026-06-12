---
title: "Wireless goes up, wireless goes down. up, down. up, down."
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by rsakuma on 2012-05-09
I have an odd isue. Every ten seconds or so, my computer will no longer display web pages. Wifi works fine, I can access local things like my router an modem, but pages don't load, they don't even time out. I can disconnect and reconnect for the pages to load properly, but doing this every ten seconds is INSANE.

I think I found a temp fix, setting terminal to ping google nonstop has kept the network alive. But I don't want to do this forever, I'd love to have this fixed.

Network card:
 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)


edit: pinging wasn't a temp fix. Also, odd thing I found....while pinging, it didn't say "network unreachable" until I manualy disconnected, it just....didn't put any new text on the lines.

64 bytes from 64.212.100.110: icmp_req=409 ttl=54 time=33.5 ms
64 bytes from 64.212.100.110: icmp_req=410 ttl=54 time=34.8 ms
64 bytes from 64.212.100.110: icmp_req=411 ttl=54 time=33.1 ms
**It has here for 45 seconds until I killed the net**
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 64.212.100.110: icmp_req=512 ttl=54 time=32.9 ms
[/b]

---

