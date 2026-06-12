---
title: "Testing LAN transfer speed"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by gtg556h on 2011-03-05
I'd like to test local network speed without actually transferring large files (I sometimes have networking equipment problems, and I sometimes have ISP problems, and would like to use this to differentiate between the 2, when pinging doesn't provide enough data).  To verify proper functionality of my SSD, I run:

>>> pv /dev/sda > /dev/null

Would it be appropriate to scp to /dev/null on another computer on my LAN to determine local transfer speeds without actually writing data?  Or is there a better way?  Thanks!

---

### Post by porec on 2012-10-25
No one?
I also looking for somthing like this.

---

### Post by Sergius14 on 2012-10-26
iperf.

But you have to know what to test and how to read results.


Bandwith could be tested with a single TCP test with big chunks.


"Quality", latency, jitter, packet lost, etc. could be tested with UDP packets or icmp.


By default it test uni-directional. You may want to test bi-directional, etc.


Also need to know: Extremelly high number of packets and traffic can eat all your CPU before reaching the network limit (specially true with small udp packets test on GB LAN). Keep an eye on it. Just in case.

---

