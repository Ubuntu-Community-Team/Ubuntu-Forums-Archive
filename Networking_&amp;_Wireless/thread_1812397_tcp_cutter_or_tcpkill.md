---
title: "tcp cutter or tcpkill"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by pradeepthundiyil on 2011-07-26
Hi,

I 'm trying to kill an existing tcp connection using cutter 


1. ) i have installed cutter : sudo apt get install cutter

sudo cutter 192.168.10.2 9100   ---> getting an error message

No matching connections.

2.) I could kill tcp connection using tcpkill

sudo tcpkill -i eth0 host 172.16.2.1



Please help me to kill tcp with cutter..

---

### Post by jmoorse on 2011-07-26
Stuck print job?

What does this output show:

```

sudo netstat -tan | grep 9100

```

---

### Post by kay_rus on 2012-06-29
cutter was developed for older linux kernels and it uses old methods in /proc FS.

---

