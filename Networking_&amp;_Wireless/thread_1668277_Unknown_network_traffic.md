---
title: "Unknown network traffic"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by ondrokm on 2011-01-16
Hi
A few minutes ago I noticed a huge data transfer to my computer. I wasn't downloading anything big, I have just opened Firefox, Thunderbird etc. It stopped after a minute but I'd like to know, what that was - this wasn't the first time something like this happened.
I promptly started Wireshark and captured a few packets, all of them look like this:
```

No.     Time        Source                Destination           Protocol Info
      6 0.008106    AskeyCom_0b:1a:e9     HonHaiPr_13:92:09     0x05f0   Ethernet II

Frame 6 (1534 bytes on wire, 1534 bytes captured)
    Arrival Time: Jan 16, 2011 11:45:56.478165000
    [Time delta from previous captured frame: 0.001543000 seconds]
    [Time delta from previous displayed frame: 0.001543000 seconds]
    [Time since reference or first frame: 0.008106000 seconds]
    Frame Number: 6
    Frame Length: 1534 bytes
    Capture Length: 1534 bytes
    [Frame is marked: True]
    [Protocols in frame: eth:data]
Ethernet II, Src: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9), Dst: HonHaiPr_13:92:09 (00:22:69:13:92:09)
    Destination: HonHaiPr_13:92:09 (00:22:69:13:92:09)
        Address: HonHaiPr_13:92:09 (00:22:69:13:92:09)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9)
        Address: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: Unknown (0x05f0)
Data (1520 bytes)
```
I tried to look at askey.com, but that webpage does not work.
Does anyone have an idea what the traffic might be caused by? Couldn't anyone hacked my pc?
Thank you

---

### Post by gmargo on 2011-01-16
> 
Ethernet II, Src: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9), Dst: HonHaiPr_13:92:09 (00:22:69:13:92:09)
These are MAC addresses for local endpoints on your network. 'AskeyCom' and 'HonHaiPr' are manufacturer ids for ethernet chips.  

Here's the manufacturer info for those two MAC addresses.  You can look these up on this IEEE site: [http://standards.ieee.org/develop/regauth/oui/public.html](http://standards.ieee.org/develop/regauth/oui/public.html)

```

E8-39-DF   (hex)                Askey Computer
E839DF     (base 16)            Askey Computer
                                10F,NO.119,CHIENKANG RD,CHUNG-HO,
                                TAIPEI 235
                                TAIWAN, REPUBLIC OF CHINA

00-22-69   (hex)                Hon Hai Precision Ind. Co., Ltd.
002269     (base 16)            Hon Hai Precision Ind. Co., Ltd.
                                66, Chung Shan Rd.Tu-Cheng
                                Taipei Hsien  236
                                TAIWAN, REPUBLIC OF CHINA

```My point is that there is no need to suspect Askey of anything.  They just made the chip.

What is strange is the protocol 0x05f0 that wireshark can't decode.  For a normal IP packet that protocol should be 0x0800 (for IPv4) or 0x86dd (for IPv6).

Since presumably those ethernet chips also pass IP traffic, you could check the arp cache to identify which machines on your network are talking.  That data is strange, but if it's not IP-based then it's not going out to the internet.  Perhaps the sender chip is malfunctioning?  Is it always one sender or do they seem to be exchanging messages on that protocol?

Here's the official list of ethernet types, and 0x05f0 is not on the list: [http://www.iana.org/assignments/ethernet-numbers](http://www.iana.org/assignments/ethernet-numbers)

---

