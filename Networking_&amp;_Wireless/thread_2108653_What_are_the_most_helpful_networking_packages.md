---
title: "What are the most helpful networking packages?"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by jbcohen on 2013-01-25
My wireless networking at home is fine, however I would like to explore networking packages, such as packages to tell me the speed of my network and ways to improve bandwidth via repeater placement.  what are your recommendations?

---

### Post by jonobr on 2013-01-25
You could try [bandwidthd]("http://bandwidthd.sourceforge.net/") or [bmon]("http://linux.die.net/man/1/bmon")

---

### Post by tgalati4 on 2013-01-25
iperf -s (on one machine)

iperf -c 192.168.1.162 -w 1024k -i 2 -t 20 -m (on another machine)

Change the IP address to the machine running the iperf packet catcher.   Run it both ways to identify bottlenecks.

---

### Post by ryankidman on 2013-01-26
bandwidthd is better I will vote for it

---

