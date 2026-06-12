---
title: "tcpdump shows lots of activity"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by amsterdamharu on 2011-01-24
The only window that's open is the terminal running this command, no pidgin, skype, samba, torrent or anything I can think of is using the network yet there is ***** load of output from tcpdump.
I was hoping to use this to check where certain applications connect to and what messages they send but when I'm doing nothing there is already more output than I can go through.


Running tcpdump for less than 10 seconds gives me the following output:

```
16:13:22.015683 IP ns.hihkptt.net.cn.domain > desk.local.56598: 46887 1/2/2 (166)
16:13:22.016251 IP ns.hihkptt.net.cn.domain > desk.local.60099: 21168 1/2/2 (166)
16:13:22.016743 IP ns.hihkptt.net.cn.domain > desk.local.42325: 50346 1/2/2 (166)
16:13:22.034733 IP ns.hihkptt.net.cn.domain > desk.local.41441: 63658 1/2/0 (134)
16:13:22.035215 IP ns.hihkptt.net.cn.domain > desk.local.42865: 37537 1/2/0 (134)
16:13:22.036124 IP ns.hihkptt.net.cn.domain > desk.local.35006: 7520 1/2/0 (134)
16:13:22.036569 IP ns.hihkptt.net.cn.domain > desk.local.38480: 51322 1/2/0 (134)
16:13:22.066006 ARP, Reply 192.168.0.1 is-at 00:b0:0c:02:60:9c (oui Unknown), length 46
16:13:22.074192 IP ns.hihkptt.net.cn.domain > desk.local.50505: 35630 1/2/0 (134)
16:13:22.074640 IP ns.hihkptt.net.cn.domain > desk.local.38312: 31402 1/2/0 (134)
16:13:22.082717 IP ns.hihkptt.net.cn.domain > desk.local.37192: 49764 1/2/0 (134)
16:13:22.723763 IP p8444d0.tokynt01.ap.so-net.ne.jp.52411 > desk.local.18914: Flags [S], seq 1641154025, win 8192, options [mss 1414,nop,nop,sackOK], length 0
16:13:22.723872 IP desk.local.18914 > p8444d0.tokynt01.ap.so-net.ne.jp.52411: Flags [R.], seq 0, ack 1641154026, win 0, length 0
16:13:22.724181 IP p8444d0.tokynt01.ap.so-net.ne.jp.13570 > desk.local.18914: UDP, length 30
16:13:22.724244 IP desk.local > p8444d0.tokynt01.ap.so-net.ne.jp: ICMP desk.local udp port 18914 unreachable, length 66
16:13:22.759804 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:22.787468 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
16:13:22.951350 IP desk.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 122.160.67.112.in-addr.arpa. (45)
16:13:23.362655 IP p8444d0.tokynt01.ap.so-net.ne.jp.52411 > desk.local.18914: Flags [S], seq 1641154025, win 8192, options [mss 1414,nop,nop,sackOK], length 0
16:13:23.362760 IP desk.local.18914 > p8444d0.tokynt01.ap.so-net.ne.jp.52411: Flags [R.], seq 0, ack 1, win 0, length 0
16:13:24.001692 IP p8444d0.tokynt01.ap.so-net.ne.jp.52411 > desk.local.18914: Flags [S], seq 1641154025, win 8192, options [mss 1414,nop,nop,sackOK], length 0
16:13:24.001795 IP desk.local.18914 > p8444d0.tokynt01.ap.so-net.ne.jp.52411: Flags [R.], seq 0, ack 1, win 0, length 0
16:13:24.432246 IP cm-83-97-149-73.telecable.es.1311 > 192.168.0.18.6256: Flags [S], seq 504414268, win 65535, options [mss 1452,nop,nop,sackOK], length 0
16:13:24.819807 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:24.820252 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
16:13:24.952746 IP desk.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 122.160.67.112.in-addr.arpa. (45)
16:13:26.042363 IP 126.24.114.112.broad.km.yn.dynamic.163data.com.cn.2783 > 192.168.0.18.6256: Flags [S], seq 1539582133, win 65535, options [mss 1440,nop,wscale 0,nop,nop,TS val 0 ecr 0,nop,nop,sackOK], length 0
16:13:26.566445 ARP, Reply 192.168.0.1 is-at 00:b0:0c:02:60:9c (oui Unknown), length 46
16:13:26.851498 IP desk.local.44107 > ns.hihkptt.net.cn.domain: 12029+ PTR? 20.13.9.121.in-addr.arpa. (42)
16:13:26.862361 IP ns.hihkptt.net.cn.domain > desk.local.44107: 12029 NXDomain 0/1/0 (102)
16:13:26.872338 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:26.899257 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
16:13:26.963702 IP desk.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 20.13.9.121.in-addr.arpa. (42)
16:13:27.965190 IP desk.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 20.13.9.121.in-addr.arpa. (42)
16:13:27.996439 IP HSI-KBW-046-005-211-070.hsi8.kabel-badenwuerttemberg.de.2418 > 192.168.0.18.6256: Flags [S], seq 3992874492, win 65535, options [mss 1452,nop,nop,sackOK], length 0
16:13:27.996706 IP desk.local.45970 > ns.hihkptt.net.cn.domain: 26307+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.996883 IP desk.local.50121 > ns.hihkptt.net.cn.domain: 25806+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997053 IP desk.local.56254 > ns.hihkptt.net.cn.domain: 45446+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997220 IP desk.local.56616 > ns.hihkptt.net.cn.domain: 19612+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997389 IP desk.local.50784 > ns.hihkptt.net.cn.domain: 57471+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997549 IP desk.local.45161 > ns.hihkptt.net.cn.domain: 43681+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997702 IP desk.local.56317 > ns.hihkptt.net.cn.domain: 50001+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.997861 IP desk.local.42225 > ns.hihkptt.net.cn.domain: 62259+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.998020 IP desk.local.51391 > ns.hihkptt.net.cn.domain: 46038+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.998185 IP desk.local.60458 > ns.hihkptt.net.cn.domain: 14808+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.998349 IP desk.local.42393 > ns.hihkptt.net.cn.domain: 60022+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:27.998514 IP desk.local.38470 > ns.hihkptt.net.cn.domain: 45269+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:28.441469 IP ns.hihkptt.net.cn.domain > desk.local.50784: 57471 1/4/4 (263)
16:13:28.442425 IP ns.hihkptt.net.cn.domain > desk.local.45161: 43681 1/4/4 (263)
16:13:28.442896 IP ns.hihkptt.net.cn.domain > desk.local.42225: 62259 1/4/4 (263)
16:13:28.443877 IP ns.hihkptt.net.cn.domain > desk.local.56317: 50001 1/4/4 (263)
16:13:28.702816 IP ns.hihkptt.net.cn.domain > desk.local.50121: 25806 1/4/4 (263)
16:13:28.703771 IP ns.hihkptt.net.cn.domain > desk.local.38470: 45269 1/4/4 (263)
16:13:28.704301 IP ns.hihkptt.net.cn.domain > desk.local.42393: 60022 1/4/4 (263)
16:13:28.705308 IP ns.hihkptt.net.cn.domain > desk.local.56254: 45446 1/4/4 (263)
16:13:28.706276 IP ns.hihkptt.net.cn.domain > desk.local.60458: 14808 1/4/4 (263)
16:13:28.707027 IP ns.hihkptt.net.cn.domain > desk.local.51391: 46038 1/4/4 (263)
16:13:28.879515 IP ns.hihkptt.net.cn.domain > desk.local.45970: 26307 1/4/4 (263)
16:13:28.912960 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:28.929483 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
16:13:29.541615 IP ns.hihkptt.net.cn.domain > desk.local.56616: 19612 1/4/4 (263)
16:13:29.966588 IP desk.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 20.13.9.121.in-addr.arpa. (42)
16:13:30.442923 IP cm-83-97-149-73.telecable.es.1311 > 192.168.0.18.6256: Flags [S], seq 504414268, win 65535, options [mss 1452,nop,nop,sackOK], length 0
16:13:30.994404 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:31.015786 IP HSI-KBW-046-005-211-070.hsi8.kabel-badenwuerttemberg.de.2418 > 192.168.0.18.6256: Flags [S], seq 3992874492, win 65535, options [mss 1452,nop,nop,sackOK], length 0
16:13:31.022442 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
16:13:31.066904 ARP, Reply 192.168.0.1 is-at 00:b0:0c:02:60:9c (oui Unknown), length 46
16:13:31.866112 IP desk.local.42173 > ns.hihkptt.net.cn.domain: 41987+ PTR? 126.24.114.112.in-addr.arpa. (45)
16:13:31.927474 IP ns.hihkptt.net.cn.domain > desk.local.42173: 41987 1/2/2 (194)
16:13:31.928721 IP desk.local.56607 > ns.hihkptt.net.cn.domain: 23531+ PTR? 73.149.97.83.in-addr.arpa. (43)
16:13:31.939580 IP ns.hihkptt.net.cn.domain > desk.local.56607: 23531 1/2/2 (166)
16:13:31.940813 IP desk.local.49874 > ns.hihkptt.net.cn.domain: 18136+ PTR? 208.68.132.223.in-addr.arpa. (45)
16:13:31.952392 IP ns.hihkptt.net.cn.domain > desk.local.49874: 18136 1/5/3 (237)
16:13:31.953879 IP desk.local.33625 > ns.hihkptt.net.cn.domain: 31632+ PTR? 70.211.5.46.in-addr.arpa. (42)
16:13:31.964503 IP ns.hihkptt.net.cn.domain > desk.local.33625: 31632 1/4/4 (263)
16:13:33.027578 IP 112.67.160.122.1799 > 192.168.0.12.12609: UDP, length 17
16:13:33.054877 IP 121.9.13.20.17788 > 192.168.0.12.12609: UDP, length 20
```

---

### Post by sanderj on 2011-01-24
My guess is ns.hihkptt.net.cn is a DNS nameserver. So, have you configured your system to use a Chinese nameserver? Are you in China? Do you use Chinese software?

---

### Post by amsterdamharu on 2011-01-24
Yes, I am in China. What I can't figure out is why it connects to the DNS so often when nothing is actively using the Internet.

I've logged out and gone to tty1 then stopped gdm but still get lots of udp packages, maybe because my room mate uses the router and is downloading torrents?

But then still, why would my computer send packages when there is nothing to do?

Is there a way to figure out what program is sending this stuff, tried on my laptop and with live CD but traffic stays quite busy.

---

