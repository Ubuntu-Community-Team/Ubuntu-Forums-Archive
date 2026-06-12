---
title: "Why cant I go to any website other than Google?"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by RobFS1 on 2009-08-02
Why cant I go to any website other than Google? I can make Google searches, and view my Gmail, but i cant go anywhere else but those places. Can anyone help?

---

### Post by jonobr on 2009-08-02
open a terminal

whats happens when you do 

nslookup pingplotter.com

what happens when you ping 216.92.151.75 from the terminal?

What happens when you ping pingplotter.com in the terminal

what happens when you type 

w3m 216.92.151.75

what happens when you type 
w3m pingplotter.com

Post results of all here

---

### Post by Iowan on 2009-08-02
Mostly  curiousity: Is that (Google) your home page?

---

### Post by RobFS1 on 2009-08-02
My home page is not Google by the way

Here is the output:

```
nslookup pingplotter.com
;; Got recursion not available from 216.57.160.5, trying next server
Server:		216.57.160.8
Address:	216.57.160.8#53

Name:	pingplotter.com
Address: 216.92.151.75

 ping 216.92.151.75
PING 216.92.151.75 (216.92.151.75) 56(84) bytes of data.
64 bytes from 216.92.151.75: icmp_seq=1 ttl=47 time=113 ms
64 bytes from 216.92.151.75: icmp_seq=2 ttl=47 time=117 ms
64 bytes from 216.92.151.75: icmp_seq=3 ttl=47 time=106 ms
64 bytes from 216.92.151.75: icmp_seq=4 ttl=47 time=135 ms
64 bytes from 216.92.151.75: icmp_seq=5 ttl=47 time=112 ms
64 bytes from 216.92.151.75: icmp_seq=6 ttl=47 time=109 ms
64 bytes from 216.92.151.75: icmp_seq=7 ttl=47 time=108 ms
64 bytes from 216.92.151.75: icmp_seq=8 ttl=47 time=106 ms
64 bytes from 216.92.151.75: icmp_seq=9 ttl=47 time=108 ms
64 bytes from 216.92.151.75: icmp_seq=10 ttl=47 time=109 ms
64 bytes from 216.92.151.75: icmp_seq=11 ttl=47 time=119 ms
64 bytes from 216.92.151.75: icmp_seq=12 ttl=47 time=119 ms
64 bytes from 216.92.151.75: icmp_seq=13 ttl=47 time=110 ms
64 bytes from 216.92.151.75: icmp_seq=14 ttl=47 time=110 ms
64 bytes from 216.92.151.75: icmp_seq=15 ttl=47 time=107 ms
64 bytes from 216.92.151.75: icmp_seq=16 ttl=47 time=118 ms
64 bytes from 216.92.151.75: icmp_seq=17 ttl=47 time=110 ms
64 bytes from 216.92.151.75: icmp_seq=18 ttl=47 time=108 ms
64 bytes from 216.92.151.75: icmp_seq=19 ttl=47 time=117 ms
64 bytes from 216.92.151.75: icmp_seq=20 ttl=47 time=111 ms
64 bytes from 216.92.151.75: icmp_seq=21 ttl=47 time=115 ms
64 bytes from 216.92.151.75: icmp_seq=22 ttl=47 time=110 ms
64 bytes from 216.92.151.75: icmp_seq=23 ttl=47 time=117 ms
64 bytes from 216.92.151.75: icmp_seq=24 ttl=47 time=114 ms
64 bytes from 216.92.151.75: icmp_seq=25 ttl=47 time=112 ms
64 bytes from 216.92.151.75: icmp_seq=26 ttl=47 time=113 ms
64 bytes from 216.92.151.75: icmp_seq=27 ttl=47 time=111 ms
64 bytes from 216.92.151.75: icmp_seq=28 ttl=47 time=104 ms
64 bytes from 216.92.151.75: icmp_seq=29 ttl=47 time=111 ms
64 bytes from 216.92.151.75: icmp_seq=30 ttl=47 time=113 ms

And So forth, it has gone on like this until sequence 500 and so on

(216.92.151.75) 56(84) bytes of data.
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=1 ttl=47 time=111 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=2 ttl=47 time=105 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=3 ttl=47 time=118 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=4 ttl=47 time=108 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=5 ttl=47 time=114 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=6 ttl=47 time=108 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=7 ttl=47 time=111 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=8 ttl=47 time=111 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=9 ttl=47 time=110 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=10 ttl=47 time=109 ms

Likewise

w3m 216.92.151.75

216.92.151.75 contacted. Waiting for reply...



w3m pingplotter.com

pingplotter.com contacted. Waiting for reply...


They just stay like that forever.
```

---

### Post by jonobr on 2009-08-03
Hello


Do you have something setup other then just a regular desktop machine?

Are your running bind/dns yourself?
Did you modify the /etc/resolv.conf file yourself directly?

Have you been modifying your IP tables configuration and blocking ports  ?

---

### Post by dpellon on 2009-08-03
what about using the ggole traductor to navigate the web?

it could be temporel solution.

---

### Post by RobFS1 on 2009-08-03
> **jonobr said:**
> Hello


Do you have something setup other then just a regular desktop machine?

Are your running bind/dns yourself?
Did you modify the /etc/resolv.conf file yourself directly?

Have you been modifying your IP tables configuration and blocking ports  ?

No, but i think that one of those things might have been screwed up, so is there anyway to restore them? Mabey reset it all somehow?

---

### Post by jonobr on 2009-08-04
actually if you were modifying those things you would know about it, so Im thinking they are what they should be.,

The only other thing I can suggest is a packet trace on the interface to see whats happening.

You can do this by opening a terminal window,

```
sudo tcpdump -w trace.pcap -s 1600 -i any port 80
```

launch you browser, then go to another website,
cnn.com or whatever, and then once done, hit control c on the command ran.

That should leave you with a file called trace.pcap.
If you could post here, maybe it would shed some light/

---

### Post by RobFS1 on 2009-08-04
I did that command,

```
sudo tcpdump -w trace.pcap -s 1600 -i any port 80
tcpdump: WARNING: Promiscuous mode not supported on the "any" device
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
226 packets captured
226 packets received by filter
0 packets dropped by kernel

```

What do i do past this?

---

### Post by RobFS1 on 2009-08-04
I have the file but I cant attach it, and i cant open it, what should i do?

---

### Post by jerrrys on 2009-08-04
how bout installing another browser just to see if it works...

---

### Post by jonobr on 2009-08-04
Can you attach this to this thread?

---

### Post by RobFS1 on 2009-08-04
The Browser isn't the problem, it is that all access to the internet aside from Google isn't attainable. I cant even download packages from synaptic. 

jonobr, I am not able to attach it to the thread, no. Is there some way of opening it and attaching the code to the forumn? By the way, jonobr, i really have to thank you for your help.

---

### Post by jonobr on 2009-08-04
You would need to download a program to view it so that would be difficult given your setup.

If you have access to gmail Im thinking you could email the file to your self and attach it using some the machine your using now,?
WOuld that work?

If no

then try this


```
tcpdump -vvxNs0 -i any port 80
```

Launch the broswer to google, 
then launch the browser to another site and grab the result

---

### Post by RobFS1 on 2009-08-04
How would i attach it if i cant attach .pcap files on this forumn?

---

### Post by RobFS1 on 2009-08-04
Can you make light of this?

