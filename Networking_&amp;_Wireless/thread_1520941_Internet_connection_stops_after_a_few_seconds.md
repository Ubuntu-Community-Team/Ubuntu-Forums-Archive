---
title: "Internet connection stops after a few seconds"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by eXmifrator on 2010-06-30
Internet connection has been very unstable on my system latley. Think it was because of last update.

Basically for example i watch a video on youtube and it never fully loads. Even when i browse pages dont fully load and i must wait a few seconds before i press reload.

Does anyone have a clue why this is?

I am connected through cable.
Network is working fine on other OS

---

### Post by iponeverything on 2010-06-30
It could be just a coincidence that your isp started having issues after the upgrade..

anyway, we might get an idea of what is going by installing tcpdump and watching traffic while going to site that stalls on load. After the site has stalled, stop the tcpdump and post the last 50 lines.  Also post your routing table, a "route -n" will display it..

---

### Post by eXmifrator on 2010-06-30
tcpdump:

```

14:35:01.384296 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:01.499953 IP 192.168.57.35.netbios-ns > 192.168.57.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
14:35:02.264277 IP 192.168.57.35.netbios-ns > 192.168.57.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
14:35:02.945400 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:03.034684 ARP, Request who-has 192.168.57.252 tell 192.168.57.3, length 46
14:35:03.444279 ARP, Request who-has 192.168.57.33 tell 192.168.57.14, length 46
14:35:04.117310 ARP, Request who-has 192.168.57.31 tell 192.168.57.12, length 46
14:35:04.951465 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:05.136744 ARP, Request who-has 192.168.57.31 tell 192.168.57.12, length 46
14:35:05.384065 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:05.526372 ARP, Request who-has 192.168.57.252 tell 192.168.57.28, length 46
14:35:06.316510 ARP, Request who-has 192.168.57.252 tell 192.168.57.37, length 46
14:35:06.953922 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:06.990298 ARP, Request who-has 192.168.57.92 tell 192.168.57.35, length 46
14:35:07.182629 IP 192.168.57.12.427 > hp-device-disc.mcast.net.427: UDP, length 44
14:35:07.551760 ARP, Request who-has 192.168.57.92 tell 192.168.57.35, length 46
14:35:08.208763 ARP, Request who-has est-213-228-152-155.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:08.208960 IP miguel-artshare.local.35002 > 192.168.57.252.domain: 11629+ PTR? 155.152.228.213.in-addr.arpa. (46)
14:35:08.233629 IP 192.168.57.252.domain > miguel-artshare.local.35002: 11629 1/2/2 (158)
14:35:08.265940 ARP, Request who-has 192.168.57.31 tell 192.168.57.12, length 46
14:35:08.383634 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:08.549996 ARP, Request who-has 192.168.57.92 tell 192.168.57.35, length 46
14:35:08.940911 ARP, Request who-has est-213-228-152-155.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:08.959757 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:09.098694 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:09.443264 ARP, Request who-has 192.168.57.33 tell 192.168.57.14, length 46
14:35:09.930772 ARP, Request who-has est-213-228-152-155.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:10.034565 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:10.625930 IP6 fe80::2555:adc4:196e:ac4e.546 > ff02::1:2.547: dhcp6 solicit
14:35:10.920695 ARP, Request who-has est-213-228-152-155.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:10.967418 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:11.032791 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:11.383406 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:11.625245 IP6 fe80::2555:adc4:196e:ac4e.546 > ff02::1:2.547: dhcp6 solicit
14:35:11.911782 ARP, Request who-has condde.local tell DrayTek.router, length 46
14:35:11.911801 ARP, Request who-has NPIE11623.local tell DrayTek.router, length 46
14:35:11.911806 ARP, Request who-has 192.168.57.201 tell DrayTek.router, length 46
14:35:12.967024 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:13.208320 ARP, Request who-has 192.168.57.252 tell miguel-artshare.local, length 28
14:35:13.208679 ARP, Reply 192.168.57.252 is-at 00:1b:fc:1b:fd:29 (oui Unknown), length 46
14:35:13.625096 IP6 fe80::2555:adc4:196e:ac4e.546 > ff02::1:2.547: dhcp6 solicit
14:35:13.825541 IP6 fe80::e521:bd29:d316:b67c.64221 > ff02::1:3.hostmon: UDP, length 21
14:35:13.825562 IP 192.168.57.42.63718 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.825993 IP6 fe80::e521:bd29:d316:b67c.52080 > ff02::1:3.hostmon: UDP, length 21
14:35:13.826604 IP6 fe80::e521:bd29:d316:b67c.61374 > ff02::1:3.hostmon: UDP, length 21
14:35:13.826689 IP 192.168.57.42.59884 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.827015 IP6 fe80::e521:bd29:d316:b67c.64096 > ff02::1:3.hostmon: UDP, length 21
14:35:13.940010 IP6 fe80::e521:bd29:d316:b67c.58440 > ff02::1:3.hostmon: UDP, length 21
14:35:13.940029 IP 192.168.57.42.62535 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.940498 IP6 fe80::e521:bd29:d316:b67c.55754 > ff02::1:3.hostmon: UDP, length 21
14:35:13.947069 IP6 fe80::e521:bd29:d316:b67c.62799 > ff02::1:3.hostmon: UDP, length 21
14:35:13.947082 IP 192.168.57.42.61591 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.947484 IP6 fe80::e521:bd29:d316:b67c.52535 > ff02::1:3.hostmon: UDP, length 21
14:35:13.953648 IP6 fe80::e521:bd29:d316:b67c.55728 > ff02::1:3.hostmon: UDP, length 21
14:35:13.953661 IP 192.168.57.42.54616 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.954042 IP6 fe80::e521:bd29:d316:b67c.60541 > ff02::1:3.hostmon: UDP, length 21
14:35:13.954652 IP6 fe80::e521:bd29:d316:b67c.57404 > ff02::1:3.hostmon: UDP, length 21
14:35:13.954738 IP 192.168.57.42.62418 > 224.0.0.252.hostmon: UDP, length 21
14:35:13.955032 IP6 fe80::e521:bd29:d316:b67c.58093 > ff02::1:3.hostmon: UDP, length 21
14:35:14.001587 IP6 fe80::e521:bd29:d316:b67c.60930 > ff02::1:3.hostmon: UDP, length 21
14:35:14.001605 IP 192.168.57.42.50974 > 224.0.0.252.hostmon: UDP, length 21
14:35:14.002085 IP6 fe80::e521:bd29:d316:b67c.50217 > ff02::1:3.hostmon: UDP, length 21
14:35:14.002664 IP6 fe80::e521:bd29:d316:b67c.64395 > ff02::1:3.hostmon: UDP, length 21
14:35:14.002750 IP 192.168.57.42.52113 > 224.0.0.252.hostmon: UDP, length 21
14:35:14.003065 IP6 fe80::e521:bd29:d316:b67c.62814 > ff02::1:3.hostmon: UDP, length 21
14:35:14.031714 ARP, Request who-has 192.168.57.252 tell 192.168.57.38, length 46
14:35:14.049548 IP6 fe80::e521:bd29:d316:b67c.53913 > ff02::1:3.hostmon: UDP, length 21
14:35:14.049568 IP 192.168.57.42.58727 > 224.0.0.252.hostmon: UDP, length 21
14:35:14.050050 IP6 fe80::e521:bd29:d316:b67c.52590 > ff02::1:3.hostmon: UDP, length 21
14:35:14.050629 IP6 fe80::e521:bd29:d316:b67c.61727 > ff02::1:3.hostmon: UDP, length 21
14:35:14.050777 IP 192.168.57.42.54169 > 224.0.0.252.hostmon: UDP, length 21
14:35:14.050999 IP6 fe80::e521:bd29:d316:b67c.57076 > ff02::1:3.hostmon: UDP, length 21
14:35:14.199625 ARP, Request who-has 192.168.57.31 tell 192.168.57.12, length 46
14:35:14.971512 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:15.383178 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:15.442257 ARP, Request who-has 192.168.57.33 tell 192.168.57.14, length 46
14:35:15.812442 ARP, Request who-has 192.168.57.36 tell 192.168.57.30, length 46
14:35:15.936278 IP6 fe80::7446:4e27:2147:d6b3.546 > ff02::1:2.547: dhcp6 solicit
14:35:16.060203 ARP, Request who-has NPIE11623.local tell 192.168.57.52, length 46
14:35:16.570338 ARP, Request who-has 192.168.57.36 tell 192.168.57.30, length 46
14:35:16.935615 IP6 fe80::7446:4e27:2147:d6b3.546 > ff02::1:2.547: dhcp6 solicit
14:35:16.979142 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:17.570294 ARP, Request who-has 192.168.57.36 tell 192.168.57.30, length 46
14:35:17.624762 IP6 fe80::2555:adc4:196e:ac4e.546 > ff02::1:2.547: dhcp6 solicit
14:35:17.927151 IP6 fe80::130:f0e1:791c:208f.51874 > ff02::1:3.hostmon: UDP, length 26
14:35:17.927856 IP 192.168.57.30.59774 > 224.0.0.252.hostmon: UDP, length 26
14:35:18.027220 IP6 fe80::130:f0e1:791c:208f.51874 > ff02::1:3.hostmon: UDP, length 26
14:35:18.027239 IP 192.168.57.30.59774 > 224.0.0.252.hostmon: UDP, length 26
14:35:18.223202 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:18.248354 IP 192.168.57.30.netbios-ns > 192.168.57.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
14:35:18.382794 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:18.935357 IP6 fe80::7446:4e27:2147:d6b3.546 > ff02::1:2.547: dhcp6 solicit
14:35:18.983478 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:18.998187 IP 192.168.57.30.netbios-ns > 192.168.57.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
14:35:19.034228 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:19.747948 IP 192.168.57.30.netbios-ns > 192.168.57.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
14:35:20.032461 ARP, Request who-has 192.168.57.92 tell 192.168.57.42, length 46
14:35:20.032486 IP6 fe80::e521:bd29:d316:b67c.546 > ff02::1:2.547: dhcp6 solicit
14:35:20.369416 ARP, Request who-has est-213-228-152-156.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:20.991042 STP 802.1d, Config, Flags [none], bridge-id 81a6.00:16:47:52:c7:80.8009, length 43
14:35:21.316377 ARP, Request who-has est-213-228-152-156.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:21.382651 IP6 fe80::2555:adc4:196e:ac4e.62839 > ff02::c.1900: UDP, length 146
14:35:21.442285 ARP, Request who-has NPIE11623.local tell 192.168.57.14, length 46
14:35:21.810740 ARP, Request who-has 192.168.57.11 tell DrayTek.router, length 46
14:35:21.810760 ARP, Request who-has BRN001BA914E80B.local tell DrayTek.router, length 46
14:35:21.810764 ARP, Request who-has 192.168.57.93 tell DrayTek.router, length 46
14:35:21.897788 IP6 fe80::7446:4e27:2147:d6b3.56977 > ff02::1:3.hostmon: UDP, length 33
14:35:21.901034 IP 192.168.57.28.50847 > 224.0.0.252.hostmon: UDP, length 33
14:35:22.145269 IP 192.168.57.28.61165 > 239.255.255.250.1900: UDP, length 98
14:35:22.306315 ARP, Request who-has est-213-228-152-156.netvisao.pt tell est-213-228-152-153.netvisao.pt, length 46
14:35:22.757633 IP 192.168.57.28.17500 > 255.255.255.255.17500: UDP, length 121
14:35:22.776253 IP 192.168.57.28.17500 > 255.255.255.255.17500: UDP, length 121
14:35:22.776588 IP 192.168.57.28.17500 > 192.168.57.255.17500: UDP, length 121
14:35:22.778880 IP 192.168.57.28.17500 > 255.255.255.255.17500: UDP, length 121
^C
29738 packets captured
35217 packets received by filter
5479 packets dropped by kernel

```

