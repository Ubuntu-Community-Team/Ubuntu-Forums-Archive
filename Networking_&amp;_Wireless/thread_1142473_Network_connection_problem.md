---
title: "Network connection problem"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by yogi4 on 2009-04-29
Hi i m using ubuntu 8.10 ,yesterday i hd install a bunch of softwares from add & remove program but after that i am not able to open ny website after connecting to net through wifi when i try to ping it is giving send msg:operation not permitted. i dont know which programm is blocking pls help me out.

---

### Post by sahabcse on 2009-04-29
tail -f /var/log/messages

---

### Post by yogi4 on 2009-04-29
Well even after doing this m facing d same problem

---

### Post by lisati on 2009-04-29
> **sahabcse said:**
> tail -f /var/log/messages

> **yogi4 said:**
> Well even after doing this m facing d same problem

I'm about to sign off for the night, but I think posting the output from the tail command might be of some use to those who wish to help.

---

### Post by yogi4 on 2009-04-29
k i got it but after running d tail command the output was very long & it was keep on running in infinite loop. i will paste it now

---

### Post by yogi4 on 2009-04-29
Here is d tail output
Apr 29 17:53:52 yogesh-laptop kernel: [  137.606751] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:77:d0:eb:8a:08:00 SRC=172.16.36.206 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=5981 PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 29 17:53:52 yogesh-laptop kernel: [  137.807380] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:77:d0:eb:8a:08:00 SRC=172.16.36.206 DST=172.16.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=5985 PROTO=UDP SPT=137 DPT=137 LEN=76 
Apr 29 17:53:52 yogesh-laptop kernel: [  137.808550] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:5c:12:0e:7d:08:00 SRC=172.16.38.1 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=1112 PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 29 17:53:52 yogesh-laptop kernel: [  138.115443] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:5c:12:0e:7d:08:00 SRC=172.16.38.1 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=1119 PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 29 17:53:52 yogesh-laptop kernel: [  138.116630] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:68:d2:cf:03:08:00 SRC=172.16.36.155 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=310 PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 29 17:53:53 yogesh-laptop kernel: [  138.626421] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:5c:12:0e:7d:08:00 SRC=172.16.38.1 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=1121 PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 29 17:53:53 yogesh-laptop kernel: [  139.138436] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:68:d2:cf:03:08:00 SRC=172.16.36.155 DST=172.16.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=313 PROTO=UDP SPT=137 DPT=137 LEN=58

---

### Post by yogi4 on 2009-04-29
Will somebody help me out here...
i cant use my ubuntu untill net is nt wrking in it hd been wrkin in windows,which i hate d most

---

### Post by yogi4 on 2009-04-30
no one to help me here

---

### Post by Iowan on 2009-04-30
Without knowing what "bunch of softwares" you installed, it is hard to know "which programm is blocking". Is your website on a local server? What program is issuing the error message?

---

