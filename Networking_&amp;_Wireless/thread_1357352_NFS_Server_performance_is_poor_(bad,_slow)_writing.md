---
title: "NFS Server performance is poor (bad, slow) writing to Ubuntu Server 9.10 Karmic Koala"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by milojah on 2009-12-17
When transferring between a Mac or Linux client to a Ubuntu 9.10 server, nfs write performance is 95% less than nfs read performance.

Server HW: (x64 Ubuntu Server 9.10)
Phenom II X3 720 -- performance set for all cpu scaling_governor
4GB DDR2 RAM
LSI LOGIC SAS PCI-E controller w/4 disk stripe
Intel Pro/1000 (e1000e) Server PCIe adapter

Read and write performance to/from the local disk is extremely fast.
---
Write:
Ubuntu 9.10 Server $ dd if=/dev/zero of=test.large.file bs=1024k count=4000
4000+0 records in
4000+0 records out
4194304000 bytes (4.2 GB) copied, 8.70623 s, 482 MB/s

Read:
Ubuntu 9.10 Server $ dd if=test.large.file of=/dev/null bs=1024k
4000+0 records in
4000+0 records out
4194304000 bytes (4.2 GB) copied, 10.3393 s, 406 MB/s
---

GbE is configured using 9000b jumbo frames, and speed validated via istat.

Sending from host to Ubuntu:
bash-3.2# iperf -c 192.168.1.184
------------------------------------------------------------
Client connecting to 192.168.1.184, TCP port 5001
TCP window size:   131 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.195 port 62900 connected with 192.168.1.184 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.10 GBytes    947 Mbits/sec

Receiving from Ubuntu to host:
bash-3.2# iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   256 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.195 port 5001 connected with 192.168.1.184 port 60448
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.14 GBytes    983 Mbits/sec
---

When reading from the Ubuntu via NFS (using default mount flags) from OSX, performance is good:

Macintosh Host $ dd if=test.large.file of=/dev/null bs=1024k
4000+0 records in
4000+0 records out
4194304000 bytes transferred in 41.249161 secs (101682165 bytes/sec)

When writing to the Ubuntu via NFS, everything falls apart:

Macintosh Host $ dd if=/dev/zero of=write.from.osx bs=1024k count=1000
1000+0 records in
1000+0 records out
1048576000 bytes transferred in 141.017190 secs (7435803 bytes/sec)
(half the data in over 3x the time)
---

I've also tried these same tests with the Ubuntu server running as a client to OSX, and reads and writes are both 100+MB/s.

I have tried mount flags to nfs from the client server, only negative effects.

Flags tried (in all possible combinations):
-o bg -o intr -o wsize=65536 -o rsize=65536 -o noatime

I have tried various sysctl changes on Ubuntu, and they've only had negative effects.

Sysctl keys tried (in all possible combinations)
# perf settings
#increase TCP maximum buffer size
net.core.rmem_default = 20971520
net.core.wmem_default = 20971520
net.core.rmem_max = 20971520
net.core.wmem_max = 20971520

# increase linux autotuning TCP buffer limits
net.ipv4.tcp_rmem = 4096 87380 20971520
net.ipv4.tcp_wmem = 4096 65536 20971520
net.ipv4.tcp_mem = 8388608 12582912 20971520
net.ipv4.udp_mem = 8388608 12582912 20971520

---

Any and all help would be greatly appreciated.

---

PS - I tried installing FreeBSD 7.2 on the Ubuntu hardware, and NFS performance read and write is 100+MB/s, so I don't think there is a hardware problem.

PPS - Had same performance issues with 9.04.

---

### Post by mbaysek on 2010-08-03
Have you had any luck with this?  I have been having the same exact problem.  Locally, I get blazing speeds both reading and writing to my software raids, but when writing over NFS, it goes to less than 1 MB/sec.  

And this is on a gigabit wire!

---

### Post by whit on 2010-09-21
No problem with speed Linux-Linux, but copying a large file from OSX to a 10.04.1 NFS server takes over 6 minutes for what's about 30 seconds from a Linux client.

---

### Post by SeijiSensei on 2010-09-21
> **milojah said:**
> Flags tried (in all possible combinations):
-o bg -o intr -o wsize=65536 -o rsize=65536 -o noatime

How about async?  Did you try that?  I've found it makes a substantial difference in writing speeds.  It's less robust than sync, of course, since you'll lose data if the NFS server dies before it writes any buffered data to its drive, but that's a very low probability event in my experience.  See "man exports" (from the nfs-kernel-server package) for details.

---

