---
title: "ubuntu moblock wont start please help me"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2010-07-13
I have installed moblock, moblock-control and mobloquer from the AUR, however I am unable to start moblock.

Mobloquer launches fine, and will update the blocklists fine. However, upon clicking "start" I receive the following;

Problematic Deamon status: 1

Moblock is not running*


what do i do??? please help me i have tryed loging in as root and i maked it for compleat removal? then i reinstalled it but it still gives me the same error
it was working until i changed my MAC on wlan0



when i go to MoBlock status: this is what it says

```
Current IPv4 iptables rules (this may take a while):
Chain INPUT (policy DROP 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination
4 381 blockcontrol_in all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
0 0 ACCEPT tcp -- * * 192.168.1.1 0.0.0.0/0 tcp flags:!0x17/0x02
98 12395 ACCEPT udp -- * * 192.168.1.1 0.0.0.0/0
0 0 ACCEPT all -- lo * 0.0.0.0/0 0.0.0.0/0
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 10/sec burst 5
1 340 DROP all -- wlan0 * 0.0.0.0/0 255.255.255.255
5 1160 DROP all -- * * 0.0.0.0/0 192.168.1.255
0 0 DROP all -- * * 224.0.0.0/8 0.0.0.0/0
0 0 DROP all -- * * 0.0.0.0/0 224.0.0.0/8
0 0 DROP all -- * * 255.255.255.255 0.0.0.0/0
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 state INVALID
0 0 LSI all -f * * 0.0.0.0/0 0.0.0.0/0 limit: avg 10/min burst 5
2083 2800K INBOUND all -- wlan0 * 0.0.0.0/0 0.0.0.0/0
0 0 LOG_FILTER all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 LOG flags 0 level 6 prefix `Unknown Input'
Chain FORWARD (policy DROP 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination
0 0 blockcontrol_fw all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 10/sec burst 5
0 0 LOG_FILTER all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 LOG flags 0 level 6 prefix `Unknown Forward'
Chain OUTPUT (policy DROP 1 packets, 166 bytes)
pkts bytes target prot opt in out source destination
4 230 blockcontrol_out all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
0 0 ACCEPT tcp -- * * 192.168.1.4 192.168.1.1 tcp dpt:53
101 6403 ACCEPT udp -- * * 192.168.1.4 192.168.1.1 udp dpt:53
0 0 ACCEPT all -- * lo 0.0.0.0/0 0.0.0.0/0
0 0 DROP all -- * * 224.0.0.0/8 0.0.0.0/0
4 640 DROP all -- * * 0.0.0.0/0 224.0.0.0/8
0 0 DROP all -- * * 255.255.255.255 0.0.0.0/0
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 state INVALID
1609 138K OUTBOUND all -- * wlan0 0.0.0.0/0 0.0.0.0/0
0 0 LOG_FILTER all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 LOG flags 0 level 6 prefix `Unknown Output'
Chain INBOUND (1 references)
pkts bytes target prot opt in out source destination
2070 2799K ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
4 304 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:2123
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:2123
9 456 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:4672
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:4672
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:4671
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:4671
0 0 LSI all -- * * 0.0.0.0/0 0.0.0.0/0
Chain LOG_FILTER (5 references)
pkts bytes target prot opt in out source destination
Chain LSI (2 references)
pkts bytes target prot opt in out source destination
0 0 LOG_FILTER all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 LOG tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
0 0 DROP tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp flags:0x17/0x02
0 0 LOG tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
0 0 DROP tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp flags:0x17/0x04
0 0 LOG icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
0 0 DROP icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 8
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0
Chain LSO (0 references)
pkts bytes target prot opt in out source destination
0 0 LOG_FILTER all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound '
0 0 REJECT all -- * * 0.0.0.0/0 0.0.0.0/0 reject-with icmp-port-unreachable
Chain OUTBOUND (1 references)
pkts bytes target prot opt in out source destination
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0
1577 137K ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
3 228 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
29 1308 ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0
Chain blockcontrol_fw (1 references)
pkts bytes target prot opt in out source destination
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa
0 0 RETURN all -- * * 0.0.0.0/0 192.168.1.1
0 0 RETURN all -- * * 192.168.1.0/24 192.168.1.0/24
0 0 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Chain blockcontrol_in (1 references)
pkts bytes target prot opt in out source destination
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa
0 0 RETURN all -- lo * 0.0.0.0/0 0.0.0.0/0
1 229 RETURN all -- * * 192.168.1.0/24 0.0.0.0/0
3 152 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Chain blockcontrol_out (1 references)
pkts bytes target prot opt in out source destination
0 0 REJECT all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa reject-with icmp-port-unreachable
0 0 RETURN all -- * lo 0.0.0.0/0 0.0.0.0/0
3 186 RETURN all -- * * 0.0.0.0/0 192.168.1.1
0 0 RETURN all -- * * 0.0.0.0/0 192.168.1.0/24
0 0 RETURN all -- * * 0.0.0.0/0 204.16.33.161
0 0 RETURN all -- * * 0.0.0.0/0 204.16.33.162
0 0 RETURN all -- * * 0.0.0.0/0 204.16.33.164
0 0 RETURN all -- * * 0.0.0.0/0 68.71.51.58
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:443
1 44 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:80
0 0 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Please check if the above printed iptables rules are correct!
* moblock is not running
* blockcontrol.wd is running
PID: 14605 CMD: /bin/sh /usr/bin/blockcontrol.wd

```



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by jre on 2010-07-14
We found the soltution in another thread:

It is the IPFilterX that causes the problems. This list is in ipfilter.dat format (leading zeros in the IP e.g. 001.001.001.001). MoBlock only accepts either p2p format (1.1.1.1) which is used by most lists, or ipfilter.dat format.

Generally it is no good idea to use too many lists. Read their description and then decide whether you really want to use it. IPFilterX is designed as a very slim list in contrast to Bluetack's level1, or TBG's Primary Threats. So I see no point in using those together.

---

### Post by xenosaga456 on 2010-07-14
wow thanks i ****ing love u i have been trying for DAYS to get that fixed\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

