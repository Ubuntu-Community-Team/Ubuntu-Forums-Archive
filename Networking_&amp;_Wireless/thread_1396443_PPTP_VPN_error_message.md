---
title: "PPTP VPN error message"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by nani2ratna on 2010-02-02
Hi, 

I am trying to connect VPN which is in another office branch.
If i connect to my office lan and try to connect to VPN, its failed to connect.

And the error message is 

```
Feb  2 10:54:39 ratnak-laptop pppd[3755]: Connect: ppp0 <--> /dev/pts/1
Feb  2 10:54:40 ratnak-laptop kernel: [ 4631.060560] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=6507 PROTO=47
Feb  2 10:54:40 ratnak-laptop kernel: [ 4631.069756] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=27684 PROTO=47
Feb  2 10:54:42 ratnak-laptop kernel: [ 4633.317097] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=59140 PROTO=47
Feb  2 10:54:43 ratnak-laptop kernel: [ 4634.045231] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=52025 PROTO=47
Feb  2 10:54:45 ratnak-laptop kernel: [ 4635.419349] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=59231 PROTO=47
Feb  2 10:54:46 ratnak-laptop kernel: [ 4637.047842] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=890 PROTO=47
Feb  2 10:54:47 ratnak-laptop kernel: [ 4637.468199] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=18793 PROTO=47
Feb  2 10:54:49 ratnak-laptop kernel: [ 4639.608321] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=4410 PROTO=47
Feb  2 10:54:49 ratnak-laptop kernel: [ 4640.057073] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=45092 PROTO=47
Feb  2 10:54:51 ratnak-laptop kernel: [ 4641.827312] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=31086 PROTO=47
Feb  2 10:54:52 ratnak-laptop kernel: [ 4643.066037] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=32013 PROTO=47
Feb  2 10:54:53 ratnak-laptop kernel: [ 4643.898497] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=31063 PROTO=47
Feb  2 10:54:55 ratnak-laptop kernel: [ 4646.057882] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=78 TOS=0x08 PREC=0x20 TTL=58 ID=45901 PROTO=47
Feb  2 10:54:55 ratnak-laptop kernel: [ 4646.057933] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=56 TOS=0x08 PREC=0x20 TTL=58 ID=60990 PROTO=47
Feb  2 10:54:57 ratnak-laptop kernel: [ 4648.342597] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=12405 PROTO=47
Feb  2 10:54:58 ratnak-laptop kernel: [ 4649.053898] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=33655 PROTO=47
Feb  2 10:54:59 ratnak-laptop kernel: [ 4650.346683] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=74 TOS=0x08 PREC=0x20 TTL=58 ID=9032 PROTO=47
Feb  2 10:55:01 ratnak-laptop kernel: [ 4652.076231] Inbound IN=eth0 OUT= MAC=00:24:81:6b:dc:a3:00:0d:bc:b9:0f:d4:08:00 SRC=196.44.10.194 DST=10.10.14.40 LEN=60 TOS=0x08 PREC=0x20 TTL=58 ID=29952 PROTO=47
Feb  2 10:55:02 ratnak-laptop pppd[3755]: Modem hangup
Feb  2 10:55:02 ratnak-laptop pppd[3755]: Connection terminated.
Feb  2 10:55:02 ratnak-laptop pppd[3755]: Exit.

```

But If i am in 3g or out of my office, then i can conenct to VPN.

I dont know why this is happeneing.
I disabled EAP.
I triedmy level bext by reading so many forums.

Thanks and Regards
RS

---

