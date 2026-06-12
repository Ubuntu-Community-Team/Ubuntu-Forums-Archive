---
title: "Changing Transmission ports"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by Josep CA on 2011-10-25
Hi,
I'm using Transmission but I have its port blocked by my ISP. Is there any (legal) way to get it to work (by changing the port or using a proxy for instance)? If the answer is yes how would you do it?

This is my nmap output:
```

josep@josep-K52JT:~$ sudo nmap -sS -O 127.0.0.1
[sudo] password for josep: 

Starting Nmap 5.21 ( http://nmap.org ) at 2011-10-25 15:40 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000031s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp

```

Many thanks! :popcorn:

---

