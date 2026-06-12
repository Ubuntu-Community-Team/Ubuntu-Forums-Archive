---
title: "Unable to connect to my ISP via VPN/PPTP"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by karabaja4 on 2010-09-10
Hello,

I'm trying to establish a connection to my ISP which uses PPTP protocol and a VPN server. The deivce I got from my ISP is a modem, not a router. The problem is my computer is unable to communicate with the ISP VPN server. 

P.S Here are the instructions for Windows XP which work: [http://portal.bnet.hr/ZG/windows-xp.htm](http://portal.bnet.hr/ZG/windows-xp.htm)

Here's what I have done so far:

dhcpcd eth0 output:

```
[badc0ffee ~]$ sudo dhcpcd eth0
dhcpcd[6774]: version 5.2.7 starting
dhcpcd[6774]: eth0: rebinding lease of 10.63.205.35
dhcpcd[6774]: eth0: acknowledged 10.63.205.35 from 83.139.64.71
dhcpcd[6774]: eth0: checking for 10.63.205.35
dhcpcd[6774]: eth0: leased 10.63.205.35 for 43200 seconds
dhcpcd[6774]: forked to background, child pid 6795
```

now, I have access to my ISP IPs, but no internet access. Now I must connect to VPN with pptp. My /etc/ppp/peers/provider file:

```
pty "pptp 10.64.0.1 --nolaunchpppd"
file /etc/ppp/options.pptp
remotename PPTP
nodefaultroute
usepeerdns
debug
name xy12345@fer.hr
ipparam provider
```

My pap-secrets file (I changed the password and username):

```
xy12345@fer.hr PPTP mypassword *
```

My ISP uses PAP, so i have commented out refuse-pap in options.pptp and also doesn't use encryption so I commented out those as well.

Here's what I get when I execute pon

```
[badc0ffee ~]$ sudo pon provider debug dump logfd 2 nodetach 
pppd options in effect:
debug debug        # (from command line)
nodetach        # (from command line)
logfd 2        # (from command line)
dump        # (from command line)
noauth        # (from /etc/ppp/options.pptp)
refuse-chap        # (from /etc/ppp/options.pptp)
refuse-mschap        # (from /etc/ppp/options.pptp)
refuse-eap        # (from /etc/ppp/options.pptp)
name xy12345@fer.hr        # (from /etc/ppp/peers/provider)
remotename PPTP        # (from /etc/ppp/peers/provider)
        # (from /etc/ppp/options.pptp)
pty pptp 10.64.0.1 --nolaunchpppd        # (from /etc/ppp/peers/provider)
crtscts        # (from /etc/ppp/options)
        # (from /etc/ppp/options)
asyncmap 0        # (from /etc/ppp/options)
mtu 1400        # (from /etc/ppp/options)
lcp-echo-failure 4        # (from /etc/ppp/options)
lcp-echo-interval 30        # (from /etc/ppp/options)
hide-password        # (from /etc/ppp/options)
ipparam provider        # (from /etc/ppp/peers/provider)
nodefaultroute        # (from /etc/ppp/peers/provider)
proxyarp        # (from /etc/ppp/options)
usepeerdns        # (from /etc/ppp/peers/provider)
nobsdcomp        # (from /etc/ppp/options.pptp)
nodeflate        # (from /etc/ppp/options.pptp)
noipx        # (from /etc/ppp/options)
using channel 8
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7f26e040> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp 10.64.0.1 --nolaunchpppd, pid 5342
sending SIGTERM to process 5342
```

My filtered TCP dump:

```
[deadbeef ~]$ sudo tcpdump -i eth0 -s 0 tcp port 1723 or proto 47 > dumpfiltered.txt
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
22:12:30.469612 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [S], seq 3663717443, win 5840, options [mss 1460,sackOK,TS val 4294964464 ecr 0,nop,wscale 6], length 0
22:12:30.608385 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [S.], seq 1544764806, ack 3663717444, win 4128, options [mss 536], length 0
22:12:30.608404 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [.], ack 1, win 5840, length 0
22:12:30.608863 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [P.], seq 1:157, ack 1, win 5840, length 156: pptp CTRL_MSGTYPE=SCCRQ PROTO_VER(1.0) FRAME_CAP(AS) BEARER_CAP(DA) MAX_CHAN(65535) FIRM_REV(1) HOSTNAME(local) VENDOR(cananian)
22:12:30.626765 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [P.], seq 1:157, ack 157, win 3972, length 156: pptp CTRL_MSGTYPE=SCCRP PROTO_VER(1.0) RESULT_CODE(1) ERR_CODE(0) FRAME_CAP(AS) BEARER_CAP(DA) MAX_CHAN(0) FIRM_REV(4608) HOSTNAME(CN-XCARNet-03-RO) VENDOR(Cisco Systems, Inc.)
22:12:30.626779 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [.], ack 157, win 6432, length 0
22:12:31.608811 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [P.], seq 157:325, ack 157, win 6432, length 168: pptp CTRL_MSGTYPE=OCRQ CALL_ID(0) CALL_SER_NUM(0) MIN_BPS(2400) MAX_BPS(10000000) BEARER_TYPE(Any) FRAME_TYPE(E) RECV_WIN(3) PROC_DELAY(0) PHONE_NO_LEN(0) PHONE_NO() SUB_ADDR()
22:12:31.642301 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [.], ack 325, win 3804, length 0
22:13:06.733356 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [P.], seq 325:341, ack 157, win 6432, length 16: pptp CTRL_MSGTYPE=CCRQ CALL_ID(0)
22:13:06.733407 IP 10.63.207.31.44466 > 10.64.0.1.pptp: Flags [F.], seq 341, ack 157, win 6432, length 0
22:13:06.749673 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [.], ack 325, win 3804, length 0
22:13:06.749700 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [.], ack 342, win 3788, length 0
22:13:06.749748 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [.], ack 342, win 3788, length 0
22:13:06.749884 IP 10.64.0.1.pptp > 10.63.207.31.44466: Flags [R], seq 1544764963, win 3788, length 0
14 packets captured
14 packets received by filter
0 packets dropped by kernel

```

My unfiltered TCP dump:

```
22:09:15.294613 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:15.360817 ARP, Request who-has 10.63.204.1 tell 10.63.207.31, length 28
22:09:15.361704 ARP, Request who-has 94.253.143.245 tell 94.253.140.1, length 46
22:09:15.463682 ARP, Request who-has 94.253.160.128 tell 94.253.160.1, length 46
22:09:15.482534 ARP, Reply 10.63.204.1 is-at 00:21:a0:ce:8c:05 (oui Unknown), length 46
22:09:15.482541 IP 10.63.207.31.34036 > 83.139.64.10.domain: 9554+ PTR? 44.162.253.94.in-addr.arpa. (44)
22:09:15.490401 IP 83.139.64.10.domain > 10.63.207.31.34036: 9554*- 0/1/0 (97)
22:09:15.490519 IP 10.63.207.31.53604 > 83.139.64.10.domain: 21877+ PTR? 1.160.253.94.in-addr.arpa. (43)
22:09:15.519130 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:15.522316 IP 83.139.64.10.domain > 10.63.207.31.53604: 21877*- 0/1/0 (96)
22:09:15.522386 IP 10.63.207.31.34676 > 83.139.64.10.domain: 40075+ PTR? 1.204.63.10.in-addr.arpa. (42)
22:09:15.537027 IP 83.139.64.10.domain > 10.63.207.31.34676: 40075*- 0/1/0 (95)
22:09:15.537079 IP 10.63.207.31.40955 > 83.139.64.10.domain: 58523+ PTR? 31.207.63.10.in-addr.arpa. (43)
22:09:15.576240 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:15.584134 IP 83.139.64.10.domain > 10.63.207.31.40955: 58523*- 0/1/0 (96)
22:09:15.584193 IP 10.63.207.31.51715 > 83.139.64.10.domain: 62070+ PTR? 245.143.253.94.in-addr.arpa. (45)
22:09:15.596730 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:15.602373 IP 83.139.64.10.domain > 10.63.207.31.51715: 62070*- 0/1/0 (98)
22:09:15.602426 IP 10.63.207.31.56382 > 83.139.64.10.domain: 18300+ PTR? 1.140.253.94.in-addr.arpa. (43)
22:09:15.617020 ARP, Request who-has 94.253.136.129 tell 94.253.136.1, length 46
22:09:15.631504 IP 83.139.64.10.domain > 10.63.207.31.56382: 18300*- 0/1/0 (96)
22:09:15.631562 IP 10.63.207.31.36689 > 83.139.64.10.domain: 32694+ PTR? 128.160.253.94.in-addr.arpa. (45)
22:09:15.660176 IP 83.139.64.10.domain > 10.63.207.31.36689: 32694*- 0/1/0 (98)
22:09:15.661363 IP 10.63.207.31.41451 > 83.139.64.10.domain: 22165+ PTR? 10.64.139.83.in-addr.arpa. (43)
22:09:15.668710 ARP, Request who-has 94.253.142.235 tell 94.253.140.1, length 46
22:09:15.672420 IP 83.139.64.10.domain > 10.63.207.31.41451: 22165*- 0/1/0 (96)
22:09:15.672515 IP 10.63.207.31.53545 > 83.139.64.10.domain: 12393+ PTR? 138.137.253.94.in-addr.arpa. (45)
22:09:15.708475 IP 83.139.64.10.domain > 10.63.207.31.53545: 12393*- 0/1/0 (98)
22:09:15.708528 IP 10.63.207.31.39826 > 83.139.64.10.domain: 37614+ PTR? 1.136.253.94.in-addr.arpa. (43)
22:09:15.735869 IP 83.139.64.10.domain > 10.63.207.31.39826: 37614*- 0/1/0 (96)
22:09:15.735985 IP 10.63.207.31.43110 > 83.139.64.10.domain: 61482+ PTR? 23.162.253.94.in-addr.arpa. (44)
22:09:15.762636 IP 83.139.64.10.domain > 10.63.207.31.43110: 61482*- 0/1/0 (97)
22:09:15.762707 IP 10.63.207.31.42207 > 83.139.64.10.domain: 32672+ PTR? 146.163.253.94.in-addr.arpa. (45)
22:09:15.772568 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:15.790176 IP 83.139.64.10.domain > 10.63.207.31.42207: 32672*- 0/1/0 (98)
22:09:15.790253 IP 10.63.207.31.54638 > 83.139.64.10.domain: 33149+ PTR? 129.136.253.94.in-addr.arpa. (45)
22:09:15.808387 IP 83.139.64.10.domain > 10.63.207.31.54638: 33149*- 0/1/0 (98)
22:09:15.808477 IP 10.63.207.31.38835 > 83.139.64.10.domain: 36570+ PTR? 235.142.253.94.in-addr.arpa. (45)
22:09:15.826214 IP 83.139.64.10.domain > 10.63.207.31.38835: 36570*- 0/1/0 (98)
22:09:15.826319 IP 10.63.207.31.44415 > 83.139.64.10.domain: 44248+ PTR? 198.143.253.94.in-addr.arpa. (45)
22:09:15.873827 ARP, Request who-has 94.253.141.26 tell 94.253.140.1, length 46
22:09:15.874457 IP 83.139.64.10.domain > 10.63.207.31.44415: 44248*- 0/1/0 (98)
22:09:15.874554 IP 10.63.207.31.58490 > 83.139.64.10.domain: 49442+ PTR? 26.141.253.94.in-addr.arpa. (44)
22:09:15.882101 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:15.884551 ARP, Request who-has 94.253.161.21 tell 94.253.160.1, length 46
22:09:15.898338 IP 83.139.64.10.domain > 10.63.207.31.58490: 49442*- 0/1/0 (97)
22:09:15.898411 IP 10.63.207.31.36895 > 83.139.64.10.domain: 64071+ PTR? 177.138.253.94.in-addr.arpa. (45)
22:09:15.909840 IP 83.139.64.10.domain > 10.63.207.31.36895: 64071*- 0/1/0 (98)
22:09:15.909899 IP 10.63.207.31.54036 > 83.139.64.10.domain: 24277+ PTR? 21.161.253.94.in-addr.arpa. (44)
22:09:15.931756 IP 83.139.64.10.domain > 10.63.207.31.54036: 24277*- 0/1/0 (97)
22:09:15.962846 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:15.962902 IP 10.63.207.31.41894 > 83.139.64.10.domain: 17813+ PTR? 131.161.253.94.in-addr.arpa. (45)
22:09:15.975195 IP 83.139.64.10.domain > 10.63.207.31.41894: 17813*- 0/1/0 (98)
22:09:15.992545 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:15.992640 IP 10.63.207.31.58810 > 83.139.64.10.domain: 32475+ PTR? 189.142.253.94.in-addr.arpa. (45)
22:09:16.004851 IP 83.139.64.10.domain > 10.63.207.31.58810: 32475*- 0/1/0 (98)
22:09:16.048015 ARP, Request who-has 94.253.137.8 tell 94.253.136.1, length 46
22:09:16.048066 IP 10.63.207.31.44826 > 83.139.64.10.domain: 48996+ PTR? 8.137.253.94.in-addr.arpa. (43)
22:09:16.063647 IP 83.139.64.10.domain > 10.63.207.31.44826: 48996*- 0/1/0 (96)
22:09:16.159660 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:16.159743 IP 10.63.207.31.51590 > 83.139.64.10.domain: 8036+ PTR? 250.160.253.94.in-addr.arpa. (45)
22:09:16.171113 IP 83.139.64.10.domain > 10.63.207.31.51590: 8036*- 0/1/0 (98)
22:09:16.179753 ARP, Request who-has 94.253.138.217 tell 94.253.136.1, length 46
22:09:16.179803 IP 10.63.207.31.60748 > 83.139.64.10.domain: 17458+ PTR? 217.138.253.94.in-addr.arpa. (45)
22:09:16.182441 ARP, Request who-has 94.253.139.41 tell 94.253.136.1, length 46
22:09:16.201949 IP 83.139.64.10.domain > 10.63.207.31.60748: 17458*- 0/1/0 (98)
22:09:16.202015 IP 10.63.207.31.37250 > 83.139.64.10.domain: 2184+ PTR? 41.139.253.94.in-addr.arpa. (44)
22:09:16.260894 ARP, Request who-has 94.253.141.82 tell 94.253.140.1, length 46
22:09:16.264109 IP 83.139.64.10.domain > 10.63.207.31.37250: 2184*- 0/1/0 (97)
22:09:16.264181 IP 10.63.207.31.53051 > 83.139.64.10.domain: 23838+ PTR? 82.141.253.94.in-addr.arpa. (44)
22:09:16.275422 IP 83.139.64.10.domain > 10.63.207.31.53051: 23838*- 0/1/0 (97)
22:09:16.404285 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:16.404358 IP 10.63.207.31.53801 > 83.139.64.10.domain: 32028+ PTR? 50.160.253.94.in-addr.arpa. (44)
22:09:16.484996 IP 83.139.64.10.domain > 10.63.207.31.53801: 32028*- 0/1/0 (97)
22:09:16.512467 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:16.512522 IP 10.63.207.31.49710 > 83.139.64.10.domain: 64649+ PTR? 187.140.253.94.in-addr.arpa. (45)
22:09:16.541638 ARP, Request who-has 94.253.160.169 tell 94.253.160.1, length 46
22:09:16.542291 IP 83.139.64.10.domain > 10.63.207.31.49710: 64649*- 0/1/0 (98)
22:09:16.542359 IP 10.63.207.31.49772 > 83.139.64.10.domain: 25611+ PTR? 169.160.253.94.in-addr.arpa. (45)
22:09:16.553856 IP 83.139.64.10.domain > 10.63.207.31.49772: 25611*- 0/1/0 (98)
22:09:16.563811 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:16.563860 IP 10.63.207.31.40311 > 83.139.64.10.domain: 16368+ PTR? 206.143.253.94.in-addr.arpa. (45)
22:09:16.602243 IP 83.139.64.10.domain > 10.63.207.31.40311: 16368*- 0/1/0 (98)
22:09:16.678129 ARP, Request who-has 94.253.143.22 tell 94.253.140.1, length 46
22:09:16.678178 IP 10.63.207.31.39926 > 83.139.64.10.domain: 63797+ PTR? 22.143.253.94.in-addr.arpa. (44)
22:09:16.690038 IP 83.139.64.10.domain > 10.63.207.31.39926: 63797*- 0/1/0 (97)
22:09:16.754263 ARP, Request who-has 94.253.162.50 tell 94.253.160.1, length 46
22:09:16.754311 IP 10.63.207.31.50365 > 83.139.64.10.domain: 4076+ PTR? 50.162.253.94.in-addr.arpa. (44)
22:09:16.789285 IP 83.139.64.10.domain > 10.63.207.31.50365: 4076*- 0/1/0 (97)
22:09:16.820976 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:16.821023 IP 10.63.207.31.43895 > 83.139.64.10.domain: 56110+ PTR? 68.161.253.94.in-addr.arpa. (44)
22:09:16.829975 IP 83.139.64.10.domain > 10.63.207.31.43895: 56110*- 0/1/0 (97)
22:09:16.865399 ARP, Request who-has 94.253.143.64 tell 94.253.140.1, length 46
22:09:16.865448 IP 10.63.207.31.42239 > 83.139.64.10.domain: 57208+ PTR? 64.143.253.94.in-addr.arpa. (44)
22:09:16.887633 IP 83.139.64.10.domain > 10.63.207.31.42239: 57208*- 0/1/0 (97)
22:09:16.916561 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:16.916610 IP 10.63.207.31.50436 > 83.139.64.10.domain: 56993+ PTR? 154.161.253.94.in-addr.arpa. (45)
22:09:16.928105 IP 83.139.64.10.domain > 10.63.207.31.50436: 56993*- 0/1/0 (98)
22:09:17.093153 ARP, Request who-has 94.253.162.204 tell 94.253.160.1, length 46
22:09:17.093205 IP 10.63.207.31.35160 > 83.139.64.10.domain: 2302+ PTR? 204.162.253.94.in-addr.arpa. (45)
22:09:17.156228 IP 83.139.64.10.domain > 10.63.207.31.35160: 2302*- 0/1/0 (98)
22:09:17.163252 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:17.163350 IP 10.63.207.31.53058 > 83.139.64.10.domain: 37743+ PTR? 87.161.253.94.in-addr.arpa. (44)
22:09:17.176928 IP 83.139.64.10.domain > 10.63.207.31.53058: 37743*- 0/1/0 (97)
22:09:17.221122 ARP, Request who-has 94.253.162.102 tell 94.253.160.1, length 46
22:09:17.221175 IP 10.63.207.31.51019 > 83.139.64.10.domain: 52294+ PTR? 102.162.253.94.in-addr.arpa. (45)
22:09:17.283717 IP 83.139.64.10.domain > 10.63.207.31.51019: 52294*- 0/1/0 (98)
22:09:17.301382 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:17.536765 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:17.536833 IP 10.63.207.31.59834 > 83.139.64.10.domain: 55031+ PTR? 45.138.253.94.in-addr.arpa. (44)
22:09:17.543259 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:17.550604 IP 83.139.64.10.domain > 10.63.207.31.59834: 55031*- 0/1/0 (97)
22:09:17.550687 IP 10.63.207.31.43935 > 83.139.64.10.domain: 26655+ PTR? 75.140.253.94.in-addr.arpa. (44)
22:09:17.557478 IP 83.139.64.10.domain > 10.63.207.31.43935: 26655*- 0/1/0 (97)
22:09:17.578337 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:17.578387 IP 10.63.207.31.44784 > 83.139.64.10.domain: 38986+ PTR? 232.139.253.94.in-addr.arpa. (45)
22:09:17.585786 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:17.591995 ARP, Request who-has 94.253.143.14 tell 94.253.140.1, length 46
22:09:17.596555 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:17.623511 IP 83.139.64.10.domain > 10.63.207.31.44784: 38986*- 0/1/0 (98)
22:09:17.623577 IP 10.63.207.31.43836 > 83.139.64.10.domain: 11170+ PTR? 172.162.253.94.in-addr.arpa. (45)
22:09:17.633755 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:17.650217 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:17.655706 IP 83.139.64.10.domain > 10.63.207.31.43836: 11170*- 0/1/0 (98)
22:09:17.655771 IP 10.63.207.31.53364 > 83.139.64.10.domain: 30704+ PTR? 14.143.253.94.in-addr.arpa. (44)
22:09:17.668623 IP 83.139.64.10.domain > 10.63.207.31.53364: 30704*- 0/1/0 (97)
22:09:17.668698 IP 10.63.207.31.53774 > 83.139.64.10.domain: 4727+ PTR? 91.139.253.94.in-addr.arpa. (44)
22:09:17.733769 IP 83.139.64.10.domain > 10.63.207.31.53774: 4727*- 0/1/0 (97)
22:09:17.733827 IP 10.63.207.31.52049 > 83.139.64.10.domain: 22145+ PTR? 109.161.253.94.in-addr.arpa. (45)
22:09:17.754618 IP 83.139.64.10.domain > 10.63.207.31.52049: 22145*- 0/1/0 (98)
22:09:17.837252 ARP, Request who-has 94.253.161.73 tell 94.253.160.1, length 46
22:09:17.837302 IP 10.63.207.31.50318 > 83.139.64.10.domain: 60461+ PTR? 73.161.253.94.in-addr.arpa. (44)
22:09:17.851024 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:17.853218 IP 83.139.64.10.domain > 10.63.207.31.50318: 60461*- 0/1/0 (97)
22:09:17.853282 IP 10.63.207.31.40139 > 83.139.64.10.domain: 23110+ PTR? 125.161.253.94.in-addr.arpa. (45)
22:09:17.874753 IP 83.139.64.10.domain > 10.63.207.31.40139: 23110*- 0/1/0 (98)
22:09:17.923644 ARP, Request who-has 94.253.136.129 tell 94.253.136.1, length 46
22:09:17.970650 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:18.009295 ARP, Request who-has 94.253.162.62 tell 94.253.160.1, length 46
22:09:18.009382 IP 10.63.207.31.49529 > 83.139.64.10.domain: 22387+ PTR? 62.162.253.94.in-addr.arpa. (44)
22:09:18.017267 IP 83.139.64.10.domain > 10.63.207.31.49529: 22387*- 0/1/0 (97)
22:09:18.022014 ARP, Request who-has 94.253.163.244 tell 94.253.160.1, length 46
22:09:18.022062 IP 10.63.207.31.37362 > 83.139.64.10.domain: 22433+ PTR? 244.163.253.94.in-addr.arpa. (45)
22:09:18.064131 ARP, Request who-has 94.253.136.161 tell 94.253.136.1, length 46
22:09:18.065644 IP 83.139.64.10.domain > 10.63.207.31.37362: 22433*- 0/1/0 (98)
22:09:18.065709 IP 10.63.207.31.43218 > 83.139.64.10.domain: 26770+ PTR? 161.136.253.94.in-addr.arpa. (45)
22:09:18.068665 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:18.090257 ARP, Request who-has 94.253.138.111 tell 94.253.136.1, length 46
22:09:18.102193 IP 83.139.64.10.domain > 10.63.207.31.43218: 26770*- 0/1/0 (98)
22:09:18.102262 IP 10.63.207.31.50687 > 83.139.64.10.domain: 62182+ PTR? 61.163.253.94.in-addr.arpa. (44)
22:09:18.120244 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:18.129702 IP 83.139.64.10.domain > 10.63.207.31.50687: 62182*- 0/1/0 (97)
22:09:18.129760 IP 10.63.207.31.40868 > 83.139.64.10.domain: 48268+ PTR? 111.138.253.94.in-addr.arpa. (45)
22:09:18.139718 IP 83.139.64.10.domain > 10.63.207.31.40868: 48268*- 0/1/0 (98)
22:09:18.139890 IP 10.63.207.31.44350 > 83.139.64.10.domain: 37950+ PTR? 117.162.253.94.in-addr.arpa. (45)
22:09:18.150661 ARP, Request who-has 94.253.160.35 tell 94.253.160.1, length 46
22:09:18.160071 IP 83.139.64.10.domain > 10.63.207.31.44350: 37950*- 0/1/0 (98)
22:09:18.160183 IP 10.63.207.31.49362 > 83.139.64.10.domain: 53889+ PTR? 35.160.253.94.in-addr.arpa. (44)
22:09:18.170075 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:18.181399 IP 83.139.64.10.domain > 10.63.207.31.49362: 53889*- 0/1/0 (97)
22:09:18.185844 ARP, Request who-has 94.253.143.23 tell 94.253.140.1, length 46
22:09:18.185895 IP 10.63.207.31.38466 > 83.139.64.10.domain: 37956+ PTR? 23.143.253.94.in-addr.arpa. (44)
22:09:18.186625 ARP, Request who-has 94.253.140.129 tell 94.253.140.1, length 46
22:09:18.254441 IP 83.139.64.10.domain > 10.63.207.31.38466: 37956*- 0/1/0 (97)
22:09:18.254559 IP 10.63.207.31.37447 > 83.139.64.10.domain: 21105+ PTR? 129.140.253.94.in-addr.arpa. (45)
22:09:18.278021 IP 83.139.64.10.domain > 10.63.207.31.37447: 21105*- 0/1/0 (98)
22:09:18.372549 ARP, Request who-has 94.253.143.245 tell 94.253.140.1, length 46
22:09:18.410272 ARP, Request who-has 94.253.137.8 tell 94.253.136.1, length 46
22:09:18.424348 ARP, Request who-has 94.253.140.98 tell 94.253.140.1, length 46
22:09:18.424460 IP 10.63.207.31.41382 > 83.139.64.10.domain: 60390+ PTR? 98.140.253.94.in-addr.arpa. (44)
22:09:18.453322 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [S], seq 665225246, win 5840, options [mss 1460,sackOK,TS val 4294906859 ecr 0,nop,wscale 6], length 0
22:09:18.475857 IP 83.139.64.10.domain > 10.63.207.31.41382: 60390*- 0/1/0 (97)
22:09:18.475981 IP 10.63.207.31.51571 > 83.139.64.10.domain: 56653+ PTR? 1.0.64.10.in-addr.arpa. (40)
22:09:18.482247 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [S.], seq 2098537830, ack 665225247, win 4128, options [mss 536], length 0
22:09:18.482265 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [.], ack 1, win 5840, length 0
22:09:18.482567 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [P.], seq 1:157, ack 1, win 5840, length 156: pptp CTRL_MSGTYPE=SCCRQ PROTO_VER(1.0) FRAME_CAP(AS) BEARER_CAP(DA) MAX_CHAN(65535) FIRM_REV(1) HOSTNAME(local) VENDOR(cananian)
22:09:18.488977 IP 83.139.64.10.domain > 10.63.207.31.51571: 56653*- 0/1/0 (93)
22:09:18.496514 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [P.], seq 1:157, ack 157, win 3972, length 156: pptp CTRL_MSGTYPE=SCCRP PROTO_VER(1.0) RESULT_CODE(1) ERR_CODE(0) FRAME_CAP(AS) BEARER_CAP(DA) MAX_CHAN(0) FIRM_REV(4608) HOSTNAME(CN-XCARNet-03-RO) VENDOR(Cisco Systems, Inc.)
22:09:18.496526 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [.], ack 157, win 6432, length 0
22:09:18.703828 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:18.703926 IP 10.63.207.31.59930 > 83.139.64.10.domain: 9281+ PTR? 95.142.253.94.in-addr.arpa. (44)
22:09:18.713035 IP 83.139.64.10.domain > 10.63.207.31.59930: 9281*- 0/1/0 (97)
22:09:18.822791 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:18.826579 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:18.826629 IP 10.63.207.31.43657 > 83.139.64.10.domain: 32331+ PTR? 150.160.253.94.in-addr.arpa. (45)
22:09:18.858658 ARP, Request who-has 94.253.138.106 tell 94.253.136.1, length 46
22:09:18.861201 IP 83.139.64.10.domain > 10.63.207.31.43657: 32331*- 0/1/0 (98)
22:09:18.861268 IP 10.63.207.31.56464 > 83.139.64.10.domain: 47311+ PTR? 106.138.253.94.in-addr.arpa. (45)
22:09:18.882894 IP 83.139.64.10.domain > 10.63.207.31.56464: 47311*- 0/1/0 (98)
22:09:18.911838 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:18.939956 ARP, Request who-has 94.253.160.239 tell 94.253.160.1, length 46
22:09:18.940004 IP 10.63.207.31.38458 > 83.139.64.10.domain: 11986+ PTR? 239.160.253.94.in-addr.arpa. (45)
22:09:18.952238 IP 83.139.64.10.domain > 10.63.207.31.38458: 11986*- 0/1/0 (98)
22:09:18.961231 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:18.961279 IP 10.63.207.31.44470 > 83.139.64.10.domain: 49961+ PTR? 3.141.253.94.in-addr.arpa. (43)
22:09:18.975287 IP 83.139.64.10.domain > 10.63.207.31.44470: 49961*- 0/1/0 (96)
22:09:19.081446 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:19.081495 IP 10.63.207.31.54643 > 83.139.64.10.domain: 26008+ PTR? 44.138.253.94.in-addr.arpa. (44)
22:09:19.091794 ARP, Request who-has 94.253.162.204 tell 94.253.160.1, length 46
22:09:19.131140 IP 83.139.64.10.domain > 10.63.207.31.54643: 26008*- 0/1/0 (97)
22:09:19.254795 ARP, Request who-has 94.253.162.200 tell 94.253.160.1, length 46
22:09:19.254848 IP 10.63.207.31.53945 > 83.139.64.10.domain: 4462+ PTR? 200.162.253.94.in-addr.arpa. (45)
22:09:19.280471 IP 83.139.64.10.domain > 10.63.207.31.53945: 4462*- 0/1/0 (98)
22:09:19.291658 ARP, Request who-has 94.253.160.166 tell 94.253.160.1, length 46
22:09:19.291706 IP 10.63.207.31.37656 > 83.139.64.10.domain: 43535+ PTR? 166.160.253.94.in-addr.arpa. (45)
22:09:19.304014 IP 83.139.64.10.domain > 10.63.207.31.37656: 43535*- 0/1/0 (98)
22:09:19.329131 ARP, Request who-has 94.253.139.233 tell 94.253.136.1, length 46
22:09:19.329179 IP 10.63.207.31.57107 > 83.139.64.10.domain: 20490+ PTR? 233.139.253.94.in-addr.arpa. (45)
22:09:19.349970 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:19.358046 IP 83.139.64.10.domain > 10.63.207.31.57107: 20490*- 0/1/0 (98)
22:09:19.482761 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [P.], seq 157:325, ack 157, win 6432, length 168: pptp CTRL_MSGTYPE=OCRQ CALL_ID(0) CALL_SER_NUM(0) MIN_BPS(2400) MAX_BPS(10000000) BEARER_TYPE(Any) FRAME_TYPE(E) RECV_WIN(3) PROC_DELAY(0) PHONE_NO_LEN(0) PHONE_NO() SUB_ADDR()
22:09:19.491575 ARP, Request who-has 94.253.139.163 tell 94.253.136.1, length 46
22:09:19.491655 IP 10.63.207.31.60033 > 83.139.64.10.domain: 50370+ PTR? 163.139.253.94.in-addr.arpa. (45)
22:09:19.493012 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [.], ack 325, win 3804, length 0
22:09:19.512159 ARP, Request who-has 94.253.162.216 tell 94.253.160.1, length 46
22:09:19.515003 IP 83.139.64.10.domain > 10.63.207.31.60033: 50370*- 0/1/0 (98)
22:09:19.515088 IP 10.63.207.31.38719 > 83.139.64.10.domain: 4617+ PTR? 216.162.253.94.in-addr.arpa. (45)
22:09:19.550480 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:19.558046 IP 83.139.64.10.domain > 10.63.207.31.38719: 4617*- 0/1/0 (98)
22:09:19.660545 ARP, Request who-has 94.253.143.8 tell 94.253.140.1, length 46
22:09:19.660596 IP 10.63.207.31.58996 > 83.139.64.10.domain: 41986+ PTR? 8.143.253.94.in-addr.arpa. (43)
22:09:19.661957 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:19.685446 ARP, Request who-has 94.253.143.22 tell 94.253.140.1, length 46
22:09:19.692702 IP 83.139.64.10.domain > 10.63.207.31.58996: 41986*- 0/1/0 (96)
22:09:19.759349 ARP, Request who-has 94.253.162.50 tell 94.253.160.1, length 46
22:09:19.760012 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:19.882011 ARP, Request who-has 94.253.141.26 tell 94.253.140.1, length 46
22:09:19.937172 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:19.953675 ARP, Request who-has 94.253.160.128 tell 94.253.160.1, length 46
22:09:19.954128 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:19.976476 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:20.040151 ARP, Request who-has 94.253.162.249 tell 94.253.160.1, length 46
22:09:20.040203 IP 10.63.207.31.39453 > 83.139.64.10.domain: 20734+ PTR? 249.162.253.94.in-addr.arpa. (45)
22:09:20.076638 IP 83.139.64.10.domain > 10.63.207.31.39453: 20734*- 0/1/0 (98)
22:09:20.103438 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:20.103487 IP 10.63.207.31.36873 > 83.139.64.10.domain: 42244+ PTR? 133.140.253.94.in-addr.arpa. (45)
22:09:20.113836 IP 83.139.64.10.domain > 10.63.207.31.36873: 42244*- 0/1/0 (98)
22:09:20.252958 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:20.378030 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:20.402273 ARP, Request who-has 94.253.161.174 tell 94.253.160.1, length 46
22:09:20.402354 IP 10.63.207.31.51153 > 83.139.64.10.domain: 45295+ PTR? 174.161.253.94.in-addr.arpa. (45)
22:09:20.411244 IP 83.139.64.10.domain > 10.63.207.31.51153: 45295*- 0/1/0 (98)
22:09:20.474589 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:20.524463 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:20.553070 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:20.795597 ARP, Request who-has 94.253.143.23 tell 94.253.140.1, length 46
22:09:20.858997 ARP, Request who-has 94.253.138.106 tell 94.253.136.1, length 46
22:09:20.871209 ARP, Request who-has 94.253.138.143 tell 94.253.136.1, length 46
22:09:20.871261 IP 10.63.207.31.51593 > 83.139.64.10.domain: 54861+ PTR? 143.138.253.94.in-addr.arpa. (45)
22:09:20.873724 ARP, Request who-has 94.253.137.233 tell 94.253.136.1, length 46
22:09:20.874270 ARP, Request who-has 94.253.163.129 tell 94.253.160.1, length 46
22:09:20.874451 ARP, Request who-has 94.253.161.21 tell 94.253.160.1, length 46
22:09:20.884923 ARP, Request who-has 94.253.138.8 tell 94.253.136.1, length 46
22:09:20.911453 IP 83.139.64.10.domain > 10.63.207.31.51593: 54861*- 0/1/0 (98)
22:09:20.911532 IP 10.63.207.31.34970 > 83.139.64.10.domain: 60855+ PTR? 233.137.253.94.in-addr.arpa. (45)
22:09:20.958410 ARP, Request who-has 94.253.137.159 tell 94.253.136.1, length 46
22:09:20.964483 IP 83.139.64.10.domain > 10.63.207.31.34970: 60855*- 0/1/0 (98)
22:09:20.964543 IP 10.63.207.31.58120 > 83.139.64.10.domain: 55829+ PTR? 129.163.253.94.in-addr.arpa. (45)
22:09:21.008732 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:21.013608 IP 83.139.64.10.domain > 10.63.207.31.58120: 55829*- 0/1/0 (98)
22:09:21.013669 IP 10.63.207.31.41696 > 83.139.64.10.domain: 27491+ PTR? 8.138.253.94.in-addr.arpa. (43)
22:09:21.026635 IP 83.139.64.10.domain > 10.63.207.31.41696: 27491*- 0/1/0 (96)
22:09:21.026705 IP 10.63.207.31.43394 > 83.139.64.10.domain: 56908+ PTR? 159.137.253.94.in-addr.arpa. (45)
22:09:21.035580 IP 83.139.64.10.domain > 10.63.207.31.43394: 56908*- 0/1/0 (98)
22:09:21.035651 IP 10.63.207.31.46789 > 83.139.64.10.domain: 26796+ PTR? 224.141.253.94.in-addr.arpa. (45)
22:09:21.054127 IP 83.139.64.10.domain > 10.63.207.31.46789: 26796*- 0/1/0 (98)
22:09:21.060713 ARP, Request who-has 94.253.142.191 tell 94.253.140.1, length 46
22:09:21.060759 IP 10.63.207.31.39987 > 83.139.64.10.domain: 8036+ PTR? 191.142.253.94.in-addr.arpa. (45)
22:09:21.069943 IP 83.139.64.10.domain > 10.63.207.31.39987: 8036*- 0/1/0 (98)
22:09:21.073631 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:21.157979 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:21.184251 ARP, Request who-has 94.253.136.221 tell 94.253.136.1, length 46
22:09:21.184339 IP 10.63.207.31.47394 > 83.139.64.10.domain: 19352+ PTR? 221.136.253.94.in-addr.arpa. (45)
22:09:21.199930 IP 83.139.64.10.domain > 10.63.207.31.47394: 19352*- 0/1/0 (98)
22:09:21.252713 ARP, Request who-has 94.253.162.62 tell 94.253.160.1, length 46
22:09:21.285598 ARP, Request who-has 94.253.143.31 tell 94.253.140.1, length 46
22:09:21.285646 IP 10.63.207.31.53445 > 83.139.64.10.domain: 11878+ PTR? 31.143.253.94.in-addr.arpa. (44)
22:09:21.297328 IP 83.139.64.10.domain > 10.63.207.31.53445: 11878*- 0/1/0 (97)
22:09:21.299088 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:21.315389 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:21.389733 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:21.461299 ARP, Request who-has 94.253.143.9 tell 94.253.140.1, length 46
22:09:21.461358 IP 10.63.207.31.40304 > 83.139.64.10.domain: 12473+ PTR? 9.143.253.94.in-addr.arpa. (43)
22:09:21.494390 IP 83.139.64.10.domain > 10.63.207.31.40304: 12473*- 0/1/0 (96)
22:09:21.662029 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:21.675112 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:21.688546 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:21.688598 IP 10.63.207.31.52685 > 83.139.64.10.domain: 13200+ PTR? 169.137.253.94.in-addr.arpa. (45)
22:09:21.702363 IP 83.139.64.10.domain > 10.63.207.31.52685: 13200*- 0/1/0 (98)
22:09:21.729741 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:21.762884 ARP, Request who-has 94.253.139.111 tell 94.253.136.1, length 46
22:09:21.762932 IP 10.63.207.31.49636 > 83.139.64.10.domain: 44277+ PTR? 111.139.253.94.in-addr.arpa. (45)
22:09:21.773013 IP 83.139.64.10.domain > 10.63.207.31.49636: 44277*- 0/1/0 (98)
22:09:21.815698 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:21.885214 ARP, Request who-has 94.253.143.8 tell 94.253.140.1, length 46
22:09:21.909899 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:21.909949 IP 10.63.207.31.57069 > 83.139.64.10.domain: 61594+ PTR? 20.162.253.94.in-addr.arpa. (44)
22:09:21.926630 ARP, Request who-has 94.253.162.255 tell 94.253.160.1, length 46
22:09:21.937143 IP 83.139.64.10.domain > 10.63.207.31.57069: 61594*- 0/1/0 (97)
22:09:21.937209 IP 10.63.207.31.57053 > 83.139.64.10.domain: 34661+ PTR? 255.162.253.94.in-addr.arpa. (45)
22:09:21.986796 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:21.988940 IP 83.139.64.10.domain > 10.63.207.31.57053: 34661*- 0/1/0 (98)
22:09:22.054162 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:22.305110 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:22.309958 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:22.444606 ARP, Request who-has 94.253.143.158 tell 94.253.140.1, length 46
22:09:22.444694 IP 10.63.207.31.52234 > 83.139.64.10.domain: 35688+ PTR? 158.143.253.94.in-addr.arpa. (45)
22:09:22.457783 IP 83.139.64.10.domain > 10.63.207.31.52234: 35688*- 0/1/0 (98)
22:09:22.607787 ARP, Request who-has 94.253.139.233 tell 94.253.136.1, length 46
22:09:22.622454 ARP, Request who-has 94.253.139.83 tell 94.253.136.1, length 46
22:09:22.622504 IP 10.63.207.31.43255 > 83.139.64.10.domain: 38649+ PTR? 83.139.253.94.in-addr.arpa. (44)
22:09:22.640747 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:22.654436 IP 83.139.64.10.domain > 10.63.207.31.43255: 38649*- 0/1/0 (97)
22:09:22.888904 ARP, Request who-has 94.253.139.61 tell 94.253.136.1, length 46
22:09:22.888958 IP 10.63.207.31.42873 > 83.139.64.10.domain: 63188+ PTR? 61.139.253.94.in-addr.arpa. (44)
22:09:22.918946 ARP, Request who-has 94.253.163.244 tell 94.253.160.1, length 46
22:09:22.922435 IP 83.139.64.10.domain > 10.63.207.31.42873: 63188*- 0/1/0 (97)
22:09:23.097265 ARP, Request who-has 94.253.162.204 tell 94.253.160.1, length 46
22:09:23.115125 ARP, Request who-has 94.253.139.38 tell 94.253.136.1, length 46
22:09:23.115174 IP 10.63.207.31.51410 > 83.139.64.10.domain: 46545+ PTR? 38.139.253.94.in-addr.arpa. (44)
22:09:23.126645 IP 83.139.64.10.domain > 10.63.207.31.51410: 46545*- 0/1/0 (97)
22:09:23.156575 ARP, Request who-has 94.253.160.35 tell 94.253.160.1, length 46
22:09:23.211229 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:23.211282 IP 10.63.207.31.56176 > 83.139.64.10.domain: 64863+ PTR? 78.143.253.94.in-addr.arpa. (44)
22:09:23.214597 ARP, Request who-has 94.253.163.85 tell 94.253.160.1, length 46
22:09:23.269709 IP 83.139.64.10.domain > 10.63.207.31.56176: 64863*- 0/1/0 (97)
22:09:23.269777 IP 10.63.207.31.37000 > 83.139.64.10.domain: 38760+ PTR? 85.163.253.94.in-addr.arpa. (44)
22:09:23.281669 IP 83.139.64.10.domain > 10.63.207.31.37000: 38760*- 0/1/0 (97)
22:09:23.600734 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:23.721920 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:23.747542 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:23.837745 ARP, Request who-has 94.253.163.129 tell 94.253.160.1, length 46
22:09:23.911670 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:23.974366 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:23.976567 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:24.059436 ARP, Request who-has 94.253.142.191 tell 94.253.140.1, length 46
22:09:24.065947 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:24.084613 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:24.242527 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:24.330854 ARP, Request who-has 94.253.162.255 tell 94.253.160.1, length 46
22:09:24.376531 ARP, Request who-has 94.253.143.245 tell 94.253.140.1, length 46
22:09:24.452657 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:24.468076 ARP, Request who-has 94.253.141.81 tell 94.253.140.1, length 46
22:09:24.468140 IP 10.63.207.31.60218 > 83.139.64.10.domain: 34233+ PTR? 81.141.253.94.in-addr.arpa. (44)
22:09:24.473654 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:24.487360 IP 83.139.64.10.domain > 10.63.207.31.60218: 34233*- 0/1/0 (97)
22:09:24.487434 IP 10.63.207.31.60110 > 83.139.64.10.domain: 46916+ PTR? 148.136.253.94.in-addr.arpa. (45)
22:09:24.498229 IP 83.139.64.10.domain > 10.63.207.31.60110: 46916*- 0/1/0 (98)
22:09:24.508458 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:24.622732 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:24.734273 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:24.833168 ARP, Request who-has 94.253.143.8 tell 94.253.140.1, length 46
22:09:24.857522 ARP, Request who-has 94.253.138.106 tell 94.253.136.1, length 46
22:09:24.882190 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:25.029191 ARP, Request who-has 94.253.143.109 tell 94.253.140.1, length 46
22:09:25.029245 IP 10.63.207.31.56836 > 83.139.64.10.domain: 49951+ PTR? 109.143.253.94.in-addr.arpa. (45)
22:09:25.036975 IP 83.139.64.10.domain > 10.63.207.31.56836: 49951*- 0/1/0 (98)
22:09:25.073075 ARP, Request who-has 94.253.143.215 tell 94.253.140.1, length 46
22:09:25.073125 IP 10.63.207.31.51390 > 83.139.64.10.domain: 14189+ PTR? 215.143.253.94.in-addr.arpa. (45)
22:09:25.074245 ARP, Request who-has 94.253.162.200 tell 94.253.160.1, length 46
22:09:25.084216 IP 83.139.64.10.domain > 10.63.207.31.51390: 14189*- 0/1/0 (98)
22:09:25.138101 ARP, Request who-has 94.253.138.222 tell 94.253.136.1, length 46
22:09:25.138151 IP 10.63.207.31.51920 > 83.139.64.10.domain: 1325+ PTR? 222.138.253.94.in-addr.arpa. (45)
22:09:25.148584 IP 83.139.64.10.domain > 10.63.207.31.51920: 1325*- 0/1/0 (98)
22:09:25.189609 ARP, Request who-has 94.253.160.20 tell 94.253.160.1, length 46
22:09:25.189661 IP 10.63.207.31.35190 > 83.139.64.10.domain: 50998+ PTR? 20.160.253.94.in-addr.arpa. (44)
22:09:25.216614 IP 83.139.64.10.domain > 10.63.207.31.35190: 50998*- 0/1/0 (97)
22:09:25.280894 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:25.309795 ARP, Request who-has 94.253.143.9 tell 94.253.140.1, length 46
22:09:25.450895 ARP, Request who-has 94.253.143.158 tell 94.253.140.1, length 46
22:09:25.488855 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:25.527571 ARP, Request who-has 94.253.160.169 tell 94.253.160.1, length 46
22:09:25.701661 ARP, Request who-has 94.253.161.174 tell 94.253.160.1, length 46
22:09:25.724261 ARP, Request who-has 94.253.139.47 tell 94.253.136.1, length 46
22:09:25.724337 IP 10.63.207.31.35261 > 83.139.64.10.domain: 4142+ PTR? 47.139.253.94.in-addr.arpa. (44)
22:09:25.733308 IP 83.139.64.10.domain > 10.63.207.31.35261: 4142*- 0/1/0 (97)
22:09:25.872984 ARP, Request who-has 94.253.137.233 tell 94.253.136.1, length 46
22:09:25.974139 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:25.992495 ARP, Request who-has 94.253.138.143 tell 94.253.136.1, length 46
22:09:26.039908 ARP, Request who-has 94.253.140.241 tell 94.253.140.1, length 46
22:09:26.039958 IP 10.63.207.31.32869 > 83.139.64.10.domain: 54984+ PTR? 241.140.253.94.in-addr.arpa. (45)
22:09:26.102324 IP 83.139.64.10.domain > 10.63.207.31.32869: 54984*- 0/1/0 (98)
22:09:26.112640 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:26.169104 ARP, Request who-has 94.253.142.83 tell 94.253.140.1, length 46
22:09:26.169174 IP 10.63.207.31.58197 > 83.139.64.10.domain: 41725+ PTR? 83.142.253.94.in-addr.arpa. (44)
22:09:26.178086 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:26.189180 IP 83.139.64.10.domain > 10.63.207.31.58197: 41725*- 0/1/0 (97)
22:09:26.220659 ARP, Request who-has 94.253.160.128 tell 94.253.160.1, length 46
22:09:26.323137 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:26.549300 ARP, Request who-has 94.253.137.8 tell 94.253.136.1, length 46
22:09:26.554789 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:26.560281 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:26.661150 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:26.698973 ARP, Request who-has 94.253.140.98 tell 94.253.140.1, length 46
22:09:26.879116 ARP, Request who-has 94.253.161.252 tell 94.253.160.1, length 46
22:09:26.879179 IP 10.63.207.31.47127 > 83.139.64.10.domain: 1140+ PTR? 252.161.253.94.in-addr.arpa. (45)
22:09:26.892140 IP 83.139.64.10.domain > 10.63.207.31.47127: 1140*- 0/1/0 (98)
22:09:26.956581 ARP, Request who-has 94.253.143.172 tell 94.253.140.1, length 46
22:09:26.956633 IP 10.63.207.31.44775 > 83.139.64.10.domain: 41867+ PTR? 172.143.253.94.in-addr.arpa. (45)
22:09:26.976700 IP 83.139.64.10.domain > 10.63.207.31.44775: 41867*- 0/1/0 (98)
22:09:27.070112 ARP, Request who-has 94.253.143.64 tell 94.253.140.1, length 46
22:09:27.140767 ARP, Request who-has 94.253.162.62 tell 94.253.160.1, length 46
22:09:27.222001 ARP, Request who-has 94.253.137.17 tell 94.253.136.1, length 46
22:09:27.222054 IP 10.63.207.31.39921 > 83.139.64.10.domain: 21536+ PTR? 17.137.253.94.in-addr.arpa. (44)
22:09:27.249575 ARP, Request who-has 94.253.162.206 tell 94.253.160.1, length 46
22:09:27.255669 IP 83.139.64.10.domain > 10.63.207.31.39921: 21536*- 0/1/0 (97)
22:09:27.255737 IP 10.63.207.31.58562 > 83.139.64.10.domain: 30623+ PTR? 206.162.253.94.in-addr.arpa. (45)
22:09:27.259364 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:27.263275 ARP, Request who-has 94.253.139.157 tell 94.253.136.1, length 46
22:09:27.297984 IP 83.139.64.10.domain > 10.63.207.31.58562: 30623*- 0/1/0 (98)
22:09:27.298058 IP 10.63.207.31.49209 > 83.139.64.10.domain: 4470+ PTR? 157.139.253.94.in-addr.arpa. (45)
22:09:27.331464 IP 83.139.64.10.domain > 10.63.207.31.49209: 4470*- 0/1/0 (98)
22:09:27.550079 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:27.560365 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:27.567036 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:27.582698 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:27.603130 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:27.627122 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:27.649808 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:27.723757 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:27.723763 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:27.723827 IP 10.63.207.31.39055 > 83.139.64.10.domain: 21182+ PTR? 182.139.253.94.in-addr.arpa. (45)
22:09:27.748549 IP 83.139.64.10.domain > 10.63.207.31.39055: 21182*- 0/1/0 (98)
22:09:27.777054 ARP, Request who-has 83.139.66.166 tell 83.139.66.165, length 46
22:09:27.777104 IP 10.63.207.31.38675 > 83.139.64.10.domain: 29092+ PTR? 166.66.139.83.in-addr.arpa. (44)
22:09:27.787323 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:27.804214 IP 83.139.64.10.domain > 10.63.207.31.38675: 29092*- 0/1/0 (97)
22:09:27.804269 IP 10.63.207.31.44416 > 83.139.64.10.domain: 27565+ PTR? 165.66.139.83.in-addr.arpa. (44)
22:09:27.818951 IP 83.139.64.10.domain > 10.63.207.31.44416: 27565*- 0/1/0 (97)
22:09:27.836669 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:28.012422 ARP, Request who-has 94.253.136.126 tell 94.253.136.1, length 46
22:09:28.012471 IP 10.63.207.31.41202 > 83.139.64.10.domain: 44451+ PTR? 126.136.253.94.in-addr.arpa. (45)
22:09:28.018174 ARP, Request who-has 94.253.160.146 tell 94.253.160.1, length 46
22:09:28.021534 IP 83.139.64.10.domain > 10.63.207.31.41202: 44451*- 0/1/0 (98)
22:09:28.021598 IP 10.63.207.31.42309 > 83.139.64.10.domain: 31322+ PTR? 146.160.253.94.in-addr.arpa. (45)
22:09:28.048833 IP 83.139.64.10.domain > 10.63.207.31.42309: 31322*- 0/1/0 (98)
22:09:28.077453 ARP, Request who-has 94.253.143.215 tell 94.253.140.1, length 46
22:09:28.103574 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:28.121983 ARP, Request who-has 94.253.162.255 tell 94.253.160.1, length 46
22:09:28.156620 ARP, Request who-has 94.253.163.90 tell 94.253.160.1, length 46
22:09:28.156669 IP 10.63.207.31.40734 > 83.139.64.10.domain: 15481+ PTR? 90.163.253.94.in-addr.arpa. (44)
22:09:28.157081 ARP, Request who-has 94.253.139.214 tell 94.253.136.1, length 46
22:09:28.167839 ARP, Request who-has 94.253.160.14 tell 94.253.160.1, length 46
22:09:28.181488 IP 83.139.64.10.domain > 10.63.207.31.40734: 15481*- 0/1/0 (97)
22:09:28.181558 IP 10.63.207.31.38549 > 83.139.64.10.domain: 48192+ PTR? 214.139.253.94.in-addr.arpa. (45)
22:09:28.187480 IP 83.139.64.10.domain > 10.63.207.31.38549: 48192*- 0/1/0 (98)
22:09:28.187534 IP 10.63.207.31.40545 > 83.139.64.10.domain: 19229+ PTR? 14.160.253.94.in-addr.arpa. (44)
22:09:28.196350 IP 83.139.64.10.domain > 10.63.207.31.40545: 19229*- 0/1/0 (97)
22:09:28.251642 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:28.328056 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:28.344258 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:28.647897 ARP, Request who-has 94.253.139.163 tell 94.253.136.1, length 46
22:09:28.697479 ARP, Request who-has 94.253.161.174 tell 94.253.160.1, length 46
22:09:28.786498 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:28.805461 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:28.817557 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:28.867684 ARP, Request who-has 94.253.142.203 tell 94.253.140.1, length 46
22:09:28.867754 IP 10.63.207.31.51623 > 83.139.64.10.domain: 9380+ PTR? 203.142.253.94.in-addr.arpa. (45)
22:09:28.880266 IP 83.139.64.10.domain > 10.63.207.31.51623: 9380*- 0/1/0 (98)
22:09:28.941893 ARP, Request who-has 94.253.161.86 tell 94.253.160.1, length 46
22:09:28.941943 IP 10.63.207.31.57767 > 83.139.64.10.domain: 5721+ PTR? 86.161.253.94.in-addr.arpa. (44)
22:09:28.959768 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:28.975138 IP 83.139.64.10.domain > 10.63.207.31.57767: 5721*- 0/1/0 (97)
22:09:29.059179 ARP, Request who-has 94.253.141.82 tell 94.253.140.1, length 46
22:09:29.255518 ARP, Request who-has 94.253.162.232 tell 94.253.160.1, length 46
22:09:29.255571 IP 10.63.207.31.43630 > 83.139.64.10.domain: 49818+ PTR? 232.162.253.94.in-addr.arpa. (45)
22:09:29.273488 ARP, Request who-has 94.253.142.13 tell 94.253.140.1, length 46
22:09:29.292650 IP 83.139.64.10.domain > 10.63.207.31.43630: 49818*- 0/1/0 (98)
22:09:29.292719 IP 10.63.207.31.40417 > 83.139.64.10.domain: 34339+ PTR? 13.142.253.94.in-addr.arpa. (44)
22:09:29.308465 IP 83.139.64.10.domain > 10.63.207.31.40417: 34339*- 0/1/0 (97)
22:09:29.366619 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:29.421325 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:29.426753 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:29.455238 ARP, Request who-has 94.253.140.98 tell 94.253.140.1, length 46
22:09:29.610036 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:29.636866 ARP, Request who-has 94.253.142.223 tell 94.253.140.1, length 46
22:09:29.636925 IP 10.63.207.31.34286 > 83.139.64.10.domain: 319+ PTR? 223.142.253.94.in-addr.arpa. (45)
22:09:29.669206 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:29.672811 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:29.691043 IP 83.139.64.10.domain > 10.63.207.31.34286: 319*- 0/1/0 (98)
22:09:29.786911 ARP, Request who-has 94.253.160.166 tell 94.253.160.1, length 46
22:09:29.843957 ARP, Request who-has 94.253.163.129 tell 94.253.160.1, length 46
22:09:29.849682 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:29.927756 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:29.984225 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:30.002361 ARP, Request who-has 94.253.139.73 tell 94.253.136.1, length 46
22:09:30.002414 IP 10.63.207.31.52288 > 83.139.64.10.domain: 61265+ PTR? 73.139.253.94.in-addr.arpa. (44)
22:09:30.012369 IP 83.139.64.10.domain > 10.63.207.31.52288: 61265*- 0/1/0 (97)
22:09:30.012741 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:30.056717 ARP, Request who-has 94.253.142.191 tell 94.253.140.1, length 46
22:09:30.112050 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:30.170004 ARP, Request who-has 94.253.163.92 tell 94.253.160.1, length 46
22:09:30.170057 IP 10.63.207.31.51517 > 83.139.64.10.domain: 11998+ PTR? 92.163.253.94.in-addr.arpa. (44)
22:09:30.182521 IP 83.139.64.10.domain > 10.63.207.31.51517: 11998*- 0/1/0 (97)
22:09:30.252404 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:30.252762 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:30.439496 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:30.457363 ARP, Request who-has 94.253.138.26 tell 94.253.136.1, length 46
22:09:30.457424 IP 10.63.207.31.48021 > 83.139.64.10.domain: 23294+ PTR? 26.138.253.94.in-addr.arpa. (44)
22:09:30.484342 IP 83.139.64.10.domain > 10.63.207.31.48021: 23294*- 0/1/0 (97)
22:09:30.512150 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:30.652191 ARP, Request who-has 83.139.66.166 tell 83.139.66.165, length 46
22:09:30.869036 ARP, Request who-has 94.253.143.8 tell 94.253.140.1, length 46
22:09:30.882596 ARP, Request who-has 94.253.137.190 tell 94.253.136.1, length 46
22:09:30.882649 IP 10.63.207.31.46581 > 83.139.64.10.domain: 65043+ PTR? 190.137.253.94.in-addr.arpa. (45)
22:09:30.893898 IP 83.139.64.10.domain > 10.63.207.31.46581: 65043*- 0/1/0 (98)
22:09:30.922626 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:30.974402 ARP, Request who-has 94.253.136.126 tell 94.253.136.1, length 46
22:09:31.002299 ARP, Request who-has 94.253.143.9 tell 94.253.140.1, length 46
22:09:31.157800 ARP, Request who-has 94.253.160.14 tell 94.253.160.1, length 46
22:09:31.167787 ARP, Request who-has 94.253.163.93 tell 94.253.160.1, length 46
22:09:31.167838 IP 10.63.207.31.55905 > 83.139.64.10.domain: 21361+ PTR? 93.163.253.94.in-addr.arpa. (44)
22:09:31.178334 IP 83.139.64.10.domain > 10.63.207.31.55905: 21361*- 0/1/0 (97)
22:09:31.277748 ARP, Request who-has 94.253.137.74 tell 94.253.136.1, length 46
22:09:31.277800 IP 10.63.207.31.48716 > 83.139.64.10.domain: 17521+ PTR? 74.137.253.94.in-addr.arpa. (44)
22:09:31.323999 IP 83.139.64.10.domain > 10.63.207.31.48716: 17521*- 0/1/0 (97)
22:09:31.394081 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:31.453868 ARP, Request who-has 94.253.143.158 tell 94.253.140.1, length 46
22:09:31.618460 ARP, Request who-has 94.253.141.167 tell 94.253.140.1, length 46
22:09:31.618530 IP 10.63.207.31.34226 > 83.139.64.10.domain: 836+ PTR? 167.141.253.94.in-addr.arpa. (45)
22:09:31.662934 IP 83.139.64.10.domain > 10.63.207.31.34226: 836*- 0/1/0 (98)
22:09:31.794760 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:31.866875 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:31.953390 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:31.979798 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:32.064931 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:32.112177 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:32.123159 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:32.158478 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:32.322871 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:32.329556 ARP, Request who-has 94.253.137.8 tell 94.253.136.1, length 46
22:09:32.423489 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:32.460350 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:32.465598 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:32.550169 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:32.609496 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:32.625990 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:32.629676 ARP, Request who-has 94.253.160.166 tell 94.253.160.1, length 46
22:09:32.630676 ARP, Request who-has 94.253.142.223 tell 94.253.140.1, length 46
22:09:32.642247 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:32.757470 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:32.783919 ARP, Request who-has 94.253.136.129 tell 94.253.136.1, length 46
22:09:32.942969 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:32.980685 ARP, Request who-has 94.253.136.126 tell 94.253.136.1, length 46
22:09:33.037179 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:33.074222 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:33.087559 ARP, Request who-has 94.253.139.211 tell 94.253.136.1, length 46
22:09:33.087623 IP 10.63.207.31.41161 > 83.139.64.10.domain: 49656+ PTR? 211.139.253.94.in-addr.arpa. (45)
22:09:33.114647 IP 83.139.64.10.domain > 10.63.207.31.41161: 49656*- 0/1/0 (98)
22:09:33.151985 ARP, Request who-has 94.253.139.163 tell 94.253.136.1, length 46
22:09:33.158348 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:33.164855 ARP, Request who-has 94.253.138.11 tell 94.253.136.1, length 46
22:09:33.164907 IP 10.63.207.31.57111 > 83.139.64.10.domain: 37839+ PTR? 11.138.253.94.in-addr.arpa. (44)
22:09:33.172956 IP 83.139.64.10.domain > 10.63.207.31.57111: 37839*- 0/1/0 (97)
22:09:33.172962 ARP, Request who-has 94.253.160.253 tell 94.253.160.1, length 46
22:09:33.173033 IP 10.63.207.31.44043 > 83.139.64.10.domain: 4248+ PTR? 253.160.253.94.in-addr.arpa. (45)
22:09:33.202100 IP 83.139.64.10.domain > 10.63.207.31.44043: 4248*- 0/1/0 (98)
22:09:33.207759 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:33.417885 ARP, Request who-has 94.253.138.26 tell 94.253.136.1, length 46
22:09:33.506032 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:33.554463 ARP, Request who-has 94.253.162.232 tell 94.253.160.1, length 46
22:09:33.819178 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:33.941435 ARP, Request who-has 94.253.143.100 tell 94.253.140.1, length 46
22:09:33.941502 IP 10.63.207.31.34793 > 83.139.64.10.domain: 35128+ PTR? 100.143.253.94.in-addr.arpa. (45)
22:09:33.941802 ARP, Request who-has 94.253.163.100 tell 94.253.160.1, length 46
22:09:33.943307 ARP, Request who-has 94.253.160.79 tell 94.253.160.1, length 46
22:09:33.953765 IP 83.139.64.10.domain > 10.63.207.31.34793: 35128*- 0/1/0 (98)
22:09:33.953839 IP 10.63.207.31.44759 > 83.139.64.10.domain: 58876+ PTR? 100.163.253.94.in-addr.arpa. (45)
22:09:33.962511 IP 83.139.64.10.domain > 10.63.207.31.44759: 58876*- 0/1/0 (98)
22:09:33.962569 IP 10.63.207.31.60619 > 83.139.64.10.domain: 38032+ PTR? 79.160.253.94.in-addr.arpa. (44)
22:09:33.967500 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:33.976994 IP 83.139.64.10.domain > 10.63.207.31.60619: 38032*- 0/1/0 (97)
22:09:34.078995 ARP, Request who-has 94.253.139.61 tell 94.253.136.1, length 46
22:09:34.083520 ARP, Request who-has 94.253.143.215 tell 94.253.140.1, length 46
22:09:34.095618 ARP, Request who-has 94.253.160.146 tell 94.253.160.1, length 46
22:09:34.099678 ARP, Request who-has 94.253.138.57 tell 94.253.136.1, length 46
22:09:34.099727 IP 10.63.207.31.56591 > 83.139.64.10.domain: 14613+ PTR? 57.138.253.94.in-addr.arpa. (44)
22:09:34.108021 IP 83.139.64.10.domain > 10.63.207.31.56591: 14613*- 0/1/0 (97)
22:09:34.153601 ARP, Request who-has 94.253.141.32 tell 94.253.140.1, length 46
22:09:34.153650 IP 10.63.207.31.56610 > 83.139.64.10.domain: 8670+ PTR? 32.141.253.94.in-addr.arpa. (44)
22:09:34.164586 IP 83.139.64.10.domain > 10.63.207.31.56610: 8670*- 0/1/0 (97)
22:09:34.184361 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:34.197563 ARP, Request who-has 94.253.139.74 tell 94.253.136.1, length 46
22:09:34.197612 IP 10.63.207.31.42589 > 83.139.64.10.domain: 42889+ PTR? 74.139.253.94.in-addr.arpa. (44)
22:09:34.253566 IP 83.139.64.10.domain > 10.63.207.31.42589: 42889*- 0/1/0 (97)
22:09:34.330069 ARP, Request who-has 94.253.138.222 tell 94.253.136.1, length 46
22:09:34.374814 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:34.482748 ARP, Request who-has 94.253.160.135 tell 94.253.160.1, length 46
22:09:34.482828 IP 10.63.207.31.57871 > 83.139.64.10.domain: 19463+ PTR? 135.160.253.94.in-addr.arpa. (45)
22:09:34.494474 IP 83.139.64.10.domain > 10.63.207.31.57871: 19463*- 0/1/0 (98)
22:09:34.496742 ARP, Request who-has 94.253.143.109 tell 94.253.140.1, length 46
22:09:34.599411 ARP, Request who-has 94.253.139.38 tell 94.253.136.1, length 46
22:09:34.615056 ARP, Request who-has 94.253.141.167 tell 94.253.140.1, length 46
22:09:34.700155 ARP, Request who-has 94.253.161.174 tell 94.253.160.1, length 46
22:09:34.809033 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:34.935464 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:34.986957 ARP, Request who-has 94.253.136.126 tell 94.253.136.1, length 46
22:09:35.067194 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:35.090646 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:35.123142 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:35.324921 ARP, Request who-has 94.253.160.14 tell 94.253.160.1, length 46
22:09:35.325118 ARP, Request who-has 94.253.141.82 tell 94.253.140.1, length 46
22:09:35.513217 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:35.556918 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:35.631619 ARP, Request who-has 94.253.160.166 tell 94.253.160.1, length 46
22:09:35.796790 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:35.869853 ARP, Request who-has 94.253.138.11 tell 94.253.136.1, length 46
22:09:35.881435 ARP, Request who-has 94.253.137.190 tell 94.253.136.1, length 46
22:09:35.914086 ARP, Request who-has 94.253.163.62 tell 94.253.160.1, length 46
22:09:35.914153 IP 10.63.207.31.45657 > 83.139.64.10.domain: 12247+ PTR? 62.163.253.94.in-addr.arpa. (44)
22:09:35.927382 IP 83.139.64.10.domain > 10.63.207.31.45657: 12247*- 0/1/0 (97)
22:09:35.937264 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:36.021365 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:36.073365 ARP, Request who-has 94.253.139.211 tell 94.253.136.1, length 46
22:09:36.081231 ARP, Request who-has 94.253.138.69 tell 94.253.136.1, length 46
22:09:36.081283 IP 10.63.207.31.42561 > 83.139.64.10.domain: 61748+ PTR? 69.138.253.94.in-addr.arpa. (44)
22:09:36.087992 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:36.097808 IP 83.139.64.10.domain > 10.63.207.31.42561: 61748*- 0/1/0 (97)
22:09:36.154621 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:36.228422 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:36.277171 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:36.514342 ARP, Request who-has 94.253.136.155 tell 94.253.136.1, length 46
22:09:36.514411 IP 10.63.207.31.35759 > 83.139.64.10.domain: 33344+ PTR? 155.136.253.94.in-addr.arpa. (45)
22:09:36.515247 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:36.525690 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:36.531275 IP 83.139.64.10.domain > 10.63.207.31.35759: 33344*- 0/1/0 (98)
22:09:36.689423 ARP, Request who-has 83.139.66.166 tell 83.139.66.165, length 46
22:09:36.806622 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:36.811148 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:36.913130 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:36.921929 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:37.007915 ARP, Request who-has 94.253.161.252 tell 94.253.160.1, length 46
22:09:37.170093 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:37.180776 ARP, Request who-has 94.253.139.74 tell 94.253.136.1, length 46
22:09:37.341900 ARP, Request who-has 94.253.142.13 tell 94.253.140.1, length 46
22:09:37.373450 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:37.497112 ARP, Request who-has 94.253.142.44 tell 94.253.140.1, length 46
22:09:37.497188 IP 10.63.207.31.33916 > 83.139.64.10.domain: 59237+ PTR? 44.142.253.94.in-addr.arpa. (44)
22:09:37.523021 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:37.538003 IP 83.139.64.10.domain > 10.63.207.31.33916: 59237*- 0/1/0 (97)
22:09:37.544711 ARP, Request who-has 94.253.160.135 tell 94.253.160.1, length 46
22:09:37.556608 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:37.578815 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:37.645264 ARP, Request who-has 94.253.143.23 tell 94.253.140.1, length 46
22:09:37.731840 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:37.734213 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:37.895883 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:37.984937 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:38.076111 ARP, Request who-has 94.253.139.211 tell 94.253.136.1, length 46
22:09:38.155247 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:38.170855 ARP, Request who-has 94.253.160.35 tell 94.253.160.1, length 46
22:09:38.351750 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:38.361366 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:38.417180 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:38.419458 ARP, Request who-has 94.253.140.171 tell 94.253.140.1, length 46
22:09:38.419519 IP 10.63.207.31.47226 > 83.139.64.10.domain: 12236+ PTR? 171.140.253.94.in-addr.arpa. (45)
22:09:38.445808 IP 83.139.64.10.domain > 10.63.207.31.47226: 12236*- 0/1/0 (98)
22:09:38.461491 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:38.559980 ARP, Request who-has 94.253.161.189 tell 94.253.160.1, length 46
22:09:38.560030 IP 10.63.207.31.48769 > 83.139.64.10.domain: 58795+ PTR? 189.161.253.94.in-addr.arpa. (45)
22:09:38.603065 IP 83.139.64.10.domain > 10.63.207.31.48769: 58795*- 0/1/0 (98)
22:09:38.635930 ARP, Request who-has 94.253.142.223 tell 94.253.140.1, length 46
22:09:38.671935 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:38.756736 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:38.892726 ARP, Request who-has 94.253.143.9 tell 94.253.140.1, length 46
22:09:38.912393 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:38.970866 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:38.993181 ARP, Request who-has 94.253.136.126 tell 94.253.136.1, length 46
22:09:38.999513 ARP, Request who-has 94.253.162.62 tell 94.253.160.1, length 46
22:09:39.019705 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:39.092705 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:39.120662 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:39.182110 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:39.257244 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:39.257815 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:39.268463 ARP, Request who-has 94.253.137.8 tell 94.253.136.1, length 46
22:09:39.289955 ARP, Request who-has 94.253.139.163 tell 94.253.136.1, length 46
22:09:39.293665 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:39.316654 ARP, Request who-has 94.253.136.155 tell 94.253.136.1, length 46
22:09:39.437104 ARP, Request who-has 94.253.138.26 tell 94.253.136.1, length 46
22:09:39.462092 ARP, Request who-has 94.253.141.98 tell 94.253.140.1, length 46
22:09:39.462156 IP 10.63.207.31.33885 > 83.139.64.10.domain: 48985+ PTR? 98.141.253.94.in-addr.arpa. (44)
22:09:39.473259 IP 83.139.64.10.domain > 10.63.207.31.33885: 48985*- 0/1/0 (97)
22:09:39.474636 ARP, Request who-has 94.253.162.204 tell 94.253.160.1, length 46
22:09:39.671141 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:39.883097 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:39.978069 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:40.006734 ARP, Request who-has 94.253.137.1 tell 94.253.136.1, length 46
22:09:40.006788 IP 10.63.207.31.59867 > 83.139.64.10.domain: 58954+ PTR? 1.137.253.94.in-addr.arpa. (43)
22:09:40.017321 IP 83.139.64.10.domain > 10.63.207.31.59867: 58954*- 0/1/0 (96)
22:09:40.077389 ARP, Request who-has 94.253.139.211 tell 94.253.136.1, length 46
22:09:40.188746 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:40.253151 ARP, Request who-has 94.253.143.23 tell 94.253.140.1, length 46
22:09:40.281117 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:40.327651 ARP, Request who-has 94.253.138.217 tell 94.253.136.1, length 46
22:09:40.390445 ARP, Request who-has 94.253.161.70 tell 94.253.160.1, length 46
22:09:40.390517 IP 10.63.207.31.50365 > 83.139.64.10.domain: 25208+ PTR? 70.161.253.94.in-addr.arpa. (44)
22:09:40.412451 IP 83.139.64.10.domain > 10.63.207.31.50365: 25208*- 0/1/0 (97)
22:09:40.441795 ARP, Request who-has 94.253.162.80 tell 94.253.160.1, length 46
22:09:40.441852 IP 10.63.207.31.60429 > 83.139.64.10.domain: 20920+ PTR? 80.162.253.94.in-addr.arpa. (44)
22:09:40.463130 IP 83.139.64.10.domain > 10.63.207.31.60429: 20920*- 0/1/0 (97)
22:09:40.530410 ARP, Request who-has 94.253.143.181 tell 94.253.140.1, length 46
22:09:40.530469 IP 10.63.207.31.39132 > 83.139.64.10.domain: 58908+ PTR? 181.143.253.94.in-addr.arpa. (45)
22:09:40.576844 IP 83.139.64.10.domain > 10.63.207.31.39132: 58908*- 0/1/0 (98)
22:09:40.612029 ARP, Request who-has 94.253.141.167 tell 94.253.140.1, length 46
22:09:40.749185 ARP, Request who-has 94.253.141.184 tell 94.253.140.1, length 46
22:09:40.749239 IP 10.63.207.31.51163 > 83.139.64.10.domain: 32877+ PTR? 184.141.253.94.in-addr.arpa. (45)
22:09:40.757704 IP 83.139.64.10.domain > 10.63.207.31.51163: 32877*- 0/1/0 (98)
22:09:40.880847 ARP, Request who-has 94.253.137.190 tell 94.253.136.1, length 46
22:09:40.888824 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:40.897218 ARP, Request who-has 94.253.136.64 tell 94.253.136.1, length 46
22:09:40.897271 IP 10.63.207.31.48177 > 83.139.64.10.domain: 63972+ PTR? 64.136.253.94.in-addr.arpa. (44)
22:09:40.912858 IP 83.139.64.10.domain > 10.63.207.31.48177: 63972*- 0/1/0 (97)
22:09:41.006243 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:41.019688 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:41.074132 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:41.274010 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:41.406746 ARP, Request who-has 94.253.140.171 tell 94.253.140.1, length 46
22:09:41.449031 ARP, Request who-has 94.253.160.14 tell 94.253.160.1, length 46
22:09:41.487566 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:41.519929 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:41.541819 ARP, Request who-has 94.253.141.209 tell 94.253.140.1, length 46
22:09:41.541879 IP 10.63.207.31.59820 > 83.139.64.10.domain: 2123+ PTR? 209.141.253.94.in-addr.arpa. (45)
22:09:41.562576 IP 83.139.64.10.domain > 10.63.207.31.59820: 2123*- 0/1/0 (98)
22:09:41.617614 ARP, Request who-has 94.253.160.166 tell 94.253.160.1, length 46
22:09:41.628925 ARP, Request who-has 94.253.142.200 tell 94.253.140.1, length 46
22:09:41.628975 IP 10.63.207.31.44527 > 83.139.64.10.domain: 1819+ PTR? 200.142.253.94.in-addr.arpa. (45)
22:09:41.658565 IP 83.139.64.10.domain > 10.63.207.31.44527: 1819*- 0/1/0 (98)
22:09:41.670761 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:41.725972 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:41.735994 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:41.923429 ARP, Request who-has 94.253.141.98 tell 94.253.140.1, length 46
22:09:41.934089 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:42.023947 ARP, Request who-has 94.253.138.11 tell 94.253.136.1, length 46
22:09:42.045794 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:42.109270 ARP, Request who-has 94.253.161.189 tell 94.253.160.1, length 46
22:09:42.115600 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:42.239265 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:42.402060 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:42.477933 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:42.583285 ARP, Request who-has 94.253.161.172 tell 94.253.160.1, length 46
22:09:42.583347 IP 10.63.207.31.44970 > 83.139.64.10.domain: 39993+ PTR? 172.161.253.94.in-addr.arpa. (45)
22:09:42.595014 IP 83.139.64.10.domain > 10.63.207.31.44970: 39993*- 0/1/0 (98)
22:09:42.613977 ARP, Request who-has 94.253.141.43 tell 94.253.140.1, length 46
22:09:42.614029 IP 10.63.207.31.52873 > 83.139.64.10.domain: 2360+ PTR? 43.141.253.94.in-addr.arpa. (44)
22:09:42.661664 IP 83.139.64.10.domain > 10.63.207.31.52873: 2360*- 0/1/0 (97)
22:09:42.739478 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:42.786638 ARP, Request who-has 94.253.141.88 tell 94.253.140.1, length 46
22:09:42.786689 IP 10.63.207.31.56102 > 83.139.64.10.domain: 10893+ PTR? 88.141.253.94.in-addr.arpa. (44)
22:09:42.796869 IP 83.139.64.10.domain > 10.63.207.31.56102: 10893*- 0/1/0 (97)
22:09:42.852039 ARP, Request who-has 94.253.162.177 tell 94.253.160.1, length 46
22:09:42.852088 IP 10.63.207.31.40661 > 83.139.64.10.domain: 611+ PTR? 177.162.253.94.in-addr.arpa. (45)
22:09:42.862413 IP 83.139.64.10.domain > 10.63.207.31.40661: 611*- 0/1/0 (98)
22:09:42.906746 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:42.917522 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:42.955593 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:42.991256 ARP, Request who-has 94.253.142.189 tell 94.253.140.1, length 46
22:09:43.011148 ARP, Request who-has 94.253.163.244 tell 94.253.160.1, length 46
22:09:43.180603 ARP, Request who-has 94.253.160.150 tell 94.253.160.1, length 46
22:09:43.189023 ARP, Request who-has 94.253.143.64 tell 94.253.140.1, length 46
22:09:43.212819 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:43.218037 ARP, Request who-has 94.253.139.61 tell 94.253.136.1, length 46
22:09:43.388663 ARP, Request who-has 94.253.162.232 tell 94.253.160.1, length 46
22:09:43.392045 ARP, Request who-has 94.253.161.70 tell 94.253.160.1, length 46
22:09:43.512788 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:43.514076 ARP, Request who-has 94.253.162.62 tell 94.253.160.1, length 46
22:09:43.552687 ARP, Request who-has 94.253.160.135 tell 94.253.160.1, length 46
22:09:43.568336 ARP, Request who-has 94.253.142.19 tell 94.253.140.1, length 46
22:09:43.568405 IP 10.63.207.31.57856 > 83.139.64.10.domain: 45245+ PTR? 19.142.253.94.in-addr.arpa. (44)
22:09:43.588333 IP 83.139.64.10.domain > 10.63.207.31.57856: 45245*- 0/1/0 (97)
22:09:43.622260 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:43.631394 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:43.638935 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:43.654343 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:43.695711 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:43.773250 ARP, Request who-has 94.253.162.200 tell 94.253.160.1, length 46
22:09:43.942413 ARP, Request who-has 94.253.143.100 tell 94.253.140.1, length 46
22:09:43.943364 ARP, Request who-has 94.253.140.190 tell 94.253.140.1, length 46
22:09:43.943416 IP 10.63.207.31.48191 > 83.139.64.10.domain: 57947+ PTR? 190.140.253.94.in-addr.arpa. (45)
22:09:43.968257 IP 83.139.64.10.domain > 10.63.207.31.48191: 57947*- 0/1/0 (98)
22:09:43.988796 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:44.031743 ARP, Request who-has 94.253.142.17 tell 94.253.140.1, length 46
22:09:44.031792 IP 10.63.207.31.36630 > 83.139.64.10.domain: 49520+ PTR? 17.142.253.94.in-addr.arpa. (44)
22:09:44.048588 ARP, Request who-has 94.253.163.78 tell 94.253.160.1, length 46
22:09:44.068220 IP 83.139.64.10.domain > 10.63.207.31.36630: 49520*- 0/1/0 (97)
22:09:44.068286 IP 10.63.207.31.60612 > 83.139.64.10.domain: 20594+ PTR? 78.163.253.94.in-addr.arpa. (44)
22:09:44.076253 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:44.079527 IP 83.139.64.10.domain > 10.63.207.31.60612: 20594*- 0/1/0 (97)
22:09:44.084627 ARP, Request who-has 94.253.139.211 tell 94.253.136.1, length 46
22:09:44.095200 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:44.102324 ARP, Request who-has 94.253.163.123 tell 94.253.160.1, length 46
22:09:44.102372 IP 10.63.207.31.57991 > 83.139.64.10.domain: 35238+ PTR? 123.163.253.94.in-addr.arpa. (45)
22:09:44.109004 IP 83.139.64.10.domain > 10.63.207.31.57991: 35238*- 0/1/0 (98)
22:09:44.161927 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:44.202160 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:44.230350 ARP, Request who-has 94.253.163.202 tell 94.253.160.1, length 46
22:09:44.230400 IP 10.63.207.31.55731 > 83.139.64.10.domain: 36421+ PTR? 202.163.253.94.in-addr.arpa. (45)
22:09:44.248399 IP 83.139.64.10.domain > 10.63.207.31.55731: 36421*- 0/1/0 (98)
22:09:44.272793 ARP, Request who-has 94.253.141.184 tell 94.253.140.1, length 46
22:09:44.546221 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:44.549658 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:44.628652 ARP, Request who-has 94.253.140.129 tell 94.253.140.1, length 46
22:09:44.797459 ARP, Request who-has 94.253.141.98 tell 94.253.140.1, length 46
22:09:44.805455 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:44.945509 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:45.012029 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:45.087881 ARP, Request who-has 94.253.163.8 tell 94.253.160.1, length 46
22:09:45.087946 IP 10.63.207.31.40740 > 83.139.64.10.domain: 24114+ PTR? 8.163.253.94.in-addr.arpa. (43)
22:09:45.110949 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:45.116106 IP 83.139.64.10.domain > 10.63.207.31.40740: 24114*- 0/1/0 (96)
22:09:45.121966 ARP, Request who-has 94.253.161.189 tell 94.253.160.1, length 46
22:09:45.141385 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:45.229700 ARP, Request who-has 94.253.143.109 tell 94.253.140.1, length 46
22:09:45.239766 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:45.281827 ARP, Request who-has 94.253.142.13 tell 94.253.140.1, length 46
22:09:45.370455 ARP, Request who-has 94.253.136.148 tell 94.253.136.1, length 46
22:09:45.502026 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:45.548794 ARP, Request who-has 94.253.139.163 tell 94.253.136.1, length 46
22:09:45.598327 ARP, Request who-has 94.253.161.172 tell 94.253.160.1, length 46
22:09:45.630574 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:45.692562 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:45.758266 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:45.801238 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:45.850847 ARP, Request who-has 94.253.138.92 tell 94.253.136.1, length 46
22:09:45.850910 IP 10.63.207.31.49652 > 83.139.64.10.domain: 19900+ PTR? 92.138.253.94.in-addr.arpa. (44)
22:09:45.869915 ARP, Request who-has 94.253.141.88 tell 94.253.140.1, length 46
22:09:45.874863 ARP, Request who-has 94.253.137.233 tell 94.253.136.1, length 46
22:09:45.877863 IP 83.139.64.10.domain > 10.63.207.31.49652: 19900*- 0/1/0 (97)
22:09:45.885010 ARP, Request who-has 94.253.161.21 tell 94.253.160.1, length 46
22:09:45.975697 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:46.101335 ARP, Request who-has 94.253.138.217 tell 94.253.136.1, length 46
22:09:46.102318 ARP, Request who-has 94.253.142.17 tell 94.253.140.1, length 46
22:09:46.175847 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:46.269693 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:46.309635 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:46.314755 ARP, Request who-has 94.253.160.169 tell 94.253.160.1, length 46
22:09:46.381584 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:46.485721 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:46.548224 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:46.658163 ARP, Request who-has 94.253.140.98 tell 94.253.140.1, length 46
22:09:46.759827 ARP, Request who-has 94.253.143.31 tell 94.253.140.1, length 46
22:09:46.882260 ARP, Request who-has 94.253.161.113 tell 94.253.160.1, length 46
22:09:46.882334 IP 10.63.207.31.52197 > 83.139.64.10.domain: 43817+ PTR? 113.161.253.94.in-addr.arpa. (45)
22:09:46.882393 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:46.891632 IP 83.139.64.10.domain > 10.63.207.31.52197: 43817*- 0/1/0 (98)
22:09:47.223889 ARP, Request who-has 94.253.137.17 tell 94.253.136.1, length 46
22:09:47.232776 ARP, Request who-has 94.253.163.202 tell 94.253.160.1, length 46
22:09:47.248152 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:47.404764 ARP, Request who-has 94.253.140.171 tell 94.253.140.1, length 46
22:09:47.431806 ARP, Request who-has 94.253.162.230 tell 94.253.160.1, length 46
22:09:47.431866 IP 10.63.207.31.42609 > 83.139.64.10.domain: 54247+ PTR? 230.162.253.94.in-addr.arpa. (45)
22:09:47.442508 ARP, Request who-has 94.253.141.3 tell 94.253.140.1, length 46
22:09:47.445799 IP 83.139.64.10.domain > 10.63.207.31.42609: 54247*- 0/1/0 (98)
22:09:47.613708 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:47.756315 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:47.767838 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:48.059416 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:48.062154 ARP, Request who-has 94.253.163.8 tell 94.253.160.1, length 46
22:09:48.082154 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:48.105674 ARP, Request who-has 94.253.141.98 tell 94.253.140.1, length 46
22:09:48.124114 ARP, Request who-has 94.253.142.95 tell 94.253.140.1, length 46
22:09:48.189977 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:48.273051 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:48.454934 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:48.515633 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:48.801618 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:48.838819 ARP, Request who-has 94.253.142.82 tell 94.253.140.1, length 46
22:09:48.838883 IP 10.63.207.31.44496 > 83.139.64.10.domain: 48503+ PTR? 82.142.253.94.in-addr.arpa. (44)
22:09:48.851538 ARP, Request who-has 94.253.162.177 tell 94.253.160.1, length 46
22:09:48.856074 IP 83.139.64.10.domain > 10.63.207.31.44496: 48503*- 0/1/0 (97)
22:09:48.890412 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:48.942695 ARP, Request who-has 94.253.137.103 tell 94.253.136.1, length 46
22:09:48.942746 IP 10.63.207.31.35612 > 83.139.64.10.domain: 8701+ PTR? 103.137.253.94.in-addr.arpa. (45)
22:09:48.954715 IP 83.139.64.10.domain > 10.63.207.31.35612: 8701*- 0/1/0 (98)
22:09:48.956153 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:48.989599 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:49.079351 ARP, Request who-has 94.253.141.209 tell 94.253.140.1, length 46
22:09:49.090720 ARP, Request who-has 94.253.141.70 tell 94.253.140.1, length 46
22:09:49.090768 IP 10.63.207.31.41929 > 83.139.64.10.domain: 58844+ PTR? 70.141.253.94.in-addr.arpa. (44)
22:09:49.150079 IP 83.139.64.10.domain > 10.63.207.31.41929: 58844*- 0/1/0 (97)
22:09:49.257045 ARP, Request who-has 94.253.163.244 tell 94.253.160.1, length 46
22:09:49.382084 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:49.387377 ARP, Request who-has 94.253.162.171 tell 94.253.160.1, length 46
22:09:49.387436 IP 10.63.207.31.55208 > 83.139.64.10.domain: 52655+ PTR? 171.162.253.94.in-addr.arpa. (45)
22:09:49.398141 IP 83.139.64.10.domain > 10.63.207.31.55208: 52655*- 0/1/0 (98)
22:09:49.427303 ARP, Request who-has 94.253.161.70 tell 94.253.160.1, length 46
22:09:49.430517 ARP, Request who-has 94.253.162.23 tell 94.253.160.1, length 46
22:09:49.554648 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:49.660438 ARP, Request who-has 94.253.141.193 tell 94.253.140.1, length 46
22:09:49.660520 IP 10.63.207.31.53545 > 83.139.64.10.domain: 13337+ PTR? 193.141.253.94.in-addr.arpa. (45)
22:09:49.668650 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:49.672989 IP 83.139.64.10.domain > 10.63.207.31.53545: 13337*- 0/1/0 (98)
22:09:49.785729 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:50.067069 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:50.072082 ARP, Request who-has 94.253.142.17 tell 94.253.140.1, length 46
22:09:50.136193 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:50.146984 ARP, Request who-has 94.253.142.83 tell 94.253.140.1, length 46
22:09:50.256011 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:50.256417 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:50.257784 ARP, Request who-has 94.253.141.184 tell 94.253.140.1, length 46
22:09:50.310810 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:50.437737 ARP, Request who-has 94.253.137.159 tell 94.253.136.1, length 46
22:09:50.541388 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:50.553865 ARP, Request who-has 94.253.160.169 tell 94.253.160.1, length 46
22:09:50.647145 ARP, Request who-has 94.253.139.157 tell 94.253.136.1, length 46
22:09:50.665432 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:50.729839 ARP, Request who-has 94.253.139.61 tell 94.253.136.1, length 46
22:09:50.750144 ARP, Request who-has 94.253.160.57 tell 94.253.160.1, length 46
22:09:50.750228 IP 10.63.207.31.39089 > 83.139.64.10.domain: 22209+ PTR? 57.160.253.94.in-addr.arpa. (44)
22:09:50.766163 IP 83.139.64.10.domain > 10.63.207.31.39089: 22209*- 0/1/0 (97)
22:09:50.884263 ARP, Request who-has 94.253.161.21 tell 94.253.160.1, length 46
22:09:50.888181 ARP, Request who-has 94.253.143.64 tell 94.253.140.1, length 46
22:09:51.058512 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:51.174095 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:51.255672 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:51.255961 ARP, Request who-has 94.253.143.198 tell 94.253.140.1, length 46
22:09:51.256439 ARP, Request who-has 94.253.141.215 tell 94.253.140.1, length 46
22:09:51.256492 IP 10.63.207.31.45931 > 83.139.64.10.domain: 25995+ PTR? 215.141.253.94.in-addr.arpa. (45)
22:09:51.257766 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:51.272873 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:51.293778 IP 83.139.64.10.domain > 10.63.207.31.45931: 25995*- 0/1/0 (98)
22:09:51.301514 ARP, Request who-has 94.253.161.189 tell 94.253.160.1, length 46
22:09:51.326979 ARP, Request who-has 94.253.140.75 tell 94.253.140.1, length 46
22:09:51.417078 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:51.431970 ARP, Request who-has 94.253.138.45 tell 94.253.136.1, length 46
22:09:51.449397 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:51.512422 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:51.588696 ARP, Request who-has 94.253.163.129 tell 94.253.160.1, length 46
22:09:51.600799 ARP, Request who-has 94.253.161.172 tell 94.253.160.1, length 46
22:09:51.673681 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:51.762250 ARP, Request who-has 94.253.139.232 tell 94.253.136.1, length 46
22:09:51.935837 ARP, Request who-has 94.253.161.109 tell 94.253.160.1, length 46
22:09:51.988394 ARP, Request who-has 94.253.143.23 tell 94.253.140.1, length 46
22:09:52.046972 ARP, Request who-has 94.253.137.138 tell 94.253.136.1, length 46
22:09:52.062985 ARP, Request who-has 94.253.138.217 tell 94.253.136.1, length 46
22:09:52.081843 ARP, Request who-has 94.253.160.50 tell 94.253.160.1, length 46
22:09:52.102659 ARP, Request who-has 94.253.162.44 tell 94.253.160.1, length 46
22:09:52.249284 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:52.337745 ARP, Request who-has 94.253.162.171 tell 94.253.160.1, length 46
22:09:52.449230 ARP, Request who-has 94.253.162.172 tell 94.253.160.1, length 46
22:09:52.449424 ARP, Request who-has 94.253.162.71 tell 94.253.160.1, length 46
22:09:52.449506 IP 10.63.207.31.49918 > 83.139.64.10.domain: 12245+ PTR? 71.162.253.94.in-addr.arpa. (44)
22:09:52.460484 IP 83.139.64.10.domain > 10.63.207.31.49918: 12245*- 0/1/0 (97)
22:09:52.606883 ARP, Request who-has 94.253.143.206 tell 94.253.140.1, length 46
22:09:52.636245 ARP, Request who-has 94.253.143.9 tell 94.253.140.1, length 46
22:09:52.931191 ARP, Request who-has 94.253.162.177 tell 94.253.160.1, length 46
22:09:52.963271 ARP, Request who-has 94.253.163.146 tell 94.253.160.1, length 46
22:09:53.188192 ARP, Request who-has 94.253.160.35 tell 94.253.160.1, length 46
22:09:53.240946 ARP, Request who-has 94.253.143.92 tell 94.253.140.1, length 46
22:09:53.241057 IP 10.63.207.31.40720 > 83.139.64.10.domain: 44911+ PTR? 92.143.253.94.in-addr.arpa. (44)
22:09:53.242231 ARP, Request who-has 94.253.143.78 tell 94.253.140.1, length 46
22:09:53.252646 IP 83.139.64.10.domain > 10.63.207.31.40720: 44911*- 0/1/0 (97)
22:09:53.261317 ARP, Request who-has 94.253.163.244 tell 94.253.160.1, length 46
22:09:53.296932 ARP, Request who-has 94.253.136.215 tell 94.253.136.1, length 46
22:09:53.296990 IP 10.63.207.31.42118 > 83.139.64.10.domain: 18126+ PTR? 215.136.253.94.in-addr.arpa. (45)
22:09:53.302246 ARP, Request who-has 94.253.161.68 tell 94.253.160.1, length 46
22:09:53.318662 IP 83.139.64.10.domain > 10.63.207.31.42118: 18126*- 0/1/0 (98)
22:09:53.353456 ARP, Request who-has 94.253.140.133 tell 94.253.140.1, length 46
22:09:53.444968 ARP, Request who-has 94.253.162.117 tell 94.253.160.1, length 46
22:09:53.511429 ARP, Request who-has 94.253.142.191 tell 94.253.140.1, length 46
22:09:53.524447 ARP, Request who-has 94.253.162.72 tell 94.253.160.1, length 46
22:09:53.524511 IP 10.63.207.31.54381 > 83.139.64.10.domain: 34143+ PTR? 72.162.253.94.in-addr.arpa. (44)
22:09:53.534590 IP 83.139.64.10.domain > 10.63.207.31.54381: 34143*- 0/1/0 (97)
22:09:53.555903 ARP, Request who-has 94.253.139.91 tell 94.253.136.1, length 46
22:09:53.665335 ARP, Request who-has 94.253.142.13 tell 94.253.140.1, length 46
22:09:53.714378 ARP, Request who-has 94.253.139.61 tell 94.253.136.1, length 46
22:09:53.727392 ARP, Request who-has 94.253.163.8 tell 94.253.160.1, length 46
22:09:53.761531 ARP, Request who-has 94.253.138.177 tell 94.253.136.1, length 46
22:09:53.771164 ARP, Request who-has 94.253.139.182 tell 94.253.136.1, length 46
22:09:53.838095 ARP, Request who-has 94.253.161.87 tell 94.253.160.1, length 46
22:09:54.046997 ARP, Request who-has 94.253.162.20 tell 94.253.160.1, length 46
22:09:54.094075 ARP, Request who-has 94.253.162.200 tell 94.253.160.1, length 46
22:09:54.136856 ARP, Request who-has 94.253.139.247 tell 94.253.136.1, length 46
22:09:54.136939 IP 10.63.207.31.40901 > 83.139.64.10.domain: 19133+ PTR? 247.139.253.94.in-addr.arpa. (45)
22:09:54.161965 IP 83.139.64.10.domain > 10.63.207.31.40901: 19133*- 0/1/0 (98)
22:09:54.181277 ARP, Request who-has 94.253.141.193 tell 94.253.140.1, length 46
22:09:54.202023 ARP, Request who-has 94.253.136.161 tell 94.253.136.1, length 46
22:09:54.244377 ARP, Request who-has 94.253.141.215 tell 94.253.140.1, length 46
22:09:54.401104 ARP, Request who-has 94.253.161.154 tell 94.253.160.1, length 46
22:09:54.422869 ARP, Request who-has 94.253.162.73 tell 94.253.160.1, length 46
22:09:54.422933 IP 10.63.207.31.56053 > 83.139.64.10.domain: 36264+ PTR? 73.162.253.94.in-addr.arpa. (44)
22:09:54.431122 IP 83.139.64.10.domain > 10.63.207.31.56053: 36264*- 0/1/0 (97)
22:09:54.468772 ARP, Request who-has 94.253.141.81 tell 94.253.140.1, length 46
22:09:54.529388 ARP, Request who-has 94.253.161.125 tell 94.253.160.1, length 46
22:09:54.544089 ARP, Request who-has 94.253.163.61 tell 94.253.160.1, length 46
22:09:54.587579 ARP, Request who-has 94.253.163.129 tell 94.253.160.1, length 46
22:09:54.703551 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [P.], seq 325:341, ack 157, win 6432, length 16: pptp CTRL_MSGTYPE=CCRQ CALL_ID(0)
22:09:54.703604 IP 10.63.207.31.44464 > 10.64.0.1.pptp: Flags [F.], seq 341, ack 157, win 6432, length 0
22:09:54.710547 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [.], ack 325, win 3804, length 0
22:09:54.710585 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [.], ack 342, win 3788, length 0
22:09:54.710605 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [.], ack 342, win 3788, length 0
22:09:54.711293 IP 10.64.0.1.pptp > 10.63.207.31.44464: Flags [R], seq 2098537987, win 3788, length 0
22:09:54.756283 ARP, Request who-has 94.253.161.174 tell 94.253.160.1, length 46
22:09:54.877101 ARP, Request who-has 94.253.160.250 tell 94.253.160.1, length 46
22:09:54.882955 ARP, Request who-has 94.253.161.131 tell 94.253.160.1, length 46
22:09:54.926057 ARP, Request who-has 94.253.138.44 tell 94.253.136.1, length 46
22:09:54.949239 ARP, Request who-has 94.253.163.79 tell 94.253.160.1, length 46
22:09:54.949351 IP 10.63.207.31.47629 > 83.139.64.10.domain: 20211+ PTR? 79.163.253.94.in-addr.arpa. (44)
22:09:54.967183 ARP, Request who-has 94.253.162.177 tell 94.253.160.1, length 46
22:09:54.986581 IP 83.139.64.10.domain > 10.63.207.31.47629: 20211*- 0/1/0 (97)
22:09:54.989544 ARP, Request who-has 94.253.141.224 tell 94.253.140.1, length 46
22:09:55.081438 ARP, Request who-has 94.253.141.98 tell 94.253.140.1, length 46
22:09:55.147430 ARP, Request who-has 94.253.138.221 tell 94.253.136.1, length 46
22:09:55.147489 IP 10.63.207.31.58106 > 83.139.64.10.domain: 64718+ PTR? 221.138.253.94.in-addr.arpa. (45)
22:09:55.152562 ARP, Request who-has 94.253.137.169 tell 94.253.136.1, length 46
22:09:55.155020 ARP, Request who-has 94.253.140.187 tell 94.253.140.1, length 46
22:09:55.173285 IP 83.139.64.10.domain > 10.63.207.31.58106: 64718*- 0/1/0 (98)
22:09:55.195226 ARP, Request who-has 94.253.141.209 tell 94.253.140.1, length 46

```

As you can see from the dump, packages are not being sent at all, and GRE packages are nowhere to be seen.

pptpclient documentation suggests two solutions for this case:
([http://pptpclient.sourceforge.net/howto-diagnosis.phtml#client_no_gre_tx](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#client_no_gre_tx))

1. turn off sync and try again - sync is off already
2. iptables or ipchains rules which block GRE transmission - I don't use either of those.
(3.) I also don't have any kind of firewall or another device in the network.

I'm going crazy. I tried just about every option in /etc/ppp/options, it doesn't seem to make a difference. The connection works in Windows XP.

I'm using Archlinux, not Ubuntu, I hope that's not a problem. The configuration is the same I believe.

Anyway, any help is most welcomed!

Regards,

karabaja4

---

### Post by utilitytrack on 2010-09-11
That's interesting. Please say what the device you got from your ISP and how to you connect with him; what version of pptp client you use. Also post here output from these commands:

```
$ uname -a
$ cat /proc/cmdline
$ lspci -nn | grep -E 'Ethernet|Network'
$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'

```

next outputs before and after running of pptp client:

```
# ifconfig -a
# route -n

```

[SIZE="1"]*Also: please, if you still hope get help on this forum, install latest Ubuntu or any other Debian-based distro. But if you are fan of Arch, I think we can't help you :)*
[/SIZE]

---

### Post by karabaja4 on 2010-09-11
My ISP gave me Thomson THG540K modem  (not a router) for tunneling to their VPN server using PPTP. It has one LAN port, no wireless and no web configuration. It connects through LAN cable. It has USB connection as well but that requires drivers which don't exist for Linux systems. I'm using pptpclient 1.7.2. Here are the outputs:

uname -a (don't see why is this relevant, but ok):

```
[badc0ffee ~]$ uname -a
Linux badc0ffee 2.6.35-ARCH #1 SMP PREEMPT Fri Aug 27 17:14:28 CEST 2010 x86_64 AMD Athlon(tm) 64 
Processor 3200+ AuthenticAMD GNU/Linux
```

cat /proc/cmdline (this either, I have few partitions and disks, I use sda2 for root, sda3 for swap and sda4 for home - sda1 are windows 7, sdb1 and sdc1 are my other non-system ext4 harddrives)

```
[badc0ffee ~]$ cat /proc/cmdline 
root=/dev/sda2 ro vga=773
```

lspci - I put in a second cheap ethernet card I found in the all-mighty-old-spare-computer-parts-box just in case the first (the one on my mainboard) was faulty and was causing problems, it turned out that wasn't the case. It behaves the same on that one as it does on the first one. The Ralink RT61 listed here is my PCI wireless card.

```
[badc0ffee ~]$ lspci -nn | grep -E 'Ethernet|Network'
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:09.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```

ps ouptput - don't worry, I'm running pretty clean no-DE setup, no daemons could interfere with the network without my knowing it:

```
[badc0ffee ~]$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'
igor      3976  3802  0 23:46 pts/1    00:00:00 grep -E -i supplicant|Netwo|nm-app
```

ifconfig -a, before dhcpcd (if I start my vmware daemon there are vmnetX interfaces too - eth0 and eth1 are because of the second ethernet card. This time I'll test the pptp on eth1 because it's the one cable is currently plugged into it and I'm too lazy to reconnect it to eth0):

```
[badc0ffee ~]$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:DB:4C:A7:E2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:C0:B6:95  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0B:AD:C0:FF:EE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2467289 (2.3 Mb)  TX bytes:521405 (509.1 Kb)
```

route -n before dhcpcd, no routes yet:

```
[badc0ffee ~]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

ifconfig -a after dhcpcd on eth1:

```
[badc0ffee ~]$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:DB:4C:A7:E2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:C0:B6:95  
          inet addr:10.63.207.30  Bcast:10.63.207.255  Mask:255.255.252.0
          inet6 addr: fe80::2e0:4cff:fec0:b695/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150390 (146.8 Kb)  TX bytes:9718 (9.4 Kb)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0B:AD:C0:FF:EE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2467289 (2.3 Mb)  TX bytes:521405 (509.1 Kb)

```

route -n after dhcpcd, route exists:

```
[badc0ffee ~]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.63.204.0     0.0.0.0         255.255.252.0   U     203    0        0 eth1
0.0.0.0         10.63.204.1     0.0.0.0         UG    203    0        0 eth1
```

ifconfig -a after timed out pptp on eth1:

```
[badc0ffee ~]$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:DB:4C:A7:E2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:C0:B6:95  
          inet addr:10.63.207.30  Bcast:10.63.207.255  Mask:255.255.252.0
          inet6 addr: fe80::2e0:4cff:fec0:b695/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273197 (266.7 Kb)  TX bytes:12339 (12.0 Kb)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0B:AD:C0:FF:EE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2467289 (2.3 Mb)  TX bytes:521405 (509.1 Kb)

```

route -n after pptp timed out, another route added:

```
[badc0ffee ~]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.0.1       10.63.204.1     255.255.255.255 UGH   0      0        0 eth1
10.63.204.0     0.0.0.0         255.255.252.0   U     203    0        0 eth1
0.0.0.0         10.63.204.1     0.0.0.0         UG    203    0        0 eth1

```

I've been all over this already, it doesn't show a thing wrong... the main (and maybe the only) problem is that pon (pppd) doesn't transmit any packages to the server, and therefore the server doesn't respond with authentication.

> **utilitytrack said:**
> [SIZE="1"]*Also: please, if you still hope get help on this forum, install latest Ubuntu or any other Debian-based distro. But if you are fan of Arch, I think we can't help you :)*
[/SIZE]

[SIZE="1"]I used to be a long time ubuntu user for what it's worth (versions 7.04 through 9.10). But I don't see why does it matter, aren't we all friends here using the same Linux base system? Isn't that what the open source world is all about, community driven support without fanboyism (is that the word?) and the freedom of choice without the intrusion of software someone considers better or more suitable. At the end it all comes down on what fits you and only you. But that's not the reason not to help others, I think? :)[/SIZE]

---

### Post by utilitytrack on 2010-09-12
> My ISP gave me Thomson THG540K modem

Hmm... Your ISP uses DOCSIS technology... I'm absolutely newbie in this case, because never faced with cable providers. So I'm probable don't help you, sorry :(

> It has USB connection as well but that requires drivers which don't exist for Linux systems.

That's not a fact. Look in this:
```
# modprobe --list | grep cdc
```

> ...don't worry, I'm running pretty clean no-DE setup, no daemons could interfere with the network without my knowing it

It's awesome. Really.

> I start my vmware daemon there are vmnetX interfaces too - eth0 and eth1...

I know that it's stupid suggestion but could you remove vmware and make testing on clean machine? With one, but 100% working LAN card? Simply I think that we don't need extra complexity.

> the main (and maybe the only) problem is that pon (pppd) doesn't transmit any packages

Yes, seems that the problems in this. But why? Not yet clear. Looks like on some hardware failure. Or you wish say under OtherOS all work properly?!

***

Ok. As I already said, probably I can't help, but still I have some thoughts which may be useful.

Please say, your default gateway 10.63.204.1 and some of VPN servers (10.64.0.1 for example) send echo reply when you ping it? 

Do you sure that routes which you get from DHCP server are right?
Your ISP has some local resources (forums, corporate web servers, game servers, etc)? 

Do you exactly know that your ISP uses PAP authentication instead of MSCHAP? As I see if their VPN servers work on OtherOS Server, it's little strange.

Also I can give advice to add following to /etc/ppp/options:
```
connect /bin/true
```

I see that file /etc/ppp/pap-secrets has little other syntax: 
```
login * password
```

hovewer /etc/ppp/chap-secrets file has this syntax:
```
login PPTP password * 
```

I sure you know all this, and it's not a reason of trouble, but just in case.

Finally, do you absolutely sure that firewall is completely turned off and hasn't impact on network connections? 

PS
May be you try to use ISC DHCP (dhcp3) client ([http://ftp.isc.org/isc/dhcp/](http://ftp.isc.org/isc/dhcp/)) instead of dhcpcd? It worked better in my experiences.

PPS
please give output of 
```
# netstat --inet --numeric-hosts -a -p -e -n -c
```

when you try to establish the connection.


-------------
[SIZE="1"]> *Isn't that what the open source world is all about... and the freedom of choice without the intrusion of software someone considers better or more suitable... that's not the reason not to help others*

You are absolutely right, I agree 100%. Sorry me that I suggested you before.[/SIZE]

---

