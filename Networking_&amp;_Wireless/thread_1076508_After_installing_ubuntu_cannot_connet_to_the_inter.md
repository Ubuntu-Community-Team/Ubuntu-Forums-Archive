---
title: "After installing ubuntu cannot connet to the internet"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by the_baer on 2009-02-21
Hi,
i have installed ubuntu on many machines but this one is given me the hardest time to have it connected to the net. Ubuntu 8.04 t2. i can ping any other machine on my office network but wouldn't open a web page. The machine getting DNS and DHCP services from the server, the IP address is correct. ifconfig display the right ip and the right eth. name server is right as the other machines. brought eth down and then up without any success. restart he network and restart the machine many time without any success. i even changed the ethernet cable to the machine, and nothing again. 
anyone have any idea, all i read they are refering to the DNS resolution, but it is right as the other machines connected to the network?

Please and THank you

---

### Post by the_baer on 2009-02-21
i forgot, i can ping only my office network pc's but cannot ping the outside world.

---

### Post by superprash2003 on 2009-02-21
are you running firestarter or any other similar software?? go to the terminal and post output of the following commands

1)sudo iptables -L
2)ifconfig
3)cat /etc/resolv.conf

try pinging by ip.. like ping 74.125.67.100

---