```
Promiscuous mode not supported on the "any" device 
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes 
11:53:58.089117 IP (tos 0x0, ttl 64, id 35703, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.45205 > fxfeeds.www: S, cksum 0xaade (correct), 1837108362:1837108362(0) win 5840 <mss 1460,sackOK,timestamp 100349 0,nop,wscale 6> 
	0x0000:  4500 003c 8b77 4000 4006 dbe0 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8a 0000 0000 
	0x0020:  a002 16d0 aade 0000 0204 05b4 0402 080a 
	0x0030:  0001 87fd 0000 0000 0103 0306 
11:53:58.159305 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.www > UbuntuRob.45205: S, cksum 0xbe31 (correct), 2394306057:2394306057(0) ack 1837108363 win 5840 <mss 1460> 
	0x0000:  4500 002c 0000 4000 3106 7668 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 3609 6d80 0c8b 
	0x0020:  6012 16d0 be31 0000 0204 05b4 b643 
11:53:58.159361 IP (tos 0x0, ttl 64, id 35704, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xd5ee (correct), 1:1(0) ack 1 win 5840 
	0x0000:  4500 0028 8b78 4000 4006 dbf3 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8b 8eb6 360a 
	0x0020:  5010 16d0 d5ee 0000 
11:53:58.159458 IP (tos 0x0, ttl 64, id 35705, offset 0, flags [DF], proto TCP (6), length 717) UbuntuRob.45205 > fxfeeds.www: P, cksum 0x7f2c (correct), 1:678(677) ack 1 win 5840 
	0x0000:  4500 02cd 8b79 4000 4006 d94d c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8b 8eb6 360a 
	0x0020:  5018 16d0 7f2c 0000 4745 5420 2f65 6e2d 
	0x0030:  5553 2f66 6972 6566 6f78 2f68 6561 646c 
	0x0040:  696e 6573 2e78 6d6c 2048 5454 502f 312e 
	0x0050:  310d 0a48 6f73 743a 2065 6e2d 7573 2e66 
	0x0060:  7866 6565 6473 2e6d 6f7a 696c 6c61 2e63 
	0x0070:  6f6d 0d0a 5573 6572 2d41 6765 6e74 3a20 
	0x0080:  4d6f 7a69 6c6c 612f 352e 3020 2858 3131 
	0x0090:  3b20 553b 204c 696e 7578 2069 3638 363b 
	0x00a0:  2065 6e2d 5553 3b20 7276 3a31 2e39 2e30 
	0x00b0:  2e31 3129 2047 6563 6b6f 2f32 3030 3930 
	0x00c0:  3630 3330 3920 5562 756e 7475 2f38 2e30 
	0x00d0:  3420 2868 6172 6479 2920 4669 7265 666f 
	0x00e0:  782f 332e 302e 3131 0d0a 4163 6365 7074 
	0x00f0:  3a20 7465 7874 2f68 746d 6c2c 6170 706c 
	0x0100:  6963 6174 696f 6e2f 7868 746d 6c2b 786d 
	0x0110:  6c2c 6170 706c 6963 6174 696f 6e2f 786d 
	0x0120:  6c3b 713d 302e 392c 2a2f 2a3b 713d 302e 
	0x0130:  380d 0a41 6363 6570 742d 4c61 6e67 7561 
	0x0140:  6765 3a20 656e 2d75 732c 656e 3b71 3d30 
	0x0150:  2e35 0d0a 4163 6365 7074 2d45 6e63 6f64 
	0x0160:  696e 673a 2067 7a69 702c 6465 666c 6174 
	0x0170:  650d 0a41 6363 6570 742d 4368 6172 7365 
	0x0180:  743a 2049 534f 2d38 3835 392d 312c 7574 
	0x0190:  662d 383b 713d 302e 372c 2a3b 713d 302e 
	0x01a0:  370d 0a4b 6565 702d 416c 6976 653a 2033 
	0x01b0:  3030 0d0a 436f 6e6e 6563 7469 6f6e 3a20 
	0x01c0:  6b65 6570 2d61 6c69 7665 0d0a 582d 4d6f 
	0x01d0:  7a3a 206c 6976 6562 6f6f 6b6d 6172 6b73 
	0x01e0:  0d0a 436f 6f6b 6965 3a20 5f5f 7574 6d61 
	0x01f0:  3d31 3833 3835 3936 3432 2e31 3133 3835 
	0x0200:  3031 3035 362e 3132 3339 3636 3437 3833 
	0x0210:  2e31 3233 3936 3634 3738 332e 3132 3339 
	0x0220:  3636 3437 3833 2e31 3b20 5f5f 7574 6d7a 
	0x0230:  3d31 3833 3835 3936 3432 2e31 3233 3936 
	0x0240:  3635 3035 302e 312e 332e 7574 6d63 636e 
	0x0250:  3d28 6f72 6761 6e69 6329 7c75 746d 6373 
	0x0260:  723d 676f 6f67 6c65 7c75 746d 6374 723d 
	0x0270:  6669 7265 666f 782b 7769 6e64 6f77 732b 
	0x0280:  646f 776e 6c6f 6164 7c75 746d 636d 643d 
	0x0290:  6f72 6761 6e69 633b 2073 5f76 693d 5b43 
	0x02a0:  535d 7631 7c34 3945 3343 3841 3330 3030 
	0x02b0:  3033 4230 452d 4130 3230 3833 3530 3030 
	0x02c0:  3030 3032 325b 4345 5d0d 0a0d 0a 
11:53:58.230932 IP (tos 0x0, ttl 49, id 25762, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: ., cksum 0xcfa7 (correct), 1:1(0) ack 678 win 6770 
	0x0000:  4500 0028 64a2 4000 3106 11ca 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 360a 6d80 0f30 
	0x0020:  5010 1a72 cfa7 0000 0000 4b82 2e20 
11:53:58.233926 IP (tos 0x0, ttl 49, id 25763, offset 0, flags [DF], proto TCP (6), length 699) fxfeeds.www > UbuntuRob.45205: P, cksum 0x781c (correct), 1:660(659) ack 678 win 6770 
	0x0000:  4500 02bb 64a3 4000 3106 0f36 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 360a 6d80 0f30 
	0x0020:  5018 1a72 781c 0000 4854 5450 2f31 2e31 
	0x0030:  2033 3032 2046 6f75 6e64 0d0a 4578 7069 
	0x0040:  7265 733a 2054 7565 2c20 3034 2041 7567 
	0x0050:  2032 3031 3020 3137 3a34 393a 3535 2047 
	0x0060:  4d54 0d0a 436f 6e74 656e 742d 4c65 6e67 
	0x0070:  7468 3a20 3332 330d 0a44 6174 653a 2054 
	0x0080:  7565 2c20 3034 2041 7567 2032 3030 3920 
	0x0090:  3137 3a35 333a 3538 2047 4d54 0d0a 4c6f 
	0x00a0:  6361 7469 6f6e 3a20 6874 7470 3a2f 2f66 
	0x00b0:  7866 6565 6473 2e6d 6f7a 696c 6c61 2e63 
	0x00c0:  6f6d 2f66 6972 6566 6f78 2f68 6561 646c 
	0x00d0:  696e 6573 2e78 6d6c 0d0a 5365 7276 6572 
	0x00e0:  3a20 4170 6163 6865 2f32 2e32 2e33 2028 
	0x00f0:  5265 6420 4861 7429 0d0a 436f 6e74 656e 
	0x0100:  742d 5479 7065 3a20 7465 7874 2f68 746d 
	0x0110:  6c3b 2063 6861 7273 6574 3d69 736f 2d38 
	0x0120:  3835 392d 310d 0a4b 6565 702d 416c 6976 
	0x0130:  653a 2074 696d 656f 7574 3d32 302c 206d 
	0x0140:  6178 3d38 3931 0d0a 582d 4361 6368 652d 
	0x0150:  496e 666f 3a20 6361 6368 6564 0d0a 436f 
	0x0160:  6e6e 6563 7469 6f6e 3a20 4b65 6570 2d41 
	0x0170:  6c69 7665 0d0a 0d0a 3c21 444f 4354 5950 
	0x0180:  4520 4854 4d4c 2050 5542 4c49 4320 222d 
	0x0190:  2f2f 4945 5446 2f2f 4454 4420 4854 4d4c 
	0x01a0:  2032 2e30 2f2f 454e 223e 0a3c 6874 6d6c 
	0x01b0:  3e3c 6865 6164 3e0a 3c74 6974 6c65 3e33 
	0x01c0:  3032 2046 6f75 6e64 3c2f 7469 746c 653e 
	0x01d0:  0a3c 2f68 6561 643e 3c62 6f64 793e 0a3c 
	0x01e0:  6831 3e46 6f75 6e64 3c2f 6831 3e0a 3c70 
	0x01f0:  3e54 6865 2064 6f63 756d 656e 7420 6861 
	0x0200:  7320 6d6f 7665 6420 3c61 2068 7265 663d 
	0x0210:  2268 7474 703a 2f2f 6678 6665 6564 732e 
	0x0220:  6d6f 7a69 6c6c 612e 636f 6d2f 6669 7265 
	0x0230:  666f 782f 6865 6164 6c69 6e65 732e 786d 
	0x0240:  6c22 3e68 6572 653c 2f61 3e2e 3c2f 703e 
	0x0250:  0a3c 6872 3e0a 3c61 6464 7265 7373 3e41 
	0x0260:  7061 6368 652f 322e 322e 3320 2852 6564 
	0x0270:  2048 6174 2920 5365 7276 6572 2061 7420 
	0x0280:  656e 2d75 732e 6678 6665 6564 732e 6d6f 
	0x0290:  7a69 6c6c 612e 636f 6d20 506f 7274 2038 
	0x02a0:  303c 2f61 6464 7265 7373 3e0a 3c2f 626f 
	0x02b0:  6479 3e3c 2f68 746d 6c3e 0a 
11:53:58.233939 IP (tos 0x0, ttl 64, id 35706, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xcdc8 (correct), 678:678(0) ack 660 win 6590 
	0x0000:  4500 0028 8b7a 4000 4006 dbf1 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389d 
	0x0020:  5010 19be cdc8 0000 
11:53:58.272636 IP (tos 0x0, ttl 64, id 13532, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.45206 > fxfeeds.www: S, cksum 0xf9b6 (correct), 1846263031:1846263031(0) win 5840 <mss 1460,sackOK,timestamp 100395 0,nop,wscale 6> 
	0x0000:  4500 003c 34dc 4000 4006 327c c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf7 0000 0000 
	0x0020:  a002 16d0 f9b6 0000 0204 05b4 0402 080a 
	0x0030:  0001 882b 0000 0000 0103 0306 
11:53:58.331994 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.www > UbuntuRob.45206: S, cksum 0x8026 (correct), 1813833140:1813833140(0) ack 1846263032 win 5840 <mss 1460> 
	0x0000:  4500 002c 0000 4000 3106 7668 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b4 6e0b bcf8 
	0x0020:  6012 16d0 8026 0000 0204 05b4 9adc 
11:53:58.332037 IP (tos 0x0, ttl 64, id 13533, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x97e3 (correct), 1:1(0) ack 1 win 5840 
	0x0000:  4500 0028 34dd 4000 4006 328f c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf8 6c1c e5b5 
	0x0020:  5010 16d0 97e3 0000 
11:53:58.332119 IP (tos 0x0, ttl 64, id 13534, offset 0, flags [DF], proto TCP (6), length 683) UbuntuRob.45206 > fxfeeds.www: P, cksum 0x0a18 (correct), 1:644(643) ack 1 win 5840 
	0x0000:  4500 02ab 34de 4000 4006 300b c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf8 6c1c e5b5 
	0x0020:  5018 16d0 0a18 0000 4745 5420 2f66 6972 
	0x0030:  6566 6f78 2f68 6561 646c 696e 6573 2e78 
	0x0040:  6d6c 2048 5454 502f 312e 310d 0a48 6f73 
	0x0050:  743a 2066 7866 6565 6473 2e6d 6f7a 696c 
	0x0060:  6c61 2e63 6f6d 0d0a 5573 6572 2d41 6765 
	0x0070:  6e74 3a20 4d6f 7a69 6c6c 612f 352e 3020 
	0x0080:  2858 3131 3b20 553b 204c 696e 7578 2069 
	0x0090:  3638 363b 2065 6e2d 5553 3b20 7276 3a31 
	0x00a0:  2e39 2e30 2e31 3129 2047 6563 6b6f 2f32 
	0x00b0:  3030 3930 3630 3330 3920 5562 756e 7475 
	0x00c0:  2f38 2e30 3420 2868 6172 6479 2920 4669 
	0x00d0:  7265 666f 782f 332e 302e 3131 0d0a 4163 
	0x00e0:  6365 7074 3a20 7465 7874 2f68 746d 6c2c 
	0x00f0:  6170 706c 6963 6174 696f 6e2f 7868 746d 
	0x0100:  6c2b 786d 6c2c 6170 706c 6963 6174 696f 
	0x0110:  6e2f 786d 6c3b 713d 302e 392c 2a2f 2a3b 
	0x0120:  713d 302e 380d 0a41 6363 6570 742d 4c61 
	0x0130:  6e67 7561 6765 3a20 656e 2d75 732c 656e 
	0x0140:  3b71 3d30 2e35 0d0a 4163 6365 7074 2d45 
	0x0150:  6e63 6f64 696e 673a 2067 7a69 702c 6465 
	0x0160:  666c 6174 650d 0a41 6363 6570 742d 4368 
	0x0170:  6172 7365 743a 2049 534f 2d38 3835 392d 
	0x0180:  312c 7574 662d 383b 713d 302e 372c 2a3b 
	0x0190:  713d 302e 370d 0a4b 6565 702d 416c 6976 
	0x01a0:  653a 2033 3030 0d0a 436f 6e6e 6563 7469 
	0x01b0:  6f6e 3a20 6b65 6570 2d61 6c69 7665 0d0a 
	0x01c0:  436f 6f6b 6965 3a20 5f5f 7574 6d61 3d31 
	0x01d0:  3833 3835 3936 3432 2e31 3133 3835 3031 
	0x01e0:  3035 362e 3132 3339 3636 3437 3833 2e31 
	0x01f0:  3233 3936 3634 3738 332e 3132 3339 3636 
	0x0200:  3437 3833 2e31 3b20 5f5f 7574 6d7a 3d31 
	0x0210:  3833 3835 3936 3432 2e31 3233 3936 3635 
	0x0220:  3035 302e 312e 332e 7574 6d63 636e 3d28 
	0x0230:  6f72 6761 6e69 6329 7c75 746d 6373 723d 
	0x0240:  676f 6f67 6c65 7c75 746d 6374 723d 6669 
	0x0250:  7265 666f 782b 7769 6e64 6f77 732b 646f 
	0x0260:  776e 6c6f 6164 7c75 746d 636d 643d 6f72 
	0x0270:  6761 6e69 633b 2073 5f76 693d 5b43 535d 
	0x0280:  7631 7c34 3945 3343 3841 3330 3030 3033 
	0x0290:  4230 452d 4130 3230 3833 3530 3030 3030 
	0x02a0:  3032 325b 4345 5d0d 0a0d 0a 
11:53:58.398472 IP (tos 0x0, ttl 49, id 25766, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: ., cksum 0x908f (correct), 1:1(0) ack 644 win 7073 
	0x0000:  4500 0028 64a6 4000 3106 11c6 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b5 6e0b bf7b 
	0x0020:  5010 1ba1 908f 0000 0000 9c68 95c0 
11:53:58.402401 IP (tos 0x0, ttl 49, id 25767, offset 0, flags [DF], proto TCP (6), length 741) fxfeeds.www > UbuntuRob.45206: P, cksum 0x9835 (correct), 1:702(701) ack 644 win 7073 
	0x0000:  4500 02e5 64a7 4000 3106 0f08 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b5 6e0b bf7b 
	0x0020:  5018 1ba1 9835 0000 4854 5450 2f31 2e31 
	0x0030:  2033 3032 2046 6f75 6e64 0d0a 4578 7069 
	0x0040:  7265 733a 2054 7565 2c20 3034 2041 7567 
	0x0050:  2032 3031 3020 3137 3a35 333a 3537 2047 
	0x0060:  4d54 0d0a 436f 6e74 656e 742d 4c65 6e67 
	0x0070:  7468 3a20 3334 310d 0a44 6174 653a 2054 
	0x0080:  7565 2c20 3034 2041 7567 2032 3030 3920 
	0x0090:  3137 3a35 333a 3538 2047 4d54 0d0a 4c6f 
	0x00a0:  6361 7469 6f6e 3a20 6874 7470 3a2f 2f6e 
	0x00b0:  6577 7372 7373 2e62 6263 2e63 6f2e 756b 
	0x00c0:  2f72 7373 2f6e 6577 736f 6e6c 696e 655f 
	0x00d0:  776f 726c 645f 6564 6974 696f 6e2f 6672 
	0x00e0:  6f6e 745f 7061 6765 2f72 7373 2e78 6d6c 
	0x00f0:  0d0a 5365 7276 6572 3a20 4170 6163 6865 
	0x0100:  2f32 2e32 2e33 2028 5265 6420 4861 7429 
	0x0110:  0d0a 436f 6e74 656e 742d 5479 7065 3a20 
	0x0120:  7465 7874 2f68 746d 6c3b 2063 6861 7273 
	0x0130:  6574 3d69 736f 2d38 3835 392d 310d 0a4b 
	0x0140:  6565 702d 416c 6976 653a 2074 696d 656f 
	0x0150:  7574 3d32 302c 206d 6178 3d38 3732 0d0a 
	0x0160:  582d 4361 6368 652d 496e 666f 3a20 6361 
	0x0170:  6368 6564 0d0a 436f 6e6e 6563 7469 6f6e 
	0x0180:  3a20 4b65 6570 2d41 6c69 7665 0d0a 0d0a 
	0x0190:  3c21 444f 4354 5950 4520 4854 4d4c 2050 
	0x01a0:  5542 4c49 4320 222d 2f2f 4945 5446 2f2f 
	0x01b0:  4454 4420 4854 4d4c 2032 2e30 2f2f 454e 
	0x01c0:  223e 0a3c 6874 6d6c 3e3c 6865 6164 3e0a 
	0x01d0:  3c74 6974 6c65 3e33 3032 2046 6f75 6e64 
	0x01e0:  3c2f 7469 746c 653e 0a3c 2f68 6561 643e 
	0x01f0:  3c62 6f64 793e 0a3c 6831 3e46 6f75 6e64 
	0x0200:  3c2f 6831 3e0a 3c70 3e54 6865 2064 6f63 
	0x0210:  756d 656e 7420 6861 7320 6d6f 7665 6420 
	0x0220:  3c61 2068 7265 663d 2268 7474 703a 2f2f 
	0x0230:  6e65 7773 7273 732e 6262 632e 636f 2e75 
	0x0240:  6b2f 7273 732f 6e65 7773 6f6e 6c69 6e65 
	0x0250:  5f77 6f72 6c64 5f65 6469 7469 6f6e 2f66 
	0x0260:  726f 6e74 5f70 6167 652f 7273 732e 786d 
	0x0270:  6c22 3e68 6572 653c 2f61 3e2e 3c2f 703e 
	0x0280:  0a3c 6872 3e0a 3c61 6464 7265 7373 3e41 
	0x0290:  7061 6368 652f 322e 322e 3320 2852 6564 
	0x02a0:  2048 6174 2920 5365 7276 6572 2061 7420 
	0x02b0:  6678 6665 6564 732e 6d6f 7a69 6c6c 612e 
	0x02c0:  636f 6d20 506f 7274 2038 303c 2f61 6464 
	0x02d0:  7265 7373 3e0a 3c2f 626f 6479 3e3c 2f68 
	0x02e0:  746d 6c3e 0a 
11:53:58.402417 IP (tos 0x0, ttl 64, id 13535, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e11 (correct), 644:644(0) ack 702 win 7010 
	0x0000:  4500 0028 34df 4000 4006 328d c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e872 
	0x0020:  5010 1b62 8e11 0000 
11:53:58.425581 IP (tos 0x0, ttl 64, id 20744, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.40742 > newslb308.www: S, cksum 0x495c (correct), 1846991193:1846991193(0) win 5840 <mss 1460,sackOK,timestamp 100433 0,nop,wscale 6> 
	0x0000:  4500 003c 5108 4000 4006 7118 c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d959 0000 0000 
	0x0020:  a002 16d0 495c 0000 0204 05b4 0402 080a 
	0x0030:  0001 8851 0000 0000 0103 0306 
11:53:58.611909 IP (tos 0x0, ttl 44, id 0, offset 0, flags [DF], proto TCP (6), length 60) newslb308.www > UbuntuRob.40742: S, cksum 0x6419 (correct), 737567975:737567975(0) ack 1846991194 win 5792 <mss 1460,sackOK,timestamp 1244334680 100433,nop,wscale 7> 
	0x0000:  4500 003c 0000 4000 2c06 d620 d43a e24f 
	0x0010:  c0a8 0169 0050 9f26 2bf6 64e7 6e16 d95a 
	0x0020:  a012 16a0 6419 0000 0204 05b4 0402 080a 
	0x0030:  4a2b 0a58 0001 8851 0103 0307 
11:53:58.611962 IP (tos 0x0, ttl 64, id 20745, offset 0, flags [DF], proto TCP (6), length 52) UbuntuRob.40742 > newslb308.www: ., cksum 0xa8fa (correct), 1:1(0) ack 1 win 92 <nop,nop,timestamp 100480 1244334680> 
	0x0000:  4500 0034 5109 4000 4006 711f c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d95a 2bf6 64e8 
	0x0020:  8010 005c a8fa 0000 0101 080a 0001 8880 
	0x0030:  4a2b 0a58 
11:53:58.612046 IP (tos 0x0, ttl 64, id 20746, offset 0, flags [DF], proto TCP (6), length 733) UbuntuRob.40742 > newslb308.www: P, cksum 0xf204 (correct), 1:682(681) ack 1 win 92 <nop,nop,timestamp 100480 1244334680> 
	0x0000:  4500 02dd 510a 4000 4006 6e75 c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d95a 2bf6 64e8 
	0x0020:  8018 005c f204 0000 0101 080a 0001 8880 
	0x0030:  4a2b 0a58 4745 5420 2f72 7373 2f6e 6577 
	0x0040:  736f 6e6c 696e 655f 776f 726c 645f 6564 
	0x0050:  6974 696f 6e2f 6672 6f6e 745f 7061 6765 
	0x0060:  2f72 7373 2e78 6d6c 2048 5454 502f 312e 
	0x0070:  310d 0a48 6f73 743a 206e 6577 7372 7373 
	0x0080:  2e62 6263 2e63 6f2e 756b 0d0a 5573 6572 
	0x0090:  2d41 6765 6e74 3a20 4d6f 7a69 6c6c 612f 
	0x00a0:  352e 3020 2858 3131 3b20 553b 204c 696e 
	0x00b0:  7578 2069 3638 363b 2065 6e2d 5553 3b20 
	0x00c0:  7276 3a31 2e39 2e30 2e31 3129 2047 6563 
	0x00d0:  6b6f 2f32 3030 3930 3630 3330 3920 5562 
	0x00e0:  756e 7475 2f38 2e30 3420 2868 6172 6479 
	0x00f0:  2920 4669 7265 666f 782f 332e 302e 3131 
	0x0100:  0d0a 4163 6365 7074 3a20 7465 7874 2f68 
	0x0110:  746d 6c2c 6170 706c 6963 6174 696f 6e2f 
	0x0120:  7868 746d 6c2b 786d 6c2c 6170 706c 6963 
	0x0130:  6174 696f 6e2f 786d 6c3b 713d 302e 392c 
	0x0140:  2a2f 2a3b 713d 302e 380d 0a41 6363 6570 
	0x0150:  742d 4c61 6e67 7561 6765 3a20 656e 2d75 
	0x0160:  732c 656e 3b71 3d30 2e35 0d0a 4163 6365 
	0x0170:  7074 2d45 6e63 6f64 696e 673a 2067 7a69 
	0x0180:  702c 6465 666c 6174 650d 0a41 6363 6570 
	0x0190:  742d 4368 6172 7365 743a 2049 534f 2d38 
	0x01a0:  3835 392d 312c 7574 662d 383b 713d 302e 
	0x01b0:  372c 2a3b 713d 302e 370d 0a4b 6565 702d 
	0x01c0:  416c 6976 653a 2033 3030 0d0a 436f 6e6e 
	0x01d0:  6563 7469 6f6e 3a20 6b65 6570 2d61 6c69 
	0x01e0:  7665 0d0a 436f 6f6b 6965 3a20 4242 432d 
	0x01f0:  5549 443d 3334 3839 3539 6561 3330 6338 
	0x0200:  3037 3964 3834 3663 6439 6338 3031 3136 
	0x0210:  6165 3965 3939 6566 6137 3736 3830 3930 
	0x0220:  3431 3636 3033 6335 6435 6263 3238 3135 
	0x0230:  3865 3561 304d 6f7a 696c 6c61 2532 6635 
	0x0240:  2532 6530 2532 3025 3238 5831 3125 3362 
	0x0250:  2532 3055 2533 6225 3230 4c69 6e75 7825 
	0x0260:  3230 6936 3836 2533 6225 3230 656e 2532 
	0x0270:  6455 5325 3362 2532 3072 7625 3361 3125 
	0x0280:  3265 3925 3265 3025 3265 3625 3239 2532 
	0x0290:  3047 6563 6b6f 2532 6632 3030 3930 3230 
	0x02a0:  3931 3125 3230 5562 756e 7475 2532 6638 
	0x02b0:  2532 6530 3425 3230 2532 3868 6172 6479 
	0x02c0:  2532 3925 3230 4669 7265 666f 7825 3266 
	0x02d0:  3325 3265 3025 3265 360d 0a0d 0a 
11:53:58.782117 IP (tos 0x0, ttl 44, id 25770, offset 0, flags [DF], proto TCP (6), length 52) newslb308.www > UbuntuRob.40742: ., cksum 0xa5bf (correct), 1:1(0) ack 682 win 56 <nop,nop,timestamp 1244334862 100480> 
	0x0000:  4500 0034 64aa 4000 2c06 717e d43a e24f 
	0x0010:  c0a8 0169 0050 9f26 2bf6 64e8 6e16 dc03 
	0x0020:  8010 0038 a5bf 0000 0101 080a 4a2b 0b0e 
	0x0030:  0001 8880 
11:54:08.358861 IP (tos 0x0, ttl 49, id 39284, offset 0, flags [DF], proto TCP (6), length 570) giraffe.www > UbuntuRob.55887: FP, cksum 0xd2b1 (correct), 1294782094:1294782612(518) ack 1755973055 win 2036 <nop,nop,timestamp 2743964920 99086> 
	0x0000:  4500 023a 9974 4000 3106 5d8f 3ff7 4eb2 
	0x0010:  c0a8 0169 0050 da4f 4d2c ce8e 68aa 05bf 
	0x0020:  8019 07f4 d2b1 0000 0101 080a a38d 94f8 
	0x0030:  0001 830e fa1f 6fb4 869b 03dc 84b1 c485 
	0x0040:  7980 eb74 baf6 32a3 0662 fd8d 63e4 6a3a 
	0x0050:  0240 d06c 7061 ce06 f43f 4c91 a7e9 b928 
	0x0060:  9920 9233 854d 63ab e879 1eb7 dc7c 9748 
	0x0070:  e454 0a21 a16b 7fd8 0868 809a bdc1 81bf 
	0x0080:  a551 7dff bc55 685e 5ad2 712a 0587 1585 
	0x0090:  bcb5 44c4 118d 36df eb23 149d c8fc 51a5 
	0x00a0:  ee5b 4358 cfd8 ce8d cc63 fb5a af8e 69cc 
	0x00b0:  3330 0158 5c3d 86f3 7b96 3045 c5b8 b2aa 
	0x00c0:  5e0c 4748 aaf0 e7e5 effa ba6b 8049 88a9 
	0x00d0:  d146 fdb5 f7a4 1657 e5c9 ef09 6698 0f52 
	0x00e0:  debc 241b afd0 ecae 7b5d 876e 2f03 99c2 
	0x00f0:  2b38 8898 33ae e874 cada 77ab ffc4 49d6 
	0x0100:  4e98 c61b 84b0 dde9 918c 4559 db44 4e10 
	0x0110:  f4ec e2cb f5c5 57f8 f980 6808 bf37 9372 
	0x0120:  26d8 98c6 e348 703c 3443 e2a5 f9c4 3fec 
	0x0130:  1c87 bdde 7137 3ce8 f58e 8ec2 d7de 4985 
	0x0140:  74c9 63f3 85e2 a8db ab0e cf19 9e3f 183f 
	0x0150:  0eab c358 d050 030c f477 c7e1 9866 1b68 
	0x0160:  281e cea2 8063 13c1 f006 3c80 50f1 c6ef 
	0x0170:  847e e7a8 4fae f0c3 6c55 56c8 f709 14b1 
	0x0180:  b0aa 77d8 0d0f dfbc 7e73 d45d 8342 2691 
	0x0190:  6a3c 8135 70e4 8126 347f 3bf3 339c 7b17 
	0x01a0:  e2bf ed39 f359 d1ad 7cf7 6e7b 1625 6dc6 
	0x01b0:  cd95 b093 c565 7eb0 f1d1 e37e abec 111b 
	0x01c0:  d75d 80c1 4048 e36e db32 c856 49ec 3e17 
	0x01d0:  b721 e2bb d920 9b43 8344 63fb 8567 aff2 
	0x01e0:  3967 1094 4e5b 70ad 829b e865 807d 0ad1 
	0x01f0:  6d05 a928 33b8 3994 a53c 41b8 26df d97b 
	0x0200:  ec7e 467b e31c e2b7 51d7 b7b7 7eaf db79 
	0x0210:  f3fa c0ef 805a 2c93 6b45 a31b a6c0 fd37 
	0x0220:  05c7 4f03 d883 401c 1ded fd17 0000 ffff 
	0x0230:  0300 7ee0 f6e7 c020 0000 
11:54:08.358904 IP (tos 0x0, ttl 64, id 33671, offset 0, flags [DF], proto TCP (6), length 64) UbuntuRob.55887 > giraffe.www: ., cksum 0xcd79 (correct), 1:1(0) ack 4294964400 win 109 <nop,nop,timestamp 102916 2743949696,nop,nop,sack 1 {0:519}> 
	0x0000:  4500 0040 8387 4000 4006 6676 c0a8 0169 
	0x0010:  3ff7 4eb2 da4f 0050 68aa 05bf 4d2c c33e 
	0x0020:  b010 006d cd79 0000 0101 080a 0001 9204 
	0x0030:  a38d 5980 0101 050a 4d2c ce8e 4d2c d095 
11:54:09.421091 IP (tos 0x0, ttl 49, id 56555, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: F, cksum 0xcd13 (correct), 660:660(0) ack 678 win 6770 
	0x0000:  4500 0028 dceb 4000 3106 9980 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 389d 6d80 0f30 
	0x0020:  5011 1a72 cd13 0000 0000 7d4c 5a52 
11:54:09.459442 IP (tos 0x0, ttl 64, id 35707, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xcdc7 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7b 4000 4006 dbf0 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5010 19be cdc7 0000 
11:54:11.018091 IP (tos 0x0, ttl 49, id 12096, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: F, cksum 0x8dd1 (correct), 702:702(0) ack 644 win 7073 
	0x0000:  4500 0028 2f40 4000 3106 472c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e872 6e0b bf7b 
	0x0020:  5011 1ba1 8dd1 0000 0000 29bd 7e61 
11:54:11.055445 IP (tos 0x0, ttl 64, id 13536, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e10 (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e0 4000 4006 328c c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5010 1b62 8e10 0000 
11:54:11.280927 IP (tos 0x0, ttl 49, id 12097, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: F, cksum 0x8dd1 (correct), 702:702(0) ack 644 win 7073 
	0x0000:  4500 0028 2f41 4000 3106 472b 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e872 6e0b bf7b 
	0x0020:  5011 1ba1 8dd1 0000 0000 0130 39c9 
11:54:11.280966 IP (tos 0x0, ttl 64, id 13537, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e10 (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e1 4000 4006 328b c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5010 1b62 8e10 0000 
11:54:22.433008 IP (tos 0x0, ttl 64, id 13538, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: F, cksum 0x8e0f (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e2 4000 4006 328a c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5011 1b62 8e0f 0000 
11:54:22.433053 IP (tos 0x0, ttl 64, id 35708, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: F, cksum 0xcdc6 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7c 4000 4006 dbef c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5011 19be cdc6 0000 
11:54:22.695497 IP (tos 0x0, ttl 64, id 13539, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: F, cksum 0x8e0f (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e3 4000 4006 3289 c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5011 1b62 8e0f 0000 
11:54:22.699470 IP (tos 0x0, ttl 64, id 35709, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: F, cksum 0xcdc6 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7d 4000 4006 dbee c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5011 19be cdc6 0000 
11:54:22.898539 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: ., cksum 0x8dd0 (correct), 703:703(0) ack 645 win 7073 
	0x0000:  4500 0028 0000 4000 3106 766c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e873 6e0b bf7c 
	0x0020:  5010 1ba1 8dd0 0000 0000 7653 2140 
11:54:22.899955 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: ., cksum 0xcd12 (correct), 661:661(0) ack 679 win 6770 
	0x0000:  4500 0028 0000 4000 3106 766c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 389e 6d80 0f31 
	0x0020:  5010 1a72 cd12 0000 0000 f04e eff5 Promiscuous mode not supported on the "any" device 
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes 
11:53:58.089117 IP (tos 0x0, ttl 64, id 35703, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.45205 > fxfeeds.www: S, cksum 0xaade (correct), 1837108362:1837108362(0) win 5840 <mss 1460,sackOK,timestamp 100349 0,nop,wscale 6> 
	0x0000:  4500 003c 8b77 4000 4006 dbe0 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8a 0000 0000 
	0x0020:  a002 16d0 aade 0000 0204 05b4 0402 080a 
	0x0030:  0001 87fd 0000 0000 0103 0306 
11:53:58.159305 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.www > UbuntuRob.45205: S, cksum 0xbe31 (correct), 2394306057:2394306057(0) ack 1837108363 win 5840 <mss 1460> 
	0x0000:  4500 002c 0000 4000 3106 7668 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 3609 6d80 0c8b 
	0x0020:  6012 16d0 be31 0000 0204 05b4 b643 
11:53:58.159361 IP (tos 0x0, ttl 64, id 35704, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xd5ee (correct), 1:1(0) ack 1 win 5840 
	0x0000:  4500 0028 8b78 4000 4006 dbf3 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8b 8eb6 360a 
	0x0020:  5010 16d0 d5ee 0000 
11:53:58.159458 IP (tos 0x0, ttl 64, id 35705, offset 0, flags [DF], proto TCP (6), length 717) UbuntuRob.45205 > fxfeeds.www: P, cksum 0x7f2c (correct), 1:678(677) ack 1 win 5840 
	0x0000:  4500 02cd 8b79 4000 4006 d94d c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0c8b 8eb6 360a 
	0x0020:  5018 16d0 7f2c 0000 4745 5420 2f65 6e2d 
	0x0030:  5553 2f66 6972 6566 6f78 2f68 6561 646c 
	0x0040:  696e 6573 2e78 6d6c 2048 5454 502f 312e 
	0x0050:  310d 0a48 6f73 743a 2065 6e2d 7573 2e66 
	0x0060:  7866 6565 6473 2e6d 6f7a 696c 6c61 2e63 
	0x0070:  6f6d 0d0a 5573 6572 2d41 6765 6e74 3a20 
	0x0080:  4d6f 7a69 6c6c 612f 352e 3020 2858 3131 
	0x0090:  3b20 553b 204c 696e 7578 2069 3638 363b 
	0x00a0:  2065 6e2d 5553 3b20 7276 3a31 2e39 2e30 
	0x00b0:  2e31 3129 2047 6563 6b6f 2f32 3030 3930 
	0x00c0:  3630 3330 3920 5562 756e 7475 2f38 2e30 
	0x00d0:  3420 2868 6172 6479 2920 4669 7265 666f 
	0x00e0:  782f 332e 302e 3131 0d0a 4163 6365 7074 
	0x00f0:  3a20 7465 7874 2f68 746d 6c2c 6170 706c 
	0x0100:  6963 6174 696f 6e2f 7868 746d 6c2b 786d 
	0x0110:  6c2c 6170 706c 6963 6174 696f 6e2f 786d 
	0x0120:  6c3b 713d 302e 392c 2a2f 2a3b 713d 302e 
	0x0130:  380d 0a41 6363 6570 742d 4c61 6e67 7561 
	0x0140:  6765 3a20 656e 2d75 732c 656e 3b71 3d30 
	0x0150:  2e35 0d0a 4163 6365 7074 2d45 6e63 6f64 
	0x0160:  696e 673a 2067 7a69 702c 6465 666c 6174 
	0x0170:  650d 0a41 6363 6570 742d 4368 6172 7365 
	0x0180:  743a 2049 534f 2d38 3835 392d 312c 7574 
	0x0190:  662d 383b 713d 302e 372c 2a3b 713d 302e 
	0x01a0:  370d 0a4b 6565 702d 416c 6976 653a 2033 
	0x01b0:  3030 0d0a 436f 6e6e 6563 7469 6f6e 3a20 
	0x01c0:  6b65 6570 2d61 6c69 7665 0d0a 582d 4d6f 
	0x01d0:  7a3a 206c 6976 6562 6f6f 6b6d 6172 6b73 
	0x01e0:  0d0a 436f 6f6b 6965 3a20 5f5f 7574 6d61 
	0x01f0:  3d31 3833 3835 3936 3432 2e31 3133 3835 
	0x0200:  3031 3035 362e 3132 3339 3636 3437 3833 
	0x0210:  2e31 3233 3936 3634 3738 332e 3132 3339 
	0x0220:  3636 3437 3833 2e31 3b20 5f5f 7574 6d7a 
	0x0230:  3d31 3833 3835 3936 3432 2e31 3233 3936 
	0x0240:  3635 3035 302e 312e 332e 7574 6d63 636e 
	0x0250:  3d28 6f72 6761 6e69 6329 7c75 746d 6373 
	0x0260:  723d 676f 6f67 6c65 7c75 746d 6374 723d 
	0x0270:  6669 7265 666f 782b 7769 6e64 6f77 732b 
	0x0280:  646f 776e 6c6f 6164 7c75 746d 636d 643d 
	0x0290:  6f72 6761 6e69 633b 2073 5f76 693d 5b43 
	0x02a0:  535d 7631 7c34 3945 3343 3841 3330 3030 
	0x02b0:  3033 4230 452d 4130 3230 3833 3530 3030 
	0x02c0:  3030 3032 325b 4345 5d0d 0a0d 0a 
11:53:58.230932 IP (tos 0x0, ttl 49, id 25762, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: ., cksum 0xcfa7 (correct), 1:1(0) ack 678 win 6770 
	0x0000:  4500 0028 64a2 4000 3106 11ca 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 360a 6d80 0f30 
	0x0020:  5010 1a72 cfa7 0000 0000 4b82 2e20 
11:53:58.233926 IP (tos 0x0, ttl 49, id 25763, offset 0, flags [DF], proto TCP (6), length 699) fxfeeds.www > UbuntuRob.45205: P, cksum 0x781c (correct), 1:660(659) ack 678 win 6770 
	0x0000:  4500 02bb 64a3 4000 3106 0f36 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 360a 6d80 0f30 
	0x0020:  5018 1a72 781c 0000 4854 5450 2f31 2e31 
	0x0030:  2033 3032 2046 6f75 6e64 0d0a 4578 7069 
	0x0040:  7265 733a 2054 7565 2c20 3034 2041 7567 
	0x0050:  2032 3031 3020 3137 3a34 393a 3535 2047 
	0x0060:  4d54 0d0a 436f 6e74 656e 742d 4c65 6e67 
	0x0070:  7468 3a20 3332 330d 0a44 6174 653a 2054 
	0x0080:  7565 2c20 3034 2041 7567 2032 3030 3920 
	0x0090:  3137 3a35 333a 3538 2047 4d54 0d0a 4c6f 
	0x00a0:  6361 7469 6f6e 3a20 6874 7470 3a2f 2f66 
	0x00b0:  7866 6565 6473 2e6d 6f7a 696c 6c61 2e63 
	0x00c0:  6f6d 2f66 6972 6566 6f78 2f68 6561 646c 
	0x00d0:  696e 6573 2e78 6d6c 0d0a 5365 7276 6572 
	0x00e0:  3a20 4170 6163 6865 2f32 2e32 2e33 2028 
	0x00f0:  5265 6420 4861 7429 0d0a 436f 6e74 656e 
	0x0100:  742d 5479 7065 3a20 7465 7874 2f68 746d 
	0x0110:  6c3b 2063 6861 7273 6574 3d69 736f 2d38 
	0x0120:  3835 392d 310d 0a4b 6565 702d 416c 6976 
	0x0130:  653a 2074 696d 656f 7574 3d32 302c 206d 
	0x0140:  6178 3d38 3931 0d0a 582d 4361 6368 652d 
	0x0150:  496e 666f 3a20 6361 6368 6564 0d0a 436f 
	0x0160:  6e6e 6563 7469 6f6e 3a20 4b65 6570 2d41 
	0x0170:  6c69 7665 0d0a 0d0a 3c21 444f 4354 5950 
	0x0180:  4520 4854 4d4c 2050 5542 4c49 4320 222d 
	0x0190:  2f2f 4945 5446 2f2f 4454 4420 4854 4d4c 
	0x01a0:  2032 2e30 2f2f 454e 223e 0a3c 6874 6d6c 
	0x01b0:  3e3c 6865 6164 3e0a 3c74 6974 6c65 3e33 
	0x01c0:  3032 2046 6f75 6e64 3c2f 7469 746c 653e 
	0x01d0:  0a3c 2f68 6561 643e 3c62 6f64 793e 0a3c 
	0x01e0:  6831 3e46 6f75 6e64 3c2f 6831 3e0a 3c70 
	0x01f0:  3e54 6865 2064 6f63 756d 656e 7420 6861 
	0x0200:  7320 6d6f 7665 6420 3c61 2068 7265 663d 
	0x0210:  2268 7474 703a 2f2f 6678 6665 6564 732e 
	0x0220:  6d6f 7a69 6c6c 612e 636f 6d2f 6669 7265 
	0x0230:  666f 782f 6865 6164 6c69 6e65 732e 786d 
	0x0240:  6c22 3e68 6572 653c 2f61 3e2e 3c2f 703e 
	0x0250:  0a3c 6872 3e0a 3c61 6464 7265 7373 3e41 
	0x0260:  7061 6368 652f 322e 322e 3320 2852 6564 
	0x0270:  2048 6174 2920 5365 7276 6572 2061 7420 
	0x0280:  656e 2d75 732e 6678 6665 6564 732e 6d6f 
	0x0290:  7a69 6c6c 612e 636f 6d20 506f 7274 2038 
	0x02a0:  303c 2f61 6464 7265 7373 3e0a 3c2f 626f 
	0x02b0:  6479 3e3c 2f68 746d 6c3e 0a 
11:53:58.233939 IP (tos 0x0, ttl 64, id 35706, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xcdc8 (correct), 678:678(0) ack 660 win 6590 
	0x0000:  4500 0028 8b7a 4000 4006 dbf1 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389d 
	0x0020:  5010 19be cdc8 0000 
11:53:58.272636 IP (tos 0x0, ttl 64, id 13532, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.45206 > fxfeeds.www: S, cksum 0xf9b6 (correct), 1846263031:1846263031(0) win 5840 <mss 1460,sackOK,timestamp 100395 0,nop,wscale 6> 
	0x0000:  4500 003c 34dc 4000 4006 327c c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf7 0000 0000 
	0x0020:  a002 16d0 f9b6 0000 0204 05b4 0402 080a 
	0x0030:  0001 882b 0000 0000 0103 0306 
11:53:58.331994 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.www > UbuntuRob.45206: S, cksum 0x8026 (correct), 1813833140:1813833140(0) ack 1846263032 win 5840 <mss 1460> 
	0x0000:  4500 002c 0000 4000 3106 7668 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b4 6e0b bcf8 
	0x0020:  6012 16d0 8026 0000 0204 05b4 9adc 
11:53:58.332037 IP (tos 0x0, ttl 64, id 13533, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x97e3 (correct), 1:1(0) ack 1 win 5840 
	0x0000:  4500 0028 34dd 4000 4006 328f c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf8 6c1c e5b5 
	0x0020:  5010 16d0 97e3 0000 
11:53:58.332119 IP (tos 0x0, ttl 64, id 13534, offset 0, flags [DF], proto TCP (6), length 683) UbuntuRob.45206 > fxfeeds.www: P, cksum 0x0a18 (correct), 1:644(643) ack 1 win 5840 
	0x0000:  4500 02ab 34de 4000 4006 300b c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bcf8 6c1c e5b5 
	0x0020:  5018 16d0 0a18 0000 4745 5420 2f66 6972 
	0x0030:  6566 6f78 2f68 6561 646c 696e 6573 2e78 
	0x0040:  6d6c 2048 5454 502f 312e 310d 0a48 6f73 
	0x0050:  743a 2066 7866 6565 6473 2e6d 6f7a 696c 
	0x0060:  6c61 2e63 6f6d 0d0a 5573 6572 2d41 6765 
	0x0070:  6e74 3a20 4d6f 7a69 6c6c 612f 352e 3020 
	0x0080:  2858 3131 3b20 553b 204c 696e 7578 2069 
	0x0090:  3638 363b 2065 6e2d 5553 3b20 7276 3a31 
	0x00a0:  2e39 2e30 2e31 3129 2047 6563 6b6f 2f32 
	0x00b0:  3030 3930 3630 3330 3920 5562 756e 7475 
	0x00c0:  2f38 2e30 3420 2868 6172 6479 2920 4669 
	0x00d0:  7265 666f 782f 332e 302e 3131 0d0a 4163 
	0x00e0:  6365 7074 3a20 7465 7874 2f68 746d 6c2c 
	0x00f0:  6170 706c 6963 6174 696f 6e2f 7868 746d 
	0x0100:  6c2b 786d 6c2c 6170 706c 6963 6174 696f 
	0x0110:  6e2f 786d 6c3b 713d 302e 392c 2a2f 2a3b 
	0x0120:  713d 302e 380d 0a41 6363 6570 742d 4c61 
	0x0130:  6e67 7561 6765 3a20 656e 2d75 732c 656e 
	0x0140:  3b71 3d30 2e35 0d0a 4163 6365 7074 2d45 
	0x0150:  6e63 6f64 696e 673a 2067 7a69 702c 6465 
	0x0160:  666c 6174 650d 0a41 6363 6570 742d 4368 
	0x0170:  6172 7365 743a 2049 534f 2d38 3835 392d 
	0x0180:  312c 7574 662d 383b 713d 302e 372c 2a3b 
	0x0190:  713d 302e 370d 0a4b 6565 702d 416c 6976 
	0x01a0:  653a 2033 3030 0d0a 436f 6e6e 6563 7469 
	0x01b0:  6f6e 3a20 6b65 6570 2d61 6c69 7665 0d0a 
	0x01c0:  436f 6f6b 6965 3a20 5f5f 7574 6d61 3d31 
	0x01d0:  3833 3835 3936 3432 2e31 3133 3835 3031 
	0x01e0:  3035 362e 3132 3339 3636 3437 3833 2e31 
	0x01f0:  3233 3936 3634 3738 332e 3132 3339 3636 
	0x0200:  3437 3833 2e31 3b20 5f5f 7574 6d7a 3d31 
	0x0210:  3833 3835 3936 3432 2e31 3233 3936 3635 
	0x0220:  3035 302e 312e 332e 7574 6d63 636e 3d28 
	0x0230:  6f72 6761 6e69 6329 7c75 746d 6373 723d 
	0x0240:  676f 6f67 6c65 7c75 746d 6374 723d 6669 
	0x0250:  7265 666f 782b 7769 6e64 6f77 732b 646f 
	0x0260:  776e 6c6f 6164 7c75 746d 636d 643d 6f72 
	0x0270:  6761 6e69 633b 2073 5f76 693d 5b43 535d 
	0x0280:  7631 7c34 3945 3343 3841 3330 3030 3033 
	0x0290:  4230 452d 4130 3230 3833 3530 3030 3030 
	0x02a0:  3032 325b 4345 5d0d 0a0d 0a 
11:53:58.398472 IP (tos 0x0, ttl 49, id 25766, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: ., cksum 0x908f (correct), 1:1(0) ack 644 win 7073 
	0x0000:  4500 0028 64a6 4000 3106 11c6 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b5 6e0b bf7b 
	0x0020:  5010 1ba1 908f 0000 0000 9c68 95c0 
11:53:58.402401 IP (tos 0x0, ttl 49, id 25767, offset 0, flags [DF], proto TCP (6), length 741) fxfeeds.www > UbuntuRob.45206: P, cksum 0x9835 (correct), 1:702(701) ack 644 win 7073 
	0x0000:  4500 02e5 64a7 4000 3106 0f08 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e5b5 6e0b bf7b 
	0x0020:  5018 1ba1 9835 0000 4854 5450 2f31 2e31 
	0x0030:  2033 3032 2046 6f75 6e64 0d0a 4578 7069 
	0x0040:  7265 733a 2054 7565 2c20 3034 2041 7567 
	0x0050:  2032 3031 3020 3137 3a35 333a 3537 2047 
	0x0060:  4d54 0d0a 436f 6e74 656e 742d 4c65 6e67 
	0x0070:  7468 3a20 3334 310d 0a44 6174 653a 2054 
	0x0080:  7565 2c20 3034 2041 7567 2032 3030 3920 
	0x0090:  3137 3a35 333a 3538 2047 4d54 0d0a 4c6f 
	0x00a0:  6361 7469 6f6e 3a20 6874 7470 3a2f 2f6e 
	0x00b0:  6577 7372 7373 2e62 6263 2e63 6f2e 756b 
	0x00c0:  2f72 7373 2f6e 6577 736f 6e6c 696e 655f 
	0x00d0:  776f 726c 645f 6564 6974 696f 6e2f 6672 
	0x00e0:  6f6e 745f 7061 6765 2f72 7373 2e78 6d6c 
	0x00f0:  0d0a 5365 7276 6572 3a20 4170 6163 6865 
	0x0100:  2f32 2e32 2e33 2028 5265 6420 4861 7429 
	0x0110:  0d0a 436f 6e74 656e 742d 5479 7065 3a20 
	0x0120:  7465 7874 2f68 746d 6c3b 2063 6861 7273 
	0x0130:  6574 3d69 736f 2d38 3835 392d 310d 0a4b 
	0x0140:  6565 702d 416c 6976 653a 2074 696d 656f 
	0x0150:  7574 3d32 302c 206d 6178 3d38 3732 0d0a 
	0x0160:  582d 4361 6368 652d 496e 666f 3a20 6361 
	0x0170:  6368 6564 0d0a 436f 6e6e 6563 7469 6f6e 
	0x0180:  3a20 4b65 6570 2d41 6c69 7665 0d0a 0d0a 
	0x0190:  3c21 444f 4354 5950 4520 4854 4d4c 2050 
	0x01a0:  5542 4c49 4320 222d 2f2f 4945 5446 2f2f 
	0x01b0:  4454 4420 4854 4d4c 2032 2e30 2f2f 454e 
	0x01c0:  223e 0a3c 6874 6d6c 3e3c 6865 6164 3e0a 
	0x01d0:  3c74 6974 6c65 3e33 3032 2046 6f75 6e64 
	0x01e0:  3c2f 7469 746c 653e 0a3c 2f68 6561 643e 
	0x01f0:  3c62 6f64 793e 0a3c 6831 3e46 6f75 6e64 
	0x0200:  3c2f 6831 3e0a 3c70 3e54 6865 2064 6f63 
	0x0210:  756d 656e 7420 6861 7320 6d6f 7665 6420 
	0x0220:  3c61 2068 7265 663d 2268 7474 703a 2f2f 
	0x0230:  6e65 7773 7273 732e 6262 632e 636f 2e75 
	0x0240:  6b2f 7273 732f 6e65 7773 6f6e 6c69 6e65 
	0x0250:  5f77 6f72 6c64 5f65 6469 7469 6f6e 2f66 
	0x0260:  726f 6e74 5f70 6167 652f 7273 732e 786d 
	0x0270:  6c22 3e68 6572 653c 2f61 3e2e 3c2f 703e 
	0x0280:  0a3c 6872 3e0a 3c61 6464 7265 7373 3e41 
	0x0290:  7061 6368 652f 322e 322e 3320 2852 6564 
	0x02a0:  2048 6174 2920 5365 7276 6572 2061 7420 
	0x02b0:  6678 6665 6564 732e 6d6f 7a69 6c6c 612e 
	0x02c0:  636f 6d20 506f 7274 2038 303c 2f61 6464 
	0x02d0:  7265 7373 3e0a 3c2f 626f 6479 3e3c 2f68 
	0x02e0:  746d 6c3e 0a 
11:53:58.402417 IP (tos 0x0, ttl 64, id 13535, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e11 (correct), 644:644(0) ack 702 win 7010 
	0x0000:  4500 0028 34df 4000 4006 328d c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e872 
	0x0020:  5010 1b62 8e11 0000 
11:53:58.425581 IP (tos 0x0, ttl 64, id 20744, offset 0, flags [DF], proto TCP (6), length 60) UbuntuRob.40742 > newslb308.www: S, cksum 0x495c (correct), 1846991193:1846991193(0) win 5840 <mss 1460,sackOK,timestamp 100433 0,nop,wscale 6> 
	0x0000:  4500 003c 5108 4000 4006 7118 c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d959 0000 0000 
	0x0020:  a002 16d0 495c 0000 0204 05b4 0402 080a 
	0x0030:  0001 8851 0000 0000 0103 0306 
11:53:58.611909 IP (tos 0x0, ttl 44, id 0, offset 0, flags [DF], proto TCP (6), length 60) newslb308.www > UbuntuRob.40742: S, cksum 0x6419 (correct), 737567975:737567975(0) ack 1846991194 win 5792 <mss 1460,sackOK,timestamp 1244334680 100433,nop,wscale 7> 
	0x0000:  4500 003c 0000 4000 2c06 d620 d43a e24f 
	0x0010:  c0a8 0169 0050 9f26 2bf6 64e7 6e16 d95a 
	0x0020:  a012 16a0 6419 0000 0204 05b4 0402 080a 
	0x0030:  4a2b 0a58 0001 8851 0103 0307 
11:53:58.611962 IP (tos 0x0, ttl 64, id 20745, offset 0, flags [DF], proto TCP (6), length 52) UbuntuRob.40742 > newslb308.www: ., cksum 0xa8fa (correct), 1:1(0) ack 1 win 92 <nop,nop,timestamp 100480 1244334680> 
	0x0000:  4500 0034 5109 4000 4006 711f c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d95a 2bf6 64e8 
	0x0020:  8010 005c a8fa 0000 0101 080a 0001 8880 
	0x0030:  4a2b 0a58 
11:53:58.612046 IP (tos 0x0, ttl 64, id 20746, offset 0, flags [DF], proto TCP (6), length 733) UbuntuRob.40742 > newslb308.www: P, cksum 0xf204 (correct), 1:682(681) ack 1 win 92 <nop,nop,timestamp 100480 1244334680> 
	0x0000:  4500 02dd 510a 4000 4006 6e75 c0a8 0169 
	0x0010:  d43a e24f 9f26 0050 6e16 d95a 2bf6 64e8 
	0x0020:  8018 005c f204 0000 0101 080a 0001 8880 
	0x0030:  4a2b 0a58 4745 5420 2f72 7373 2f6e 6577 
	0x0040:  736f 6e6c 696e 655f 776f 726c 645f 6564 
	0x0050:  6974 696f 6e2f 6672 6f6e 745f 7061 6765 
	0x0060:  2f72 7373 2e78 6d6c 2048 5454 502f 312e 
	0x0070:  310d 0a48 6f73 743a 206e 6577 7372 7373 
	0x0080:  2e62 6263 2e63 6f2e 756b 0d0a 5573 6572 
	0x0090:  2d41 6765 6e74 3a20 4d6f 7a69 6c6c 612f 
	0x00a0:  352e 3020 2858 3131 3b20 553b 204c 696e 
	0x00b0:  7578 2069 3638 363b 2065 6e2d 5553 3b20 
	0x00c0:  7276 3a31 2e39 2e30 2e31 3129 2047 6563 
	0x00d0:  6b6f 2f32 3030 3930 3630 3330 3920 5562 
	0x00e0:  756e 7475 2f38 2e30 3420 2868 6172 6479 
	0x00f0:  2920 4669 7265 666f 782f 332e 302e 3131 
	0x0100:  0d0a 4163 6365 7074 3a20 7465 7874 2f68 
	0x0110:  746d 6c2c 6170 706c 6963 6174 696f 6e2f 
	0x0120:  7868 746d 6c2b 786d 6c2c 6170 706c 6963 
	0x0130:  6174 696f 6e2f 786d 6c3b 713d 302e 392c 
	0x0140:  2a2f 2a3b 713d 302e 380d 0a41 6363 6570 
	0x0150:  742d 4c61 6e67 7561 6765 3a20 656e 2d75 
	0x0160:  732c 656e 3b71 3d30 2e35 0d0a 4163 6365 
	0x0170:  7074 2d45 6e63 6f64 696e 673a 2067 7a69 
	0x0180:  702c 6465 666c 6174 650d 0a41 6363 6570 
	0x0190:  742d 4368 6172 7365 743a 2049 534f 2d38 
	0x01a0:  3835 392d 312c 7574 662d 383b 713d 302e 
	0x01b0:  372c 2a3b 713d 302e 370d 0a4b 6565 702d 
	0x01c0:  416c 6976 653a 2033 3030 0d0a 436f 6e6e 
	0x01d0:  6563 7469 6f6e 3a20 6b65 6570 2d61 6c69 
	0x01e0:  7665 0d0a 436f 6f6b 6965 3a20 4242 432d 
	0x01f0:  5549 443d 3334 3839 3539 6561 3330 6338 
	0x0200:  3037 3964 3834 3663 6439 6338 3031 3136 
	0x0210:  6165 3965 3939 6566 6137 3736 3830 3930 
	0x0220:  3431 3636 3033 6335 6435 6263 3238 3135 
	0x0230:  3865 3561 304d 6f7a 696c 6c61 2532 6635 
	0x0240:  2532 6530 2532 3025 3238 5831 3125 3362 
	0x0250:  2532 3055 2533 6225 3230 4c69 6e75 7825 
	0x0260:  3230 6936 3836 2533 6225 3230 656e 2532 
	0x0270:  6455 5325 3362 2532 3072 7625 3361 3125 
	0x0280:  3265 3925 3265 3025 3265 3625 3239 2532 
	0x0290:  3047 6563 6b6f 2532 6632 3030 3930 3230 
	0x02a0:  3931 3125 3230 5562 756e 7475 2532 6638 
	0x02b0:  2532 6530 3425 3230 2532 3868 6172 6479 
	0x02c0:  2532 3925 3230 4669 7265 666f 7825 3266 
	0x02d0:  3325 3265 3025 3265 360d 0a0d 0a 
11:53:58.782117 IP (tos 0x0, ttl 44, id 25770, offset 0, flags [DF], proto TCP (6), length 52) newslb308.www > UbuntuRob.40742: ., cksum 0xa5bf (correct), 1:1(0) ack 682 win 56 <nop,nop,timestamp 1244334862 100480> 
	0x0000:  4500 0034 64aa 4000 2c06 717e d43a e24f 
	0x0010:  c0a8 0169 0050 9f26 2bf6 64e8 6e16 dc03 
	0x0020:  8010 0038 a5bf 0000 0101 080a 4a2b 0b0e 
	0x0030:  0001 8880 
11:54:08.358861 IP (tos 0x0, ttl 49, id 39284, offset 0, flags [DF], proto TCP (6), length 570) giraffe.www > UbuntuRob.55887: FP, cksum 0xd2b1 (correct), 1294782094:1294782612(518) ack 1755973055 win 2036 <nop,nop,timestamp 2743964920 99086> 
	0x0000:  4500 023a 9974 4000 3106 5d8f 3ff7 4eb2 
	0x0010:  c0a8 0169 0050 da4f 4d2c ce8e 68aa 05bf 
	0x0020:  8019 07f4 d2b1 0000 0101 080a a38d 94f8 
	0x0030:  0001 830e fa1f 6fb4 869b 03dc 84b1 c485 
	0x0040:  7980 eb74 baf6 32a3 0662 fd8d 63e4 6a3a 
	0x0050:  0240 d06c 7061 ce06 f43f 4c91 a7e9 b928 
	0x0060:  9920 9233 854d 63ab e879 1eb7 dc7c 9748 
	0x0070:  e454 0a21 a16b 7fd8 0868 809a bdc1 81bf 
	0x0080:  a551 7dff bc55 685e 5ad2 712a 0587 1585 
	0x0090:  bcb5 44c4 118d 36df eb23 149d c8fc 51a5 
	0x00a0:  ee5b 4358 cfd8 ce8d cc63 fb5a af8e 69cc 
	0x00b0:  3330 0158 5c3d 86f3 7b96 3045 c5b8 b2aa 
	0x00c0:  5e0c 4748 aaf0 e7e5 effa ba6b 8049 88a9 
	0x00d0:  d146 fdb5 f7a4 1657 e5c9 ef09 6698 0f52 
	0x00e0:  debc 241b afd0 ecae 7b5d 876e 2f03 99c2 
	0x00f0:  2b38 8898 33ae e874 cada 77ab ffc4 49d6 
	0x0100:  4e98 c61b 84b0 dde9 918c 4559 db44 4e10 
	0x0110:  f4ec e2cb f5c5 57f8 f980 6808 bf37 9372 
	0x0120:  26d8 98c6 e348 703c 3443 e2a5 f9c4 3fec 
	0x0130:  1c87 bdde 7137 3ce8 f58e 8ec2 d7de 4985 
	0x0140:  74c9 63f3 85e2 a8db ab0e cf19 9e3f 183f 
	0x0150:  0eab c358 d050 030c f477 c7e1 9866 1b68 
	0x0160:  281e cea2 8063 13c1 f006 3c80 50f1 c6ef 
	0x0170:  847e e7a8 4fae f0c3 6c55 56c8 f709 14b1 
	0x0180:  b0aa 77d8 0d0f dfbc 7e73 d45d 8342 2691 
	0x0190:  6a3c 8135 70e4 8126 347f 3bf3 339c 7b17 
	0x01a0:  e2bf ed39 f359 d1ad 7cf7 6e7b 1625 6dc6 
	0x01b0:  cd95 b093 c565 7eb0 f1d1 e37e abec 111b 
	0x01c0:  d75d 80c1 4048 e36e db32 c856 49ec 3e17 
	0x01d0:  b721 e2bb d920 9b43 8344 63fb 8567 aff2 
	0x01e0:  3967 1094 4e5b 70ad 829b e865 807d 0ad1 
	0x01f0:  6d05 a928 33b8 3994 a53c 41b8 26df d97b 
	0x0200:  ec7e 467b e31c e2b7 51d7 b7b7 7eaf db79 
	0x0210:  f3fa c0ef 805a 2c93 6b45 a31b a6c0 fd37 
	0x0220:  05c7 4f03 d883 401c 1ded fd17 0000 ffff 
	0x0230:  0300 7ee0 f6e7 c020 0000 
11:54:08.358904 IP (tos 0x0, ttl 64, id 33671, offset 0, flags [DF], proto TCP (6), length 64) UbuntuRob.55887 > giraffe.www: ., cksum 0xcd79 (correct), 1:1(0) ack 4294964400 win 109 <nop,nop,timestamp 102916 2743949696,nop,nop,sack 1 {0:519}> 
	0x0000:  4500 0040 8387 4000 4006 6676 c0a8 0169 
	0x0010:  3ff7 4eb2 da4f 0050 68aa 05bf 4d2c c33e 
	0x0020:  b010 006d cd79 0000 0101 080a 0001 9204 
	0x0030:  a38d 5980 0101 050a 4d2c ce8e 4d2c d095 
11:54:09.421091 IP (tos 0x0, ttl 49, id 56555, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: F, cksum 0xcd13 (correct), 660:660(0) ack 678 win 6770 
	0x0000:  4500 0028 dceb 4000 3106 9980 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 389d 6d80 0f30 
	0x0020:  5011 1a72 cd13 0000 0000 7d4c 5a52 
11:54:09.459442 IP (tos 0x0, ttl 64, id 35707, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: ., cksum 0xcdc7 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7b 4000 4006 dbf0 c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5010 19be cdc7 0000 
11:54:11.018091 IP (tos 0x0, ttl 49, id 12096, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: F, cksum 0x8dd1 (correct), 702:702(0) ack 644 win 7073 
	0x0000:  4500 0028 2f40 4000 3106 472c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e872 6e0b bf7b 
	0x0020:  5011 1ba1 8dd1 0000 0000 29bd 7e61 
11:54:11.055445 IP (tos 0x0, ttl 64, id 13536, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e10 (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e0 4000 4006 328c c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5010 1b62 8e10 0000 
11:54:11.280927 IP (tos 0x0, ttl 49, id 12097, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: F, cksum 0x8dd1 (correct), 702:702(0) ack 644 win 7073 
	0x0000:  4500 0028 2f41 4000 3106 472b 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e872 6e0b bf7b 
	0x0020:  5011 1ba1 8dd1 0000 0000 0130 39c9 
11:54:11.280966 IP (tos 0x0, ttl 64, id 13537, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: ., cksum 0x8e10 (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e1 4000 4006 328b c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5010 1b62 8e10 0000 
11:54:22.433008 IP (tos 0x0, ttl 64, id 13538, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: F, cksum 0x8e0f (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e2 4000 4006 328a c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5011 1b62 8e0f 0000 
11:54:22.433053 IP (tos 0x0, ttl 64, id 35708, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: F, cksum 0xcdc6 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7c 4000 4006 dbef c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5011 19be cdc6 0000 
11:54:22.695497 IP (tos 0x0, ttl 64, id 13539, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45206 > fxfeeds.www: F, cksum 0x8e0f (correct), 644:644(0) ack 703 win 7010 
	0x0000:  4500 0028 34e3 4000 4006 3289 c0a8 0169 
	0x0010:  3ff5 d15d b096 0050 6e0b bf7b 6c1c e873 
	0x0020:  5011 1b62 8e0f 0000 
11:54:22.699470 IP (tos 0x0, ttl 64, id 35709, offset 0, flags [DF], proto TCP (6), length 40) UbuntuRob.45205 > fxfeeds.www: F, cksum 0xcdc6 (correct), 678:678(0) ack 661 win 6590 
	0x0000:  4500 0028 8b7d 4000 4006 dbee c0a8 0169 
	0x0010:  3ff5 d15d b095 0050 6d80 0f30 8eb6 389e 
	0x0020:  5011 19be cdc6 0000 
11:54:22.898539 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45206: ., cksum 0x8dd0 (correct), 703:703(0) ack 645 win 7073 
	0x0000:  4500 0028 0000 4000 3106 766c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b096 6c1c e873 6e0b bf7c 
	0x0020:  5010 1ba1 8dd0 0000 0000 7653 2140 
11:54:22.899955 IP (tos 0x0, ttl 49, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.www > UbuntuRob.45205: ., cksum 0xcd12 (correct), 661:661(0) ack 679 win 6770 
	0x0000:  4500 0028 0000 4000 3106 766c 3ff5 d15d 
	0x0010:  c0a8 0169 0050 b095 8eb6 389e 6d80 0f31 
	0x0020:  5010 1a72 cd12 0000 0000 f04e eff5 

```