### Post by ondrokm on 2011-01-16
Every time this traffic appears (few times a day, every time about 40MB is downloaded - 200kBps for about 3 minutes, 150kBps longer) I capture a lot of those packets, about 160 per second. Usually when there is no traffic in network monitor, wireshark captures more then ten time less of similar packets.
I haven't noticed any other difference between ordinary and this strange network behavior. All of that packets are similar. The source and destination is always the same, protocol and description differs
```

54    5.443965    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    0x05f0    Ethernet II
55    5.453273    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    0x05f0    Ethernet II
56    5.454463    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    I, N(R)=16, N(S)=86; DSAP 0x72 Group, SSAP 0x72 Response
57    5.537942    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    S, func=SREJ, N(R)=16; DSAP 0x72 Group, SSAP 0x72 Response
58    5.540801    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    0x05f0    Ethernet II
59    5.542391    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    0x05f0    Ethernet II
60    5.543553    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    I, N(R)=16, N(S)=88; DSAP 0x72 Group, SSAP 0x72 Response
61    5.544024    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    S, func=RR, N(R)=16; DSAP 0x72 Group, SSAP 0x72 Response
62    5.547819    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    I, N(R)=16, N(S)=89; DSAP 0x72 Group, SSAP 0x72 Response
63    5.550040    AskeyCom_0b:1a:e9    HonHaiPr_de:77:09    LLC    U F, func=Unknown; DSAP 0x72 Group, SSAP 0x72 Response

```When I saw this huge traffic I closed all of the internet programs but it didn't stop. There shouldn't have been any updating in progress or samba or ssh connection at time. I turned off almost everything but it didn't help. I have blocked all of the incoming connections so it must be caused by some of my programs.

Another thing is, I see a strange alive connections in Firestarter. For example:
```

mu-in.f138.1e100.net (209.85.135.138) - HTTP, 80
ncc.subsignal.org (188.40.166.25) - HTTP, 80
87-98-136-30.kamsufi.com (87.98.136.30) - HTTP, 80
```

There are about 10-15 similar. This I see after firefox is turned off; these might by some alive connections but I haven't visited any of that sites and if I try it (that web page or ping it) the server is unreachable so there probably isn't any external content from previously visited pages.

I have no idea if those strange alive connections have something to do with the huge unknown network traffic :-(
What the traffic might be caused by? Is there a way how to block it?

---

### Post by ondrokm on 2011-01-16
same post send three times because server wasn't responding

---

### Post by ondrokm on 2011-01-16
same post send three times because server wasn't responding

---

### Post by gmargo on 2011-01-16
Can you identify which of your devices has this "AskeyCom_0b:1a:e9" MAC address?  Honestly, I think you have some bad hardware.

---

### Post by ondrokm on 2011-01-17
Edit: It is my router: Huawei EchoLife HG520i
```

$ arp -a
? (192.168.100.199) at e8:39:df:0b:1a:e9 [ether] on wlan0

```

---

### Post by kistenyer on 2011-01-18
would you copy some packets here? 

i am interested in this problem :):popcorn:

---

