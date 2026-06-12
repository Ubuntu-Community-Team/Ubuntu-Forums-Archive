---
title: "pppoeconf not working"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by dbv on 2011-03-09
I'm trying to use pppoeconf to connect my ADSL account on 10.04.2 LTS. I keep getting the message that it timed out waiting for PAD0. Centos (using rp-pppoe) and Mac OS X don't have any problems connecting out. For some reason my install didn't have pppoe package installed (but had pppoeconf) so I installed it using apt-get but it didn't help.

My modem is SpeedStream 5260.

Can anyone help?

---

### Post by dbv on 2011-03-10
If I understand what's happening here, pppoeconf uses the kernel mode driver while the pppoe package is the user mode Roaring Penguin pppoe.

I don't see anything in the log when I try pppoeconf, other than this:
Mar  9 23:53:09 ninja kernel: [  503.150004] eth1: no IPv6 routers present

When I try the user mode thing I see a whole bunch of this:
Mar  9 23:55:55 ninja pppd[2312]: Plugin rp-pppoe.so loaded.
Mar  9 23:55:55 ninja pppd[2312]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Mar  9 23:55:55 ninja pppd[2314]: pppd 2.4.5 started by root, uid 0
Mar  9 23:56:30 ninja pppd[2314]: Timeout waiting for PADO packets
Mar  9 23:56:30 ninja pppd[2314]: Unable to complete PPPoE Discovery

pppoe package installation went poorly as it was complaining about missing /etc/ppp/pppoe.conf file. I copied that file from my Centos install and then it started.

In either case, I can't connect.

---

### Post by dineshs on 2011-03-10
Did you try Network manager?
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by dbv on 2011-03-11
I had a bum NIC. That was the problem. pppoeconf (kernel mode driver) works fine.

Thanks.

---