---

### Post by jonobr on 2009-08-04
Hello


What websites did you test to in this test you performed?

---

### Post by jonobr on 2009-08-04
Addtional,

would you be abler to share the results of 
cat /etc/hosts
and 
cat /etc/nsswitch.conf

lastly do you have some news feed add-ons on your browsers or adblock?
Could you disable temporarily for the purposes of testing?

I dont think its it, but no harm trying

---

### Post by RobFS1 on 2009-08-04
here is from /ect/hosts

```
127.0.0.1 localhost 
127.0.1.1 Ubuntu:Rob 

# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts

```

and here is from /ect/nsswitch.conf

```
# /etc/nsswitch.conf 
# 
# Example configuration of GNU Name Service Switch functionality. 
# If you have the `glibc-doc-reference' and `info' packages installed, try: 
# `info libc "Name Service Switch"' for information about this file. 

passwd:         compat 
group:          compat 
shadow:         compat 

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 
networks:       files 

protocols:      db files 
services:       db files 
ethers:         db files 
rpc:            db files 

netgroup:       nis

```

I think that i that testing on either google or facebook.

---

### Post by jonobr on 2009-08-04
mmmmm.

Im not sure Ubuntu:Rob  is a valid hostname.

Im not sure.

Maybe you could try changing that hostname to something else.
without any special characters


```
sudo gedit /etc/hostname
```

and then

```
sudo gedit /etc/hosts
```
 then reboot

---

### Post by RobFS1 on 2009-08-04
Will that make a difference?

---

### Post by RobFS1 on 2009-08-04
Tried it and it didn't fix

---

### Post by lswb on 2009-08-04
How is your system connected to the web? DSL, cable modem, or ? Is there a router? connection sharing with another system?

---

### Post by RobFS1 on 2009-08-05
My internet comes from what my dad calls an "antenna" because it receives signal from the water tower in the middle of my town. From there the signal goes to a router that serves four total computers; three computers from a wired connection (mine, my mom's, and my dad's) and one from a wireless connection (my sister's). My computer is dual booted with Ubuntu 8.04, and Windows XP; My dad's computer is Ubuntu 8.04; my mom's computer is Window's XP; and my sister's computer is Window's Vista. All of the internet connections work except for mine, which can only access Google based websites as the beginning of this thread states. Albeit there is an Ethernet switch that i used in between the router and my computer only, but that worked before i dual booted, and all of my problems with not being able to access sites started when i installed an Ethernet driver on the Windows XP partition of my dual booted system. Hopefully that helps you guys, and thanks for helping me.:)

---

### Post by lswb on 2009-08-05
So your computer won't connect regardless of whether windows or ubuntu is running? I'm a little unclear of what's going on here. Why did you replace the ethernet driver? 

Do you know your ethernet interface name? It is usually eth0. If so, and just as a wild guess, issue this command:

sudo ifconfig eth0 mtu 1450

and see if that makes any difference.

If not, can you post the output of "sudo ifconfig" from your computer and from your dad's system?

also "cat /etc/resolv.conf" from both systems. If you have ever edited /etc/network/interfaces, post that as well.

---

### Post by RobFS1 on 2009-08-05
w00t! THANK YOU lswb! You fixed it with the "sudo ifconfig eth0 mtu 1450" command!\\:D/=D>:biggrin: Thank You! Please though, can you tell me what that command does? I am eager to learn about how it was that you fixed my problem. Thanks!

---

### Post by lswb on 2009-08-05
Well, I said it was a guess. A normal ethernet packet has an mtu or "Maximum Transmission Unit" size of 1500 bytes. Sometimes an ISP provides the connection to the internet in the form of "pppoe", "Point to Point Protocol Over Ethernet" In that situation, the MTU must be reduced to 1492 or less, because the pppoe encapsulation of the ethernet packet requires an 8 byte header. So if this is the case, packets of 1492 or less bytes can still go through, but the router will not pass the larger packets. For some reason google always uses a smaller packet size, so their site is always available. I've seen that behavior before, so that's what made me suggest the mtu change.

Now, your router *should* tell your computer about the correct mtu size when it connects, why it is not doing so is another question. You may need to do something to the router configuration if you want to correct that. In the meantime, you can just put the line "ifconfig eth0 mtu 1450" in the file /etc/rc.local (must be edited as root) somewhere before the last line that says "exit", and it will be executed at every reboot.

---

### Post by jonobr on 2009-08-05
Mmmmm IM only getting to this now, :-(


Im surprised that Google worked?


I figured it was some limitation of access to websites which points towards ad blockers, hosts file, nsswitch.conf etc.

I was on the wrong track completly

Cheers

---

