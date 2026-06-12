---
title: "how to set up dual lan card within same network"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by chrone on 2010-06-18
dear all,

could you guys tell me how to set up dual lan card using different ip addresses within the same network?

for instance, i want eth0 to be 192.168.0.100 and eth1 to be 192.168.0.200 so that the bandwidth of each card could not be saturated easily. both lan card will be using the same gateway and dns which is 192.168.0.1.

the eth0 could be used for mysql connection, while the eth1 could be used for samba connection for the entire network of 192.168.0.0/24.

is this possible??

i've tried but to my bad luck, it didn't work quite well, especially the connection to the internet.

please enlighten me. thanks in advance. :)

kind regards,


/chrone

---

### Post by Iowan on 2010-06-18
[This]("http://ubuntuforums.org/showthread.php?t=1508791") thread might be useful. The link on the Spanning tree protocol is helpful. 
Another to check: [https://help.ubuntu.com/community/UbuntuLTSP/Trunking](https://help.ubuntu.com/community/UbuntuLTSP/Trunking)

---

### Post by chrone on 2010-06-19
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1508791") thread might be useful. The link on the Spanning tree protocol is helpful. 
Another to check: [https://help.ubuntu.com/community/UbuntuLTSP/Trunking](https://help.ubuntu.com/community/UbuntuLTSP/Trunking)

thanks for the tips. i really appreciate it. :)

since i've set all the clients to use both ethernet cards, i guess i'm trying to set the eth0 with 255.255.255.0 netmask and 192.168.0.1 gateway, and eth1 with 255.255.255.255 netmask without any gateway. hope this will do just fine.

---

