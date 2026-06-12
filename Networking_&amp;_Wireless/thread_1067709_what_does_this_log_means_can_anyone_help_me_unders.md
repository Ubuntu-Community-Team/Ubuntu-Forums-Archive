---
title: "what does this log means? can anyone help me understand?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by sliver99 on 2009-02-12
Hi all,
1 week ago I've found strange logs and now I've noticed that i'm full of this:

> frz@shiva ~ $ tail /var/log/messages
Feb 12 11:29:25 shiva kernel: [ 3670.260374] Unknown OutputIN= OUT=vmnet1 SRC=192.168.129.1 DST=192.168.129.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:29:25 shiva kernel: [ 3670.260666] Unknown OutputIN= OUT=vmnet8 SRC=172.16.153.1 DST=172.16.153.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:34:25 shiva kernel: [ 3970.104957] Unknown OutputIN= OUT=vmnet1 SRC=192.168.129.1 DST=192.168.129.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:34:25 shiva kernel: [ 3970.105115] Unknown OutputIN= OUT=vmnet8 SRC=172.16.153.1 DST=172.16.153.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:35:35 shiva kernel: [ 4040.063805] Unknown OutputIN= OUT=vmnet1 SRC=192.168.129.1 DST=192.168.129.255 LEN=257 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=237
Feb 12 11:35:35 shiva kernel: [ 4040.064621] Unknown OutputIN= OUT=vmnet8 SRC=172.16.153.1 DST=172.16.153.255 LEN=257 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=237
Feb 12 11:39:25 shiva kernel: [ 4269.941634] Unknown OutputIN= OUT=vmnet1 SRC=192.168.129.1 DST=192.168.129.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:39:25 shiva kernel: [ 4269.941923] Unknown OutputIN= OUT=vmnet8 SRC=172.16.153.1 DST=172.16.153.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:44:25 shiva kernel: [ 4569.782278] Unknown OutputIN= OUT=vmnet1 SRC=192.168.129.1 DST=192.168.129.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Feb 12 11:44:25 shiva kernel: [ 4569.782571] Unknown OutputIN= OUT=vmnet8 SRC=172.16.153.1 DST=172.16.153.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

I wonder they are logs of packets exchanged between 192.168.129.1 (but my network is a WLAN 192.168.1.0/24) and 172.16.153.X but i don't know what is this.

Please, can anyone help me understand?

---

### Post by jonobr on 2009-02-12
This looks like output created by Vmware?
Are you running Vnware?

---

### Post by sliver99 on 2009-02-18
You're right!!!

i've installed vmware but i'm running a virtualbox VM. I've checked network settings of the VM and now everything is much clearer.

Thank you.

---

### Post by jonobr on 2009-02-18
kick a$$ :guitar:

---

