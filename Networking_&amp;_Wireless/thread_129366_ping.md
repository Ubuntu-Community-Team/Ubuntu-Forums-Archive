---
title: "ping"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by Nordicruler on 2006-02-13
What does this means?

PING [www.aftonbladet.se](www.aftonbladet.se) (192.71.238.76) 56(84) bytes of data.
From 192.71.238.14 icmp_seq=3 Packet filtered
From 192.71.238.14 icmp_seq=7 Packet filtered
From 192.71.238.14 icmp_seq=12 Packet filtered
From 192.71.238.14 icmp_seq=15 Packet filtered
From 192.71.238.14 icmp_seq=18 Packet filtered
From 192.71.238.14 icmp_seq=22 Packet filtered
From 192.71.238.14 icmp_seq=25 Packet filtered
From 192.71.238.14 icmp_seq=31 Packet filtered
From 192.71.238.14 icmp_seq=40 Packet filtered
From 192.71.238.14 icmp_seq=46 Packet filtered

--- [www.aftonbladet.se](www.aftonbladet.se) ping statistics ---
52 packets transmitted, 0 received, +10 errors, 100% packet loss, time 51008ms

---

### Post by mips on 2006-02-13
Probably going through a firewall of some sorts.

---

### Post by Nordicruler on 2006-02-13
On that site you mean?

---

### Post by mips on 2006-02-13
Do you have a firewall installed on your pc or router ? 
Is it blocking ICMP echos ?

---

### Post by Nordicruler on 2006-02-14
I have no router or firewall, its an default kubuntu install.

---

### Post by woedend on 2006-02-14
sounds like that server is set up to drop ping requests.  I get same message from only that server.  odd find.

---

### Post by Nordicruler on 2006-02-14
okay, then its not my fault :) 
Thanks.

---