### Post by ondrokm on 2011-01-18
Here is the same packet I pasted above:
```

No.     Time        Source                Destination           Protocol Info
      6 0.008106    AskeyCom_0b:1a:e9     HonHaiPr_13:92:09     0x05f0   Ethernet II

Frame 6 (1534 bytes on wire, 1534 bytes captured)
    Arrival Time: Jan 16, 2011 11:45:56.478165000
    [Time delta from previous captured frame: 0.001543000 seconds]
    [Time delta from previous displayed frame: 0.001543000 seconds]
    [Time since reference or first frame: 0.008106000 seconds]
    Frame Number: 6
    Frame Length: 1534 bytes
    Capture Length: 1534 bytes
    [Frame is marked: True]
    [Protocols in frame: eth:data]
Ethernet II, Src: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9), Dst: HonHaiPr_13:92:09 (00:22:69:13:92:09)
    Destination: HonHaiPr_13:92:09 (00:22:69:13:92:09)
        Address: HonHaiPr_13:92:09 (00:22:69:13:92:09)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9)
        Address: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: Unknown (0x05f0)
Data (1520 bytes)

0000  07 27 44 20 06 00 00 00 85 95 26 7c ff 63 2f 18   .'D ......&|.c/.
0010  5e af c2 01 8c 1e 03 af f5 ba e5 4f a3 d5 ce b6   ^..........O....
0020  23 42 fc c4 09 6f c0 e7 aa 9d 94 94 54 5a 57 88   #B...o......TZW.
0030  27 e7 a3 cf fa ae 99 cc c2 96 e9 fd 9d 92 56 d6   '.............V.
0040  b3 4d 2e 19 f7 17 88 f3 03 2c e8 54 d7 19 3e a9   .M.......,.T..>.
0050  8f 99 df 68 89 96 64 12 9c 65 91 aa a0 f5 a0 fe   ...h..d..e......
0060  5c 37 40 c7 78 76 2b 9a c8 32 fb 65 40 26 59 40   \7@.xv+..2.e@&Y@
0070  54 cc 49 23 c1 14 0a 52 f5 b3 6d 38 50 78 5a 27   T.I#...R..m8PxZ'
0080  91 19 b5 e9 5b 78 16 07 c8 65 18 30 7a 8d 74 c5   ....[x...e.0z.t.
0090  e8 68 4b 89 7c 4a ad f0 a6 b4 24 46 6b 59 52 a5   .hK.|J....$FkYR.
00a0  8a 5f 5d 15 56 a5 8b 67 c1 2e ad 2a 94 89 6d 3a   ._].V..g...*..m:
00b0  97 48 aa 09 06 16 54 ea 0e 6b 9d a2 0b 70 81 94   .H....T..k...p..
00c0  5c 45 23 e3 25 bf 6c 17 4f 14 79 f6 8f 5f 7e 48   \E#.%.l.O.y.._~H
00d0  33 4c a5 2f 9c 85 45 f5 20 86 23 f1 40 4b 00 a3   3L./..E. .#.@K..
00e0  aa b8 53 5f 30 1f db ed ea 72 f0 7e 3d 20 48 f3   ..S_0....r.~= H.
00f0  66 5e f4 1a e3 8e f4 0f 34 41 6c 84 98 5b 47 ca   f^......4Al..[G.
0100  d8 4a 8b b3 62 f8 dd 50 ae 0c 88 bd 6a 11 ad 6f   .J..b..P....j..o
0110  f5 e6 8b c7 37 93 62 81 45 ea 9b 5a f6 c0 f4 82   ....7.b.E..Z....
0120  07 00 68 2e f9 64 2d 63 7a 2d 94 3c 91 06 09 f8   ..h..d-cz-.<....
0130  f4 09 7d a1 78 19 17 1f e1 1e 2d 7c 8c 7a b0 39   ..}.x.....-|.z.9
0140  4f 01 31 9a 14 4a 7b 42 34 bb a0 2e d1 b2 ab 40   O.1..J{B4......@
0150  0c 2f c4 56 95 8a 0e 61 a5 dc 37 d1 e6 f6 4a 81   ./.V...a..7...J.
0160  13 f4 db 38 c7 3d cf 84 04 1a 7a 21 6b ce c0 60   ...8.=....z!k..`
0170  da 3d 79 7f f1 c7 3a e4 3e 83 17 68 75 84 5c 12   .=y...:.>..hu.\.
0180  fa 8c 08 c4 dc 5a 40 e7 7d e5 ec fb 94 63 91 28   .....Z@.}....c.(
0190  90 fc 05 87 6f 68 b9 59 e5 ce 6e 57 c3 dc 51 9f   ....oh.Y..nW..Q.
01a0  81 96 a6 4d b4 de 98 32 5c 33 77 7e c8 fe 21 ad   ...M...2\3w~..!.
01b0  29 0a 70 83 10 90 e6 0a a9 15 3e ca dd a4 75 eb   ).p.......>...u.
01c0  a0 fa 46 17 75 2e 10 fc 3e e5 b2 9e 04 43 07 23   ..F.u...>....C.#
01d0  12 f5 4d d0 d2 aa b8 50 ee c0 1e 99 3b 30 38 b2   ..M....P....;08.
01e0  02 77 2c b7 38 68 8b 1d c2 0e d0 ac 27 13 5d b8   .w,.8h......'.].
01f0  c4 22 74 5d 1d c3 fa db a4 0c 4f 9e dd 5a 52 d4   ."t]......O..ZR.
0200  a8 9d fe 63 74 70 7c 8c 82 16 59 1d cf e8 a5 b6   ...ctp|...Y.....
0210  21 ec b3 99 35 a3 09 04 a5 b7 2c f6 72 49 c8 00   !...5.....,.rI..
0220  da d4 93 08 f9 d7 4f e9 24 84 dd db fb 80 fd ce   ......O.$.......
0230  94 98 37 ef 84 85 02 ea b2 95 b4 76 91 96 07 9e   ..7........v....
0240  49 bd 00 ed 1f 85 9a 51 e1 40 67 e4 55 32 7c a9   I......Q.@g.U2|.
0250  88 ea 3e 33 62 fc 3f cf 7e 28 b0 74 17 fb 95 93   ..>3b.?.~(.t....
0260  89 ac 2c 7c 3c 34 27 78 0a fd 34 22 3e 9d ae 80   ..,|<4'x..4">...
0270  f7 34 35 e6 cf 9d 67 5e b0 f5 83 88 5a 3e 35 60   .45...g^....Z>5`
0280  5c 2e 3e e9 76 f3 dd c1 e1 1a fb 23 6f 84 a3 48   \.>.v......#o..H
0290  08 57 c9 f6 55 11 db e4 1d 23 07 ae ce 48 cc 44   .W..U....#...H.D
02a0  0e 82 b0 cb 49 3f 20 dd 40 6c 09 7a 52 0b 8c 5d   ....I? .@l.zR..]
02b0  3c 34 41 c3 ed cb ad 17 27 81 a3 92 9b a8 e8 08   <4A.....'.......
02c0  54 4f 82 40 04 99 0b 53 cb af ec 8f 9b 7e 90 95   TO.@...S.....~..
02d0  54 4e 90 33 e7 04 09 85 46 4b 6a a9 f1 ac 67 77   TN.3....FKj...gw
02e0  5e 3c b6 da d0 93 be e5 a3 90 47 d3 5d bc 85 65   ^<........G.]..e
02f0  3d 60 96 b1 25 61 8a ee 37 ac 09 9b e5 84 05 2e   =`..%a..7.......
0300  7d a4 e1 e9 33 ed 99 ec c5 bb ae d3 68 4f 1f 3f   }...3.......hO.?
0310  a0 c4 f9 5a 69 32 3b 38 7f 66 ea b5 7c 8d f6 a9   ...Zi2;8.f..|...
0320  75 81 ba 39 b5 61 b4 b4 81 95 db fa 1c 87 66 2e   u..9.a........f.
0330  1f 65 a2 15 02 0d c0 7b 0f 0e 89 6e b5 d6 72 4e   .e.....{...n..rN
0340  1a 42 d7 73 87 42 0c d4 9b aa ac 1d 40 d6 6f 56   .B.s.B......@.oV
0350  b4 ab be ed 87 6e b6 4d b9 8c 98 6e 71 d9 3e 5d   .....n.M...nq.>]
0360  50 c0 e1 ea e8 73 78 3d 48 1f ec b4 7a f9 2b 75   P....sx=H...z.+u
0370  a4 97 0e 30 71 c6 1f e1 8b 8d 10 42 6c a6 57 da   ...0q......Bl.W.
0380  6c 72 8a 6b 31 3a 19 e2 2e 44 61 07 3c 2e a1 ce   lr.k1:...Da.<...
0390  a4 fa c2 20 a7 d8 72 aa d5 17 2c 47 14 39 43 25   ... ..r...,G.9C%
03a0  f6 d0 90 73 2e 96 d3 69 db 74 51 29 c4 ac 1c 30   ...s...i.tQ)...0
03b0  f9 22 8f ee d3 90 0f 04 d9 47 fb 0b 42 41 e7 91   .".......G..BA..
03c0  97 88 a1 97 90 f2 f5 71 0e ee 25 84 5c eb 86 07   .......q..%.\...
03d0  57 ff 07 97 a4 3d 29 57 f6 bb ed 0f 42 c0 31 04   W....=)W....B.1.
03e0  72 9c 40 ae 4f 53 71 f1 63 9c ef ba 5c 4c 02 25   r.@.OSq.c...\L.%
03f0  30 6f c2 1f 7a 5d 0e 14 79 02 73 df 9f 61 cb e3   0o..z]..y.s..a..
0400  15 1d 80 be ce 9a bf cf 43 21 4f ce 49 2f d7 27   ........C!O.I/.'
0410  28 3d 74 3c d8 6a a0 64 2e ee 69 6c f2 a8 63 5f   (=t<.j.d..il..c_
0420  fa a8 53 72 a8 db 07 6a f7 6f 9a 41 05 63 3b 82   ..Sr...j.o.A.c;.
0430  7f 10 66 fc 11 71 8a 3f f2 14 a5 3d 5f 53 4a 53   ..f..q.?...=_SJS
0440  34 5a 75 4d 49 64 c2 45 b7 5c 86 96 24 98 fe 96   4ZuMId.E.\..$...
0450  01 c8 3b 2d 69 cb 3c 23 28 6c 5e 33 3c 87 f7 06   ..;-i.<#(l^3<...
0460  67 93 75 c5 d9 63 91 3e 58 3a b9 65 d0 ee 72 14   g.u..c.>X:.e..r.
0470  11 5c aa 90 2f 1d ed fb 67 68 b7 be 0b 46 a7 f5   .\../...gh...F..
0480  6c 15 75 8f af e2 aa 2e 9d 6c 40 0b 62 0d 03 c7   l.u......l@.b...
0490  4f f0 0b 75 30 84 9b 67 81 ae c5 b4 56 2b c2 bf   O..u0..g....V+..
04a0  b8 21 0b 18 47 39 63 01 18 87 27 1d 15 4f 50 1a   .!..G9c...'..OP.
04b0  49 ce 47 5d 10 cf 92 95 1b 33 3d 0c 7c e2 48 a7   I.G].....3=.|.H.
04c0  0a cc ec 36 22 d4 a3 db bd 5c ce ae 5a 01 c4 5c   ...6"....\..Z..\
04d0  81 f3 59 bc e9 40 2c 66 d2 3a 76 30 91 42 50 24   ..Y..@,f.:v0.BP$
04e0  cf 53 5a e1 19 e1 5c 35 82 4e f6 34 d1 84 ef 9c   .SZ...\5.N.4....
04f0  39 f2 96 f9 f2 62 86 9a 07 82 e2 f9 5d 75 57 e8   9....b......]uW.
0500  fb 77 b9 9b 43 e8 ad 50 b8 59 7e 28 e7 2b ac 52   .w..C..P.Y~(.+.R
0510  9c e6 c5 a0 f3 bd 7f 4b 7c 5f 5f 86 b5 1a 83 60   .......K|__....`
0520  51 76 22 af eb 98 bb bf b4 cb 26 c7 eb 54 b4 ef   Qv".......&..T..
0530  7d 84 65 9c ce b6 15 75 19 16 0e 5d 8b 67 f8 44   }.e....u...].g.D
0540  db c2 8d e6 a3 8a 50 92 77 4f 4a f9 be cc a5 87   ......P.wOJ.....
0550  bf 4d 68 65 ce 56 4c 41 4e 8f 0e dc d5 1f af 39   .Mhe.VLAN......9
0560  18 ff 63 ec b7 51 80 3a c1 c2 a3 80 ad a1 91 eb   ..c..Q.:........
0570  26 49 e1 d9 84 25 d4 81 e7 12 33 ce 56 e9 56 16   &I...%....3.V.V.
0580  56 14 10 70 96 a9 9c b5 cf 18 17 ef b0 35 30 42   V..p.........50B
0590  b0 cd f9 1b 5f 98 cd 47 96 30 78 d4 da ba 2f b9   ...._..G.0x.../.
05a0  09 73 27 78 e0 26 b0 9c ca c7 19 8b 82 78 79 c8   .s'x.&.......xy.
05b0  4e 70 48 b9 2d c4 78 cb ab 46 c9 6a 41 38 ed d9   NpH.-.x..F.jA8..
05c0  d3 76 41 ac 3e 6d 17 60 17 9a 0e 4a 63 36 bb 77   .vA.>m.`...Jc6.w
05d0  27 79 0d bb 60 cb 9c e1 23 67 b7 c1 fa 64 2c e9   'y..`...#g...d,.
05e0  c5 d4 e8 1f ae 27 0a 5c 6c b8 e0 a3 35 81 d9 36   .....'.\l...5..6
    Data: 07274420060000008595267CFF632F185EAFC2018C1E03AF...
    [Length: 1520]

```**kistenyer**: Is that what you wanted?

Now I'm "observing" it again. It had started about 40 minutes ago and hasn't stopped yet.
What is interesting, System Monitor and Etherape give me different data, see attachment. According to System monitor the download was 300kBps for 2.5 minutes so more than 40MB should have been transfered, but etherape shows the sum of accumulated traffic (also 2.5m) about 1MB ... Isn't it strange?

---

### Post by hansolo4949 on 2011-01-18
Do you have any other computers on the network? if you do, check each one and see if they have one of the specified ethernet cards. If none of them do...I think you may have a hacker. Is this activity happening when all of the other computers on the network (if any) are turned off?

---

### Post by ondrokm on 2011-01-18
Yes, I have several computers in the network but none of them has mac address 00:22:69:13:92:09. e8:39:df:0b:1a:e9 belongs to my router.
You might be right, this traffic usually occurs when another pc with Linux is turned on. From that computer I got similar packet that differs only in mac addresses
```

No.     Time        Source                Destination           Protocol Info
   1983 3.351046   ** HonHaiPr_bd:14:47**     IntelCor_41:af:5e     0x05f8   Ethernet II

Frame 1983 (1542 bytes on wire, 1542 bytes captured)
Ethernet II, Src: HonHaiPr_bd:14:47 (00:19:7e:bd:14:47), Dst: IntelCor_41:af:5e (00:1e:64:41:af:5e)
Data (1528 bytes)

```IntelCor_41:af:5e is my laptop.

On that second computer I also recorded this packet:
```

No.     Time        Source                Destination           Protocol Info
   1289 2.038915    HonHaiPr_bd:14:47     IntelCor_41:af:5e     LLC      I, N(R)=16, N(S)=6; DSAP 0x32 Individual, SSAP 0x32 Command

Frame 1289 (970 bytes on wire, 970 bytes captured)
    Arrival Time: Jan 18, 2011 20:41:03.653066000
    [Time delta from previous captured frame: 0.000638000 seconds]
    [Time delta from previous displayed frame: 0.000638000 seconds]
    [Time since reference or first frame: 2.038915000 seconds]
    Frame Number: 1289
    Frame Length: 970 bytes
    Capture Length: 970 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:llc:data]
