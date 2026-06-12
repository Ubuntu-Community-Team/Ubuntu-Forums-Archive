---
title: "Proftpd and GProftpd working on intranet not internet"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-06-05
Hey i have set up proftpd with gproftpd and i though it was all good because i checked with the computers on the lan and it worked but then i tred on another computer trying [ftp://192.168.1.12but](ftp://192.168.1.12but) it timed out go on try it yourself so then i created one on my windows partiton as 192168.1.130 using Golden FTP and it did the same and you can try that twoyouself so for somereason it i only woking on the network not internet

---

### Post by unicycler on 2006-06-05
Have you opened port 21 on your router/firewall? Then you need to get your public IP address when connecting from outside your LAN.

---

### Post by CameronCalver on 2006-06-05
how do you get your public ip ?

---

### Post by CameronCalver on 2006-06-05
Can some1 tell me how to get a public ip

---

### Post by harisund on 2006-06-06
Your public ip is what you see when you go to a website like [http://whatismyip.com](http://whatismyip.com)

---

### Post by CameronCalver on 2006-06-07
well when i have found that out how do i config proftpd to go send the ftp to that ip

---

