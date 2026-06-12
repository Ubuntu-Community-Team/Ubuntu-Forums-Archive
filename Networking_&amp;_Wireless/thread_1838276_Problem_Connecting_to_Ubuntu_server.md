---
title: "Problem Connecting to Ubuntu server"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by stephenconnolly on 2011-09-03
Hello,

I'm trying to connect remote connect to my ubuntu (version 11.04) home server via my mac book pro. I've enabled desktop sharing on the server and I've installed 'Chicked of the VNC' on my Mac book Pro. 

But when trying to connect I get an error:

Could not connect to server 192.168.1.115:5900

Operation timed out: connect()

I'm relatively new to all this, so not sure where to go from here.

Any help appreciated. 

Regards

---

### Post by stephenconnolly on 2011-09-03
*bump*

---

### Post by 2F4U on 2011-09-03
Can you ping the server from your Mac and login via ssh?

---

### Post by stephenconnolly on 2011-09-03
Just tried to ping the server and got the following......

PING 192.168.1.115 (192.168.1.115): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3
ping: sendto: No route to host
Request timeout for icmp_seq 4
ping: sendto: Host is down
Request timeout for icmp_seq 5
ping: sendto: Host is down
Request timeout for icmp_seq 6
ping: sendto: Host is down
Request timeout for icmp_seq 7
ping: sendto: Host is down
Request timeout for icmp_seq 8
ping: sendto: Host is down
Request timeout for icmp_seq 9
ping: sendto: Host is down
Request timeout for icmp_seq 10
ping: sendto: Host is down
Request timeout for icmp_seq 11
ping: sendto: Host is down
Request timeout for icmp_seq 12
ping: sendto: Host is down


Tried logging in via ssh, but it just keeps asking for a password, even when I enter the correct one.

---

### Post by stephenconnolly on 2011-09-04
*bump*

---

### Post by stephenconnolly on 2011-09-04
Problem solved, refer the following link:

[http://ubuntuforums.org/showthread.php?t=1838740](http://ubuntuforums.org/showthread.php?t=1838740)

---