IEEE 802.3 Ethernet 
    Destination: IntelCor_41:af:5e (00:1e:64:41:af:5e)
        Address: IntelCor_41:af:5e (00:1e:64:41:af:5e)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: HonHaiPr_bd:14:47 (00:19:7e:bd:14:47)
        Address: HonHaiPr_bd:14:47 (00:19:7e:bd:14:47)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Length: 956
Logical-Link Control
    DSAP: Unknown (0x32)
    IG Bit: Individual
    SSAP: Unknown (0x32)
    CR Bit: Command
    Control field: I, N(R)=16, N(S)=6 (0x200C)
        0010 000. .... .... = N(R): 16
        .... .... 0000 110. = N(S): 6
        .... .... .... ...0 = Frame type: Information frame (0x0000)
Data (952 bytes)

```This contains also the unknown address  HonHaiPr_bd:14:47 but there is also my laptop IntelCor_41:af:5e ...
If I get it right, this would mean that the second computer communicate with mine, but I'm sure network cards has different addresses (used wlan0 but also eth0). What does it mean?

I have scanned wireless devices using airodump-ng but there is no device with address HonHaiPr_bd:14:47. I'm not it a town so there is probably nobody connected to my wifi.

If this would be caused by the second Linux laptop, is there a way how to disable the transfer?

Edit: When the Linux computer was turned off, the traffic stopped but now it is here again. Now it is between AskeyCom_0b:1a:e9 (router) and HonHaiPr_de:77:09 (Windows 7 computer).
```

