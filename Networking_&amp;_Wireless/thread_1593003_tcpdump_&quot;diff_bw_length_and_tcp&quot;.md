---
title: "tcpdump &quot;diff b/w length and tcp&quot;"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by pragya on 2010-10-11
hi, i was experimenting with the tcpdump command when i got stuck at a point.

root@ubuntu:~# tcpdump -i 3 -c 5 -n
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
13:47:12.698118 IP 86.125.16.150.62091 > 192.168.1.2.51413: Flags [.], seq 3226090414:3226090950, ack 4044818052, win 4351, [COLOR="Yellow"]length 536[/COLOR]
13:47:12.698167 IP 192.168.1.2.51413 > 86.125.16.150.62091: Flags [.], ack 536, win 5158, options [nop,nop,sack 1 {1072:3216}], [COLOR="Yellow"]length 0[/COLOR]

root@ubuntu:~# tcpdump -i 3 -c 5 -n -q
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
13:47:18.341596 IP 41.196.199.145.62245 > 192.168.1.2.51413:[COLOR="Yellow"] tcp 536[/COLOR]
13:47:18.341641 IP 192.168.1.2.51413 > 41.196.199.145.62245: [COLOR="Yellow"]tcp 0[/COLOR]

Do the words "length" and "tcp" serve the same purpose??

---

