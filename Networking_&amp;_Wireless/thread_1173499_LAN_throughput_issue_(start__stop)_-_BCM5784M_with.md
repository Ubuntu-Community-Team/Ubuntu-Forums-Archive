---
title: "LAN throughput issue (start / stop) - BCM5784M with tg3 driver"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by brendanpiater on 2009-05-29
Hi All,

Having a odd issue with my wired connection. I'm connecting and able to browse the Internet, home LAN etc. 

The odd thing is that I cannot maintain a steady through put of data... I go from 15MiB/s down to 0 and back again every few seconds. (see attached screenshot)

Oddly, or perhaps not... Wireless works 100%.

Searched and searched but cannot find someone having the same issue and I'm stumped!

Running: Ubuntu 9.04 (64 bit)
lshw attached

Thanks in advance.

Cheers
Brendan

---

### Post by munky99999 on 2009-05-29
Hmm I cant really think of what would do that sort of leapfrog effect. Instead of a constant throughput.

What gets me is that it's 15 cap on wired? Even running around 100m line. It'd be more like 12.5m

Got me. I'd suggest a network monitor like.

[http://etherape.sourceforge.net/](http://etherape.sourceforge.net/)

---

### Post by brendanpiater on 2009-05-30
Yeah, it's got me confused for sure! That transfer was from a local machine on my network running 8.04 with a 100m card. But transfering from the net is the same...

---

### Post by brendanpiater on 2009-05-31
Bump

---

### Post by brendanpiater on 2009-06-08
Hi All,

Still struggling with this, any help appreciated.

Thanks in advance.

Cheers
B

---

### Post by superprash2003 on 2009-06-08
have you tried editing your MTU?post output of ifconfig from the terminal

---

### Post by brendanpiater on 2009-06-08
Hi,

Just tired changing from 1500 to 1492 but that just caused Nautilus to freeze when trying to browse the NFS share on the file server. Here is the current output;

sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:22:19:e0:aa:db  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee0:aadb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1252 errors:22 dropped:0 overruns:0 frame:22
          TX packets:1106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:947763 (947.7 KB)  TX bytes:127529 (127.5 KB)
          Interrupt:17 

Worth noting that other machines are having no problem connecting and transfering from the file server over NFS or SFTP. Seems specific to this machine. Also has the same syntons pushing or pulling data from either machine.

Thanks in advance.

Cheers
B

---

### Post by superprash2003 on 2009-06-09
try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by brendanpiater on 2009-06-09
:( no not that either... bummer. Thanks for the input though.

$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1 (disabled)

---

### Post by brendanpiater on 2009-06-09
Some additional info, I tried 8.04 LTS live CD and the same issue is present there.

---

### Post by brendanpiater on 2009-10-26
I've created a bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461212") is anyone can assist further. Thanks in advance.

Cheers
B

---

