---
title: "Gigabit network sometimes 15 MB /s others 85 MB /s"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Elchbulle on 2009-02-06
Anyone have any ideas on what I can try with my setup?  Between the same two machines on my network it's hit or miss as far as what speeds I will see.  The size of the files don't matter, they come from the same directory for the most part, no noticeable difference in the actual files.

Sometimes when I transfer it will get a nice 85 MB / sec through the whole file (and sometimes they are 30 GB files) whereas other times it will get 13 - 15 MB / sec tops. 

The card on the ubuntu side is a 88E80001 Gigabit card.  It's an onboard nic.  All my switches are gigabit, netgear and linksys.  Between my windows machines it gets a good 50 - 80 MB / sec.  

I can't figure it out for the life of me, do you think it's just a flaky card?  It never times out or stops working...

Thanks for any and all help!
Tim

---

### Post by cariboo on 2009-02-07
My personal feeling is that nautilus is the problem. Using iperf I get tansfer speed that is expected

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 56435 connected with 192.168.1.200 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    114 MBytes  95.7 Mbits/sec
```

The test is run from the command line, whereas using sftp or samba and nautilus the maximum I've seen is 48Mbps

Iperf is available in the repositories.

Jim

---

### Post by Elchbulle on 2009-02-07
Thanks for the reply!  I'm still fairly n00bish to this stuff, I have samba set up for the shares but I think nautilus is installed on the system... is there something specific I should configure?  The transfers I refer to are between my ubuntu box and a windows vista machine.

---

### Post by Elchbulle on 2009-02-07
Here are my results from iperf, with windows as the server it is getting horrible speeds, but the other way around it's even WORSE with the 16 Mb.  Any suggestions?


```
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Micro\Desktop>iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
OpenSCManager failed - Access is denied. (0x5)
[164] local 192.168.0.196 port 5001 connected with 192.168.0.197 port 53816
[ ID] Interval       Transfer     Bandwidth
[164]  0.0-10.1 sec  92.7 MBytes  77.2 Mbits/sec

C:\Users\Micro\Desktop>iperf -c micro-ubuntu
------------------------------------------------------------
Client connecting to micro-ubuntu, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[304] local 192.168.0.196 port 61045 connected with 192.168.0.197 port 5001
[ ID] Interval       Transfer     Bandwidth
[304]  0.0-10.0 sec  19.3 MBytes  16.2 Mbits/sec

C:\Users\Micro\Desktop>
```

---

### Post by thieaux on 2009-06-13
TCP WINDOWS SIZE IS YOUR ISSUE set both client and server to 16kB and let us know......

---

### Post by Elchbulle on 2009-06-15
Thanks for the reply!  I figured as much, the problem I am having now is finding a way to adjust the window size in Vista?  I have yet to find a site documenting how to do it, I have done it in XP before....

Anyone know for sure?  Just a registry change?

---

