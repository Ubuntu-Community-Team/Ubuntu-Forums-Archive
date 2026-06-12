---
title: "How increase max connection in ubuntu"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by neoqing on 2013-05-11
Hi,There:
    Recently,I try to setup some service which can server 20K user in one ubuntu box, but when I investigate the solution, I found that I cannot increase the concurrent TCP connections.
  As I know, by default, the number of max connections is 1024, I google around and found a article to describe how to increase the max connection, but in case, it does not work for me.
  I totally followed this [https://lists.launchpad.net/mosquitto-users/msg00163.html](https://lists.launchpad.net/mosquitto-users/msg00163.html), and use same type EC2 instance (ubuntu 12.04, 64bit), but it does not work.
  As well I tried that solution in my local box (ubuntu 10.10),  it's same problem, once the connetions go to 1024 approximately , the server resets following connections. And I'm sure the service (my software) does not have any limit on connections, so I do doubt it's OS level 's limitation.
 Run ulimit -a on my box, it shows
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 262144
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 262144
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

Is there any has experience regarding these stuff, would you please share your ideas on this topic? thanks in advance.

Neo

---

