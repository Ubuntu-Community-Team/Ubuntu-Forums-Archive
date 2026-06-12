---
title: "Help - Tcpdump analisys"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Summer88 on 2010-01-26
Goodmorning,
I'm in trouble with a gigabit network that runs at 54MB/ps with nc and iperf, but decrease at 16-18 MB/ps over Samba(also sometime in random the speed decrease even more until 5MB/ps).

CPU works at 40% when file transfer is active.
Disk speed 90 MB/ps.

I've already check that isn't an hardware problem.

So I'm tryng to debug the situation with tcpdump, but I'm a newbye... so I kindly demand some help

```

SMB PACKET: SMBreadX (REQUEST)
SMB Command   =  0x2E         
Error class   =  0x0          
Error code    =  0 (0x0)      
Flags1        =  0x0          
Flags2        =  0x1          
WARNING: Short packet. Try increasing the snap length
[|SMB]                                               
14:59:44.020538 00:40:63:f7:4a:07 > 00:11:d8:1c:91:8c, ethertype IPv4 (0x0800), length 1514: (tos 0x0, ttl 64, id 26451, offset 0, flags [DF], proto TCP (6), length 1500)
     Server.445 > Client.6921: Flags [.], seq 130124004:130125452, ack 469063, win 22, options [nop,nop,TS val 783283664 ecr 5867456], length 1448WARNING: Packet is continued in later TCP segments

SMB PACKET: SMBreadX (REPLY)
SMB Command   =  0x2E
Error class   =  0x0
Error code    =  0 (0x0)
Flags1        =  0x80
Flags2        =  0x1
WARNING: Short packet. Try increasing the snap length
[|SMB]
14:59:44.020548 00:40:63:f7:4a:07 > 00:11:d8:1c:91:8c, ethertype IPv4 (0x0800), length 1514: (tos 0x0, ttl 64, id 26452, offset 0, flags [DF], proto TCP (6), length 1500)
     Server.445 > Client.6921: Flags [.], seq 130125452:130126900, ack 469063, win 22, options [nop,nop,TS val 783283664 ecr 5867456], length 1448SMB-over-TCP packet:(raw data or continuation?)

14:59:44.020556 00:40:63:f7:4a:07 > 00:11:d8:1c:91:8c, ethertype IPv4 (0x0800), length 1514: (tos 0x0, ttl 64, id 26453, offset 0, flags [DF], proto TCP (6), length 1500)
    Server.445 > Client.6921: Flags [.], seq 130126900:130128348, ack 469063, win 22, options [nop,nop,TS val 783283664 ecr 5867456], length 1448SMB-over-TCP packet:(raw data or continuation?)

^C
69491 packets captured
195249 packets received by filter
125758 packets dropped by kernel

```

I don't get the means of that raw data or continuation question and "Try increasing the snap length".

Thanks in advance! kindly regards

---

### Post by epicac on 2010-10-29
Hi,

not sure I answer your question :)

tcpdump does have a default capture size for the packets. If a packet is bigger than that size you will not capture the whole packet. snaplen sets the biggest size you will capture.

use this option to make sure you capture the whole packet
-s 0

/C

---