think it might be the isp.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.57.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.57.1    0.0.0.0         UG    0      0        0 eth0

```

---

### Post by iponeverything on 2010-06-30
try turning off ipv6 to see if improves things.

Very strange, I don't see any port 80 traffic in your tcpdump.. 

What was the site that you were trying to reach that was not loading, while doing the tcpdump?

You might also look at lowering the MTU

---

### Post by eXmifrator on 2010-07-01
IPv6 was alwready in ignore.
The download i was doing was openframeworks, just as an example, but it happens on anything...
Its like i must make various requests. Like youtube for example... it loads 1/4 of the movie and then i must put it a little forward so it loads another fourth.
This doesnt happen on windows so it isnt the isp.

BTW i was on my office network but i took my laptop home to try with another isp and the problem continues.

---

### Post by guisardo on 2010-07-15
I'm having the exact same issue.
I've reported the bug here:
[https://bugs.launchpad.net/ubuntu/+bug/605864](https://bugs.launchpad.net/ubuntu/+bug/605864)

Regards.

---

### Post by Jaecyn42 on 2010-07-15
Two questions:

1. What are the relevant network devices at play? Can I get a lspci/lsusb?

2. Try pulling up one of the pages that does not fully load.  Wait until the loading bar is more than half full and then check "Work Offline". Does the page finish loading after doing this?



If the answer to the second question is "Yes", I had a very similar problem that I managed to correct.  Depending on the answer to #1, I might be able to tell you how to fix your problem.

---