No.     Time        Source                Destination           Protocol Info
      2 0.696311    AskeyCom_0b:1a:e9     HonHaiPr_de:77:09     0x05f0   Ethernet II

Frame 2 (1534 bytes on wire, 1534 bytes captured)
    Arrival Time: Jan 18, 2011 21:11:17.526751000
    [Time delta from previous captured frame: 0.696311000 seconds]
    [Time delta from previous displayed frame: 0.696311000 seconds]
    [Time since reference or first frame: 0.696311000 seconds]
    Frame Number: 2
    Frame Length: 1534 bytes
    Capture Length: 1534 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:data]
Ethernet II, Src: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9), Dst: HonHaiPr_de:77:09 (90:fb:a6:de:77:09)
    Destination: HonHaiPr_de:77:09 (90:fb:a6:de:77:09)
    Source: AskeyCom_0b:1a:e9 (e8:39:df:0b:1a:e9)
    Type: Unknown (0x05f0)
Data (1520 bytes
```

---

### Post by ondrokm on 2011-01-18
Post send twice, server wasn't responding

---

### Post by hansolo4949 on 2011-01-18
Double post. Darn lag...

---

### Post by hansolo4949 on 2011-01-18
hmm...i'm no expert on networking, but perhaps you have file sharing hooked up between the two computers? and do you have anything connected to your router? Do you have any file-sharing programs on both of the computers? maybe the other computer is "pinging" yours???

As I said before, i'm no expert at networking, so please don't think i'm going to tell you exactly what's wrong with your network system. Hmm...:mad:

---

### Post by ondrokm on 2011-01-18
No, there should be no sharing from my laptop. I usually use ssh so I do need anything else. Samba is installed on my pc but nobody has an access. I have all incoming traffic blocked by iptables so this should be cause by some of my program, but if I close all of the internet programs or services I know about, it continues.
There is nothing connected to the router (no printer, NSA, ...)
I see in firestarter pinging of other computers but it's several packets per second, not 300kBps :(

Any advice might be helpful, even if you aren't an expert ;) Thanks for helping me

---

### Post by hansolo4949 on 2011-01-18
No problemo:).

Is one of the file-sharing programs on your computer installed on one of the other linux computers on the network?

If it is...that's your problem. Somehow, the two programs are communicating with each other, and causing the mystery traffic.

Just wondering... is Giver installed on either of the machines?

---

### Post by hansolo4949 on 2011-01-18
Perhaps the two linux computers are pinging each other for some reason? perhaps to know that there's another linux computer on the network? you should use one computer while the other are off, so we can tell if it's that computer communicating with the other, or not.

---

### Post by hansolo4949 on 2011-01-18
Perhaps the two linux computers are pinging each other for some reason? perhaps to know that there's another linux computer on the network? you should use one computer while the other are off, so we can tell if it's that computer communicating with the other, or not.

---

### Post by kistenyer on 2011-01-19
Yes, thank you.

Why do you have so many pop3 and imap packets do you think?

---

### Post by ondrokm on 2011-01-19
**hansolo4949**:
It happens when my computer and any other (one Linux, two with Windows) is turned on, so it  isn't only Linux-Linux or Linux-Windows problem. When Linux computer is turned off, my laptop communicate with Windows and so on.
I've tried several different networks, there was no problem when I was connected to them.
Giver isn't installed on any of the computers. There shouldn't be any sharing program installed on all of the computers.

**kistenyer**:
Imap and pop3 packets aren't problem. They are caused by Thunderbird and many email accounts. I'm almost sure thunderbird doesn't cause it - the traffic remains when thunderbird is turned off.

---

### Post by hansolo4949 on 2011-01-19
Perhaps your router has gone on the fritz??? Maybe you somehow set it to "ping" the computers on the network. This is all very strange...

---

### Post by hansolo4949 on 2011-01-19
Perhaps your router has gone on the fritz??? Maybe you somehow set it to "ping" the computers on the network. This is all very strange...

---

### Post by hansolo4949 on 2011-01-19
Sorry for the triple post... I sure do hope Canonical and Ubuntu figure this out soon...

---

### Post by ondrokm on 2011-01-21
I think I have solved it.
About a week ago I changed the wifi channel on the router because there was another network on the same channel as mine and it caused network instability. I changed it to the different one yesterday and since that time I haven't seen the mysterious traffic.
Any idea how could wifi channel caused the huge traffic?

---

