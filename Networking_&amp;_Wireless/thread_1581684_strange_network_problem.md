---
title: "strange network problem"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by sinbaddd on 2010-09-25
hi,

i recently installed ubuntu. i am experiencing a strange network problem.
i connect to the internet thru a wireless router. apparently i am able to
my web browser (firefox) can open only google related pages.
none of the other sites are opening. i am attaching the tcpdump output.
when i try to open yahoo.com and businessweek.com site. please help.

192.168.2.1 is my wireless router ip address. (which is connected to 192.168.1.1)
192.168.1.1 is my normal rouer ip address (which is connected to the internet)

19:23:20.194783 IP (tos 0x0, ttl 64, id 20763, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.49295 > 208.43.201.101-static.reverse.softlayer.com.www: Flags [F.], cksum 0x8c0b (correct), seq 3678350293, ack 381068896, win 92, options [nop,nop,TS val 429891 ecr 2798196495,nop,nop,sack 1 {1443:1444}], length 0
19:23:20.195968 IP (tos 0x0, ttl 64, id 36675, offset 0, flags [DF], proto UDP (17), length 73)
    myhost.local.49896 > 192.168.1.1.domain: [udp sum ok] 26944+ PTR? 101.201.43.208.in-addr.arpa. (45)
19:23:20.196441 IP (tos 0x0, ttl 64, id 36675, offset 0, flags [DF], proto UDP (17), length 59)
    myhost.local.40736 > 192.168.1.1.domain: [udp sum ok] 15819+ AAAA? [www.yahoo.com]("http://www.yahoo.com"). (31)
19:23:20.231225 IP (tos 0x0, ttl 250, id 1537, offset 0, flags [DF], proto UDP (17), length 130)
    192.168.1.1.domain > myhost.local.49896: [no cksum] 26944 q: PTR? 101.201.43.208.in-addr.arpa. 1/0/0 101.201.43.208.in-addr.arpa. (102)
19:23:20.231669 IP (tos 0x0, ttl 64, id 36684, offset 0, flags [DF], proto UDP (17), length 72)
    myhost.local.57391 > 192.168.1.1.domain: [udp sum ok] 6006+ PTR? 100.2.168.192.in-addr.arpa. (44)
19:23:20.234135 IP (tos 0x0, ttl 250, id 48324, offset 0, flags [DF], proto UDP (17), length 16
    192.168.1.1.domain > myhost.local.40736: [no cksum] 15819 q: AAAA? [www.yahoo.com]("http://www.yahoo.com"). 2/1/0 [www.yahoo.com]("http://www.yahoo.com"). CNAME[|domain]
19:23:20.234267 IP (tos 0x0, ttl 64, id 36685, offset 0, flags [DF], proto UDP (17), length 59)
    myhost.local.60614 > 192.168.1.1.domain: [udp sum ok] 43213+ A? [www.yahoo.com]("http://www.yahoo.com"). (31)
19:23:20.267717 IP (tos 0x0, ttl 250, id 48470, offset 0, flags [DF], proto UDP (17), length 137)
    192.168.1.1.domain > myhost.local.57391: [no cksum] 6006 NXDomain* q: PTR? 100.2.168.192.in-addr.arpa. 0/1/0 ns: 168.192.in-addr.arpa. (109)
19:23:20.268816 IP (tos 0x0, ttl 64, id 36694, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.52828 > 192.168.1.1.domain: [udp sum ok] 20492+ PTR? 1.1.168.192.in-addr.arpa. (42)
19:23:20.270167 IP (tos 0x0, ttl 250, id 1667, offset 0, flags [DF], proto UDP (17), length 139)
    192.168.1.1.domain > myhost.local.60614: [no cksum] 43213 q: A? [www.yahoo.com]("http://www.yahoo.com"). 4/0/0 [www.yahoo.com]("http://www.yahoo.com"). CNAME[|domain]
19:23:20.270558 IP (tos 0x0, ttl 64, id 65473, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [S], cksum 0x1a01 (correct), seq 4002836631, win 5840, options [mss 1460,sackOK,TS val 429910 ecr 0,nop,wscale 6], length 0
19:23:20.305694 IP (tos 0x0, ttl 250, id 48617, offset 0, flags [DF], proto UDP (17), length 135)
    192.168.1.1.domain > myhost.local.52828: [no cksum] 20492 NXDomain* q: PTR? 1.1.168.192.in-addr.arpa. 0/1/0 ns: 168.192.in-addr.arpa. (107)
19:23:20.406620 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.1.168.192.in-addr.arpa. (42)
19:23:20.540743 IP (tos 0x0, ttl 50, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ir1.fp.vip.ac4.yahoo.com.www > myhost.local.33081: Flags [S.], cksum 0x2348 (correct), seq 84890426, ack 4002836632, win 5792, options [mss 1440,sackOK,TS val 4132350033 ecr 429910,nop,wscale 8], length 0
19:23:20.540811 IP (tos 0x0, ttl 64, id 65474, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [.], cksum 0x6801 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 429978 ecr 4132350033], length 0
19:23:20.541024 IP (tos 0x0, ttl 64, id 65475, offset 0, flags [DF], proto TCP (6), length 67
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [P.], seq 1:627, ack 1, win 92, options [nop,nop,TS val 429978 ecr 4132350033], length 626
19:23:20.817608 IP (tos 0x0, ttl 50, id 64101, offset 0, flags [DF], proto TCP (6), length 52)
    ir1.fp.vip.ac4.yahoo.com.www > myhost.local.33081: Flags [.], cksum 0x64bc (correct), seq 1, ack 627, win 28, options [nop,nop,TS val 4132350308 ecr 429978], length 0
19:23:20.841375 IP (tos 0x0, ttl 50, id 64103, offset 0, flags [DF], proto TCP (6), length 717)
    ir1.fp.vip.ac4.yahoo.com.www > myhost.local.33081: Flags [P.], seq 1:666, ack 627, win 28, options [nop,nop,TS val 4132350332 ecr 429978], length 665
19:23:20.841417 IP (tos 0x0, ttl 64, id 65476, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [.], cksum 0x616b (correct), seq 627, ack 666, win 113, options [nop,nop,TS val 430053 ecr 4132350332], length 0
19:23:20.843691 IP (tos 0x0, ttl 64, id 36837, offset 0, flags [DF], proto UDP (17), length 5
    myhost.local.38141 > 192.168.1.1.domain: [udp sum ok] 63162+ AAAA? in.yahoo.com. (30)
19:23:20.880250 IP (tos 0x0, ttl 250, id 2312, offset 0, flags [DF], proto UDP (17), length 17
    192.168.1.1.domain > myhost.local.38141: [no cksum] 63162 q: AAAA? in.yahoo.com. 2/1/0 in.yahoo.com. CNAME[|domain]
19:23:20.880490 IP (tos 0x0, ttl 64, id 36847, offset 0, flags [DF], proto UDP (17), length 5
    myhost.local.43441 > 192.168.1.1.domain: [udp sum ok] 37033+ A? in.yahoo.com. (30)
19:23:20.916456 IP (tos 0x0, ttl 250, id 4026, offset 0, flags [DF], proto UDP (17), length 165)
    192.168.1.1.domain > myhost.local.43441: [no cksum] 37033 q: A? in.yahoo.com. 5/0/0 in.yahoo.com. CNAME[|domain]
19:23:20.916942 IP (tos 0x0, ttl 64, id 13409, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.44495 > ir1.fp.in.yahoo.com.www: Flags [S], cksum 0x730e (correct), seq 4015045529, win 5840, options [mss 1460,sackOK,TS val 430072 ecr 0,nop,wscale 6], length 0
19:23:20.976363 IP (tos 0x0, ttl 54, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ir1.fp.in.yahoo.com.www > myhost.local.44495: Flags [S.], cksum 0xeca7 (correct), seq 2839682391, ack 4015045530, win 5792, options [mss 1440,sackOK,TS val 3939226929 ecr 430072,nop,wscale 8], length 0
19:23:20.976435 IP (tos 0x0, ttl 64, id 13410, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.44495 > ir1.fp.in.yahoo.com.www: Flags [.], cksum 0x3196 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 430087 ecr 3939226929], length 0
19:23:20.976582 IP (tos 0x0, ttl 64, id 13411, offset 0, flags [DF], proto TCP (6), length 470)
    myhost.local.44495 > ir1.fp.in.yahoo.com.www: Flags [P.], seq 1:419, ack 1, win 92, options [nop,nop,TS val 430087 ecr 3939226929], length 418
19:23:21.038516 IP (tos 0x0, ttl 54, id 51251, offset 0, flags [DF], proto TCP (6), length 52)
    ir1.fp.in.yahoo.com.www > myhost.local.44495: Flags [.], cksum 0x2ff6 (correct), seq 1, ack 419, win 27, options [nop,nop,TS val 3939226992 ecr 430087], length 0
19:23:21.068642 IP (tos 0x0, ttl 64, id 20764, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.49295 > 208.43.201.101-static.reverse.softlayer.com.www: Flags [F.], cksum 0x8b30 (correct), seq 0, ack 1, win 92, options [nop,nop,TS val 430110 ecr 2798196495,nop,nop,sack 1 {1443:1444}], length 0
19:23:21.407788 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.1.168.192.in-addr.arpa. (42)
19:23:22.820421 IP (tos 0x0, ttl 64, id 20765, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.49295 > 208.43.201.101-static.reverse.softlayer.com.www: Flags [F.], cksum 0x897a (correct), seq 0, ack 1, win 92, options [nop,nop,TS val 430548 ecr 2798196495,nop,nop,sack 1 {1443:1444}], length 0
19:23:23.410695 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.1.168.192.in-addr.arpa. (42)
19:23:25.308662 IP (tos 0x0, ttl 64, id 37954, offset 0, flags [DF], proto UDP (17), length 72)
    myhost.local.50162 > 192.168.1.1.domain: [udp sum ok] 63107+ PTR? 76.160.195.67.in-addr.arpa. (44)
19:23:25.343665 IP (tos 0x0, ttl 250, id 18410, offset 0, flags [DF], proto UDP (17), length 110)
    192.168.1.1.domain > myhost.local.50162: [no cksum] 63107 q: PTR? 76.160.195.67.in-addr.arpa. 1/0/0 76.160.195.67.in-addr.arpa. (82)
19:23:25.344079 IP (tos 0x0, ttl 64, id 37962, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.35663 > 192.168.1.1.domain: [udp sum ok] 53657+ PTR? 251.0.0.224.in-addr.arpa. (42)
19:23:26.136168 IP (tos 0x0, ttl 250, id 21271, offset 0, flags [DF], proto UDP (17), length 12
    192.168.1.1.domain > myhost.local.35663: [no cksum] 53657 NXDomain q: PTR? 251.0.0.224.in-addr.arpa. 0/1/0 ns: 224.in-addr.arpa. (100)
19:23:26.236815 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
19:23:26.324641 IP (tos 0x0, ttl 64, id 20766, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.49295 > 208.43.201.101-static.reverse.softlayer.com.www: Flags [F.], cksum 0x860e (correct), seq 0, ack 1, win 92, options [nop,nop,TS val 431424 ecr 2798196495,nop,nop,sack 1 {1443:1444}], length 0
19:23:27.238290 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
19:23:29.092697 IP (tos 0x0, ttl 4, id 4356, offset 0, flags [none], proto UDP (17), length 355)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 327
19:23:29.096351 IP (tos 0x0, ttl 4, id 4357, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:29.100049 IP (tos 0x0, ttl 4, id 4358, offset 0, flags [none], proto UDP (17), length 367)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 339
19:23:29.103641 IP (tos 0x0, ttl 4, id 4359, offset 0, flags [none], proto UDP (17), length 361)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 333
19:23:29.106803 IP (tos 0x0, ttl 4, id 4360, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:29.110464 IP (tos 0x0, ttl 4, id 4361, offset 0, flags [none], proto UDP (17), length 373)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 345
19:23:29.113814 IP (tos 0x0, ttl 4, id 4362, offset 0, flags [none], proto UDP (17), length 341)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 313
19:23:29.117496 IP (tos 0x0, ttl 4, id 4363, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:29.120966 IP (tos 0x0, ttl 4, id 4364, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:29.124681 IP (tos 0x0, ttl 4, id 4365, offset 0, flags [none], proto UDP (17), length 365)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 337
19:23:29.127974 IP (tos 0x0, ttl 4, id 4366, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:29.131157 IP (tos 0x0, ttl 4, id 4367, offset 0, flags [none], proto UDP (17), length 293)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 265
19:23:29.241301 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
19:23:30.094748 IP (tos 0x0, ttl 4, id 4368, offset 0, flags [none], proto UDP (17), length 355)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 327
19:23:30.098380 IP (tos 0x0, ttl 4, id 4369, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:30.101992 IP (tos 0x0, ttl 4, id 4370, offset 0, flags [none], proto UDP (17), length 367)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 339
19:23:30.105837 IP (tos 0x0, ttl 4, id 4371, offset 0, flags [none], proto UDP (17), length 361)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 333
19:23:30.108993 IP (tos 0x0, ttl 4, id 4372, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:30.112528 IP (tos 0x0, ttl 4, id 4373, offset 0, flags [none], proto UDP (17), length 373)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 345
19:23:30.119070 IP (tos 0x0, ttl 4, id 4374, offset 0, flags [none], proto UDP (17), length 341)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 313
19:23:30.119078 IP (tos 0x0, ttl 4, id 4375, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:30.122810 IP (tos 0x0, ttl 4, id 4376, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:30.126620 IP (tos 0x0, ttl 4, id 4377, offset 0, flags [none], proto UDP (17), length 365)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 337
19:23:30.129706 IP (tos 0x0, ttl 4, id 4378, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:30.132634 IP (tos 0x0, ttl 4, id 4379, offset 0, flags [none], proto UDP (17), length 293)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 265
19:23:30.772126 IP (tos 0x0, ttl 40, id 27882, offset 0, flags [DF], proto TCP (6), length 52)
    ec2-175-41-132-74.ap-southeast-1.compute.amazonaws.com.www > myhost.local.39711: Flags [R.], cksum 0x6d42 (correct), seq 3303699976, ack 3333954002, win 56, options [nop,nop,TS val 2420986017 ecr 424668], length 0
19:23:31.096642 IP (tos 0x0, ttl 4, id 4380, offset 0, flags [none], proto UDP (17), length 355)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 327
19:23:31.100389 IP (tos 0x0, ttl 4, id 4381, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:31.105471 IP (tos 0x0, ttl 4, id 4382, offset 0, flags [none], proto UDP (17), length 367)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 339
19:23:31.109151 IP (tos 0x0, ttl 4, id 4383, offset 0, flags [none], proto UDP (17), length 361)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 333
19:23:31.112264 IP (tos 0x0, ttl 4, id 4384, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:31.116027 IP (tos 0x0, ttl 4, id 4385, offset 0, flags [none], proto UDP (17), length 373)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 345
19:23:31.119483 IP (tos 0x0, ttl 4, id 4386, offset 0, flags [none], proto UDP (17), length 341)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 313
19:23:31.122872 IP (tos 0x0, ttl 4, id 4387, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:31.126541 IP (tos 0x0, ttl 4, id 4388, offset 0, flags [none], proto UDP (17), length 357)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 329
19:23:31.129934 IP (tos 0x0, ttl 4, id 4389, offset 0, flags [none], proto UDP (17), length 365)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 337
19:23:31.133161 IP (tos 0x0, ttl 4, id 4390, offset 0, flags [none], proto UDP (17), length 302)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 274
19:23:31.136436 IP (tos 0x0, ttl 4, id 4391, offset 0, flags [none], proto UDP (17), length 293)
    192.168.2.1.1900 > 239.255.255.250.1900: UDP, length 265
19:23:31.139383 IP (tos 0x0, ttl 64, id 39411, offset 0, flags [DF], proto UDP (17), length 74)
    myhost.local.39249 > 192.168.1.1.domain: [udp sum ok] 3128+ PTR? 168.152.101.121.in-addr.arpa. (46)
19:23:31.175128 IP (tos 0x0, ttl 250, id 23856, offset 0, flags [DF], proto UDP (17), length 107)
    192.168.1.1.domain > myhost.local.39249: [no cksum] 3128 q: PTR? 168.152.101.121.in-addr.arpa. 1/0/0 168.152.101.121.in-addr.arpa. (79)
19:23:31.175958 IP (tos 0x0, ttl 64, id 39420, offset 0, flags [DF], proto UDP (17), length 74)
    myhost.local.33517 > 192.168.1.1.domain: [udp sum ok] 29341+ PTR? 250.255.255.239.in-addr.arpa. (46)
19:23:31.211701 IP (tos 0x0, ttl 250, id 40627, offset 0, flags [DF], proto UDP (17), length 131)
    192.168.1.1.domain > myhost.local.33517: [no cksum] 29341 NXDomain q: PTR? 250.255.255.239.in-addr.arpa. 0/1/0 ns: 239.in-addr.arpa. (103)
19:23:31.312416 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:23:32.313984 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:23:33.332640 IP (tos 0x0, ttl 64, id 20767, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.49295 > 208.43.201.101-static.reverse.softlayer.com.www: Flags [F.], cksum 0x7f36 (correct), seq 0, ack 1, win 92, options [nop,nop,TS val 433176 ecr 2798196495,nop,nop,sack 1 {1443:1444}], length 0
19:23:34.316108 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:23:35.834834 IP (tos 0x0, ttl 50, id 64105, offset 0, flags [DF], proto TCP (6), length 52)
    ir1.fp.vip.ac4.yahoo.com.www > myhost.local.33081: Flags [F.], cksum 0x272c (correct), seq 666, ack 627, win 28, options [nop,nop,TS val 4132365327 ecr 430053], length 0
19:23:35.872411 IP (tos 0x0, ttl 64, id 65477, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [.], cksum 0x1829 (correct), seq 627, ack 667, win 113, options [nop,nop,TS val 433811 ecr 4132365327], length 0
19:23:36.215002 IP (tos 0x0, ttl 64, id 40680, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.36037 > 192.168.1.1.domain: [udp sum ok] 3992+ PTR? 1.2.168.192.in-addr.arpa. (42)
19:23:36.251699 IP (tos 0x0, ttl 250, id 60729, offset 0, flags [DF], proto UDP (17), length 135)
    192.168.1.1.domain > myhost.local.36037: [no cksum] 3992 NXDomain* q: PTR? 1.2.168.192.in-addr.arpa. 0/1/0 ns: 168.192.in-addr.arpa. (107)
19:23:36.352296 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.2.168.192.in-addr.arpa. (42)
19:23:37.353457 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.2.168.192.in-addr.arpa. (42)
19:23:38.361406 IP (tos 0x0, ttl 64, id 13412, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.44495 > ir1.fp.in.yahoo.com.www: Flags [F.], cksum 0x1eba (correct), seq 419, ack 1, win 92, options [nop,nop,TS val 434433 ecr 3939226992], length 0
19:23:38.361983 IP (tos 0x0, ttl 64, id 41217, offset 0, flags [DF], proto UDP (17), length 66)
    myhost.local.48971 > 192.168.1.1.domain: [udp sum ok] 9428+ AAAA? [www.businessweek.com]("http://www.businessweek.com"). (38)
19:23:38.398424 IP (tos 0x0, ttl 250, id 7720, offset 0, flags [DF], proto UDP (17), length 200)
    192.168.1.1.domain > myhost.local.48971: [no cksum] 9428 q: AAAA? [www.businessweek.com]("http://www.businessweek.com"). 2/1/0 [www.businessweek.com]("http://www.businessweek.com").[|domain]
19:23:38.398601 IP (tos 0x0, ttl 64, id 41226, offset 0, flags [DF], proto UDP (17), length 66)
    myhost.local.34938 > 192.168.1.1.domain: [udp sum ok] 16591+ A? [www.businessweek.com]("http://www.businessweek.com"). (3
19:23:38.419673 IP (tos 0x0, ttl 54, id 51269, offset 0, flags [DF], proto TCP (6), length 52)
    ir1.fp.in.yahoo.com.www > myhost.local.44495: Flags [.], cksum 0xcfd0 (correct), seq 2885, ack 420, win 27, options [nop,nop,TS val 3939244374 ecr 434433], length 0
19:23:38.433815 IP (tos 0x0, ttl 250, id 49794, offset 0, flags [DF], proto UDP (17), length 174)
    192.168.1.1.domain > myhost.local.34938: [no cksum] 16591 q: A? [www.businessweek.com]("http://www.businessweek.com"). 4/0/0 [www.businessweek.com]("http://www.businessweek.com").[|domain]
19:23:38.434163 IP (tos 0x0, ttl 64, id 7973, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.55178 > ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0xdb9a (correct), seq 4288790070, win 5840, options [mss 1460,sackOK,TS val 434451 ecr 0,nop,wscale 6], length 0
19:23:38.469352 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www > myhost.local.55178: Flags [S.], cksum 0x3a4e (correct), seq 3962599181, ack 4288790071, win 5792, options [mss 1460,sackOK,TS val 2459347863 ecr 434451,nop,wscale 5], length 0
19:23:38.469413 IP (tos 0x0, ttl 64, id 7974, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.55178 > ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x7f53 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434460 ecr 2459347863], length 0
19:23:38.469547 IP (tos 0x0, ttl 64, id 7975, offset 0, flags [DF], proto TCP (6), length 439)
    myhost.local.55178 > ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:388, ack 1, win 92, options [nop,nop,TS val 434460 ecr 2459347863], length 387
19:23:38.505571 IP (tos 0x0, ttl 58, id 56503, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www > myhost.local.55178: Flags [.], cksum 0x7d2f (correct), seq 1, ack 388, win 215, options [nop,nop,TS val 2459347901 ecr 434460], length 0
19:23:38.877791 IP (tos 0x0, ttl 58, id 56504, offset 0, flags [DF], proto TCP (6), length 145
    ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www > myhost.local.55178: Flags [P.], seq 1:1407, ack 388, win 215, options [nop,nop,TS val 2459348267 ecr 434460], length 1406
19:23:38.877843 IP (tos 0x0, ttl 64, id 7976, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.55178 > ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x762c (correct), seq 388, ack 1407, win 136, options [nop,nop,TS val 434562 ecr 2459348267], length 0
19:23:38.890932 IP (tos 0x0, ttl 64, id 41349, offset 0, flags [DF], proto UDP (17), length 69)
    myhost.local.39107 > 192.168.1.1.domain: [udp sum ok] 12078+ AAAA? assets.businessweek.com. (41)
19:23:38.911891 IP (tos 0x0, ttl 58, id 56510, offset 0, flags [DF], proto TCP (6), length 82)
    ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www > myhost.local.55178: Flags [P.], seq 8617:8647, ack 388, win 215, options [nop,nop,TS val 2459348306 ecr 434562], length 30
19:23:38.911909 IP (tos 0x0, ttl 64, id 7977, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.55178 > ABTS-KK-Static-010.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x3620 (correct), seq 388, ack 1407, win 136, options [nop,nop,TS val 434570 ecr 2459348267,nop,nop,sack 1 {8617:8647}], length 0
19:23:38.926603 IP (tos 0x0, ttl 250, id 5273, offset 0, flags [DF], proto UDP (17), length 206)
    192.168.1.1.domain > myhost.local.39107: [no cksum] 12078 q: AAAA? assets.businessweek.com. 2/1/0 assets.businessweek.com.[|domain]
19:23:38.926743 IP (tos 0x0, ttl 64, id 41358, offset 0, flags [DF], proto UDP (17), length 69)
    myhost.local.54787 > 192.168.1.1.domain: [udp sum ok] 19838+ A? assets.businessweek.com. (41)
19:23:38.962123 IP (tos 0x0, ttl 250, id 10096, offset 0, flags [DF], proto UDP (17), length 180)
    192.168.1.1.domain > myhost.local.54787: [no cksum] 19838 q: A? assets.businessweek.com. 4/0/0 assets.businessweek.com.[|domain]
19:23:38.962579 IP (tos 0x0, ttl 64, id 6294, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37813 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0x2462 (correct), seq 4283939073, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.962705 IP (tos 0x0, ttl 64, id 23397, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37814 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0xe261 (correct), seq 4284873458, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.962776 IP (tos 0x0, ttl 64, id 54135, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37815 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0x6a15 (correct), seq 4290999008, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.962848 IP (tos 0x0, ttl 64, id 42193, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37816 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0xd74f (correct), seq 2295110, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.962954 IP (tos 0x0, ttl 64, id 51835, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37817 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0x710c (correct), seq 4290669548, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.963026 IP (tos 0x0, ttl 64, id 24062, offset 0, flags [DF], proto TCP (6), length 60)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [S], cksum 0xe04b (correct), seq 130153, win 5840, options [mss 1460,sackOK,TS val 434583 ecr 0,nop,wscale 6], length 0
19:23:38.998842 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37813: Flags [S.], cksum 0xaa0e (correct), seq 1379024974, ack 4283939074, win 5792, options [mss 1460,sackOK,TS val 1337694263 ecr 434583,nop,wscale 5], length 0
19:23:38.998913 IP (tos 0x0, ttl 64, id 6295, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37813 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0xef13 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434592 ecr 1337694263], length 0
19:23:38.999101 IP (tos 0x0, ttl 64, id 6296, offset 0, flags [DF], proto TCP (6), length 450)
    myhost.local.37813 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:399, ack 1, win 92, options [nop,nop,TS val 434592 ecr 1337694263], length 398
19:23:38.999634 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37814: Flags [S.], cksum 0x92ef (correct), seq 1364268621, ack 4284873459, win 5792, options [mss 1460,sackOK,TS val 1337694264 ecr 434583,nop,wscale 5], length 0
19:23:38.999678 IP (tos 0x0, ttl 64, id 23398, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37814 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0xd7f4 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434592 ecr 1337694264], length 0
19:23:38.999751 IP (tos 0x0, ttl 64, id 23399, offset 0, flags [DF], proto TCP (6), length 452)
    myhost.local.37814 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:401, ack 1, win 92, options [nop,nop,TS val 434592 ecr 1337694264], length 400
19:23:39.000539 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37815: Flags [S.], cksum 0xed4b (correct), seq 1371292472, ack 4290999009, win 5792, options [mss 1460,sackOK,TS val 1337694265 ecr 434583,nop,wscale 5], length 0
19:23:39.000564 IP (tos 0x0, ttl 64, id 54136, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37815 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x3250 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694265], length 0
19:23:39.000645 IP (tos 0x0, ttl 64, id 54137, offset 0, flags [DF], proto TCP (6), length 429)
    myhost.local.37815 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:378, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694265], length 377
19:23:39.001867 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37816: Flags [S.], cksum 0x2795 (correct), seq 1378055617, ack 2295111, win 5792, options [mss 1460,sackOK,TS val 1337694266 ecr 434583,nop,wscale 5], length 0
19:23:39.001888 IP (tos 0x0, ttl 64, id 42194, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37816 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x6c99 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694266], length 0
19:23:39.001966 IP (tos 0x0, ttl 64, id 42195, offset 0, flags [DF], proto TCP (6), length 444)
    myhost.local.37816 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:393, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694266], length 392
19:23:39.002713 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37817: Flags [S.], cksum 0xe160 (correct), seq 1365268083, ack 4290669549, win 5792, options [mss 1460,sackOK,TS val 1337694268 ecr 434583,nop,wscale 5], length 0
19:23:39.002741 IP (tos 0x0, ttl 64, id 51836, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37817 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x2665 (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694268], length 0
19:23:39.002940 IP (tos 0x0, ttl 64, id 51837, offset 0, flags [DF], proto TCP (6), length 465)
    myhost.local.37817 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:414, ack 1, win 92, options [nop,nop,TS val 434593 ecr 1337694268], length 413
19:23:39.006254 IP (tos 0x0, ttl 58, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37818: Flags [S.], cksum 0x14a7 (correct), seq 1364890225, ack 130154, win 5792, options [mss 1460,sackOK,TS val 1337694269 ecr 434583,nop,wscale 5], length 0
19:23:39.006281 IP (tos 0x0, ttl 64, id 24063, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x59aa (correct), seq 1, ack 1, win 92, options [nop,nop,TS val 434594 ecr 1337694269], length 0
19:23:39.007157 IP (tos 0x0, ttl 64, id 24064, offset 0, flags [DF], proto TCP (6), length 460)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 1:409, ack 1, win 92, options [nop,nop,TS val 434594 ecr 1337694269], length 408
19:23:39.037287 IP (tos 0x0, ttl 58, id 55318, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37813: Flags [.], cksum 0xece2 (correct), seq 1, ack 399, win 215, options [nop,nop,TS val 1337694303 ecr 434592], length 0
19:23:39.043623 IP (tos 0x0, ttl 58, id 36398, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37814: Flags [.], cksum 0xd5bc (correct), seq 1, ack 401, win 215, options [nop,nop,TS val 1337694309 ecr 434592], length 0
19:23:39.047803 IP (tos 0x0, ttl 58, id 56156, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37815: Flags [.], cksum 0x302b (correct), seq 1, ack 378, win 215, options [nop,nop,TS val 1337694314 ecr 434593], length 0
19:23:39.052758 IP (tos 0x0, ttl 58, id 60840, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37816: Flags [.], cksum 0x6a61 (correct), seq 1, ack 393, win 215, options [nop,nop,TS val 1337694319 ecr 434593], length 0
19:23:39.058858 IP (tos 0x0, ttl 58, id 52740, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37817: Flags [.], cksum 0x2414 (correct), seq 1, ack 414, win 215, options [nop,nop,TS val 1337694325 ecr 434593], length 0
19:23:39.064082 IP (tos 0x0, ttl 58, id 2567, offset 0, flags [DF], proto TCP (6), length 52)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37818: Flags [.], cksum 0x575a (correct), seq 1, ack 409, win 215, options [nop,nop,TS val 1337694330 ecr 434594], length 0
19:23:39.068422 IP (tos 0x0, ttl 58, id 2568, offset 0, flags [DF], proto TCP (6), length 921)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37818: Flags [P.], seq 1:870, ack 409, win 215, options [nop,nop,TS val 1337694330 ecr 434594], length 869
19:23:39.068451 IP (tos 0x0, ttl 64, id 24065, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x5445 (correct), seq 409, ack 870, win 119, options [nop,nop,TS val 434610 ecr 1337694330], length 0
19:23:39.068720 IP (tos 0x0, ttl 64, id 24066, offset 0, flags [DF], proto TCP (6), length 435)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [P.], seq 409:792, ack 870, win 119, options [nop,nop,TS val 434610 ecr 1337694330], length 383
19:23:39.108239 IP (tos 0x0, ttl 58, id 2571, offset 0, flags [DF], proto TCP (6), length 885)
    ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www > myhost.local.37818: Flags [P.], seq 3754:4587, ack 792, win 248, options [nop,nop,TS val 1337694371 ecr 434610], length 833
19:23:39.108280 IP (tos 0x0, ttl 64, id 24067, offset 0, flags [DF], proto TCP (6), length 64)
    myhost.local.37818 > ABTS-KK-Static-019.225.178.122.airtelbroadband.in.www: Flags [.], cksum 0x3479 (correct), seq 792, ack 870, win 119, options [nop,nop,TS val 434619 ecr 1337694330,nop,nop,sack 1 {3754:4587}], length 0
19:23:39.354419 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70)
    myhost.local.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 1.2.168.192.in-addr.arpa. (42)
19:23:41.255616 IP (tos 0x0, ttl 64, id 41940, offset 0, flags [DF], proto UDP (17), length 72)
    myhost.local.51694 > 192.168.1.1.domain: [udp sum ok] 34870+ PTR? 74.132.41.175.in-addr.arpa. (44)
19:23:41.559005 IP (tos 0x0, ttl 250, id 61193, offset 0, flags [DF], proto UDP (17), length 140)
    192.168.1.1.domain > myhost.local.51694: [no cksum] 34870 q: PTR? 74.132.41.175.in-addr.arpa. 1/0/0 74.132.41.175.in-addr.arpa. (112)
19:23:41.560031 IP (tos 0x0, ttl 64, id 42016, offset 0, flags [DF], proto UDP (17), length 73)
    myhost.local.59364 > 192.168.1.1.domain: [udp sum ok] 63741+ PTR? 10.225.178.122.in-addr.arpa. (45)
19:23:41.596173 IP (tos 0x0, ttl 250, id 56144, offset 0, flags [DF], proto UDP (17), length 136)
    192.168.1.1.domain > myhost.local.59364: [no cksum] 63741 q: PTR? 10.225.178.122.in-addr.arpa. 1/0/0 10.225.178.122.in-addr.arpa. (108)
19:23:41.596871 IP (tos 0x0, ttl 64, id 42026, offset 0, flags [DF], proto UDP (17), length 73)
    myhost.local.39802 > 192.168.1.1.domain: [udp sum ok] 64766+ PTR? 19.225.178.122.in-addr.arpa. (45)
19:23:41.632170 IP (tos 0x0, ttl 250, id 61453, offset 0, flags [DF], proto UDP (17), length 136)
    192.168.1.1.domain > myhost.local.39802: [no cksum] 64766 q: PTR? 19.225.178.122.in-addr.arpa. 1/0/0 19.225.178.122.in-addr.arpa. (10
19:23:43.509897 IP (tos 0x0, ttl 1, id 40, offset 0, flags [none], proto IGMP (2), length 2
    192.168.2.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
19:23:43.510235 IP (tos 0x0, ttl 64, id 42504, offset 0, flags [DF], proto UDP (17), length 6
    myhost.local.45263 > 192.168.1.1.domain: [udp sum ok] 15313+ PTR? 1.0.0.224.in-addr.arpa. (40)
19:23:43.510537 IP (tos 0x0, ttl 1, id 41, offset 0, flags [none], proto IGMP (2), length 2
    192.168.2.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
19:23:43.546306 IP (tos 0x0, ttl 250, id 63504, offset 0, flags [DF], proto UDP (17), length 103)
    192.168.1.1.domain > myhost.local.45263: [no cksum] 15313 q: PTR? 1.0.0.224.in-addr.arpa. 1/0/0 1.0.0.224.in-addr.arpa. (75)
19:23:43.983183 IP (tos 0x0, ttl 64, id 65478, offset 0, flags [DF], proto TCP (6), length 52)
    myhost.local.33081 > ir1.fp.vip.ac4.yahoo.com.www: Flags [F.], cksum 0x103d (correct), seq 627, ack 667, win 113, options [nop,nop,TS val 435838 ecr 4132365327], length 0
19:23:44.252200 IP (tos 0x0, ttl 50, id 0, offset 0, flags [DF], proto TCP (6), length 52)
    ir1.fp.vip.ac4.yahoo.com.www > myhost.local.33081: Flags [.], cksum 0xefb0 (correct), seq 667, ack 628, win 28, options [nop,nop,TS val 4132373744 ecr 435838], length 0

---

### Post by grahammechanical on 2010-09-25
There is a Wireless Trouble Shooting Guide. It says this:

>  5.2. connected, Issues with Certain Websites       Disable IPV6. 

Right click network manager icon . Edit Connections.

Hope this helps       regards

---

