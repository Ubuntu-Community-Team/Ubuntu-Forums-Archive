---
title: "DNS questions"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by saitoh on 2009-05-08
I'm having some strange DNS issues. I have a Debian DNS server on my home network so that I can ping and log into my other computers by their hostname. The DNS server works fine for all of the computers. Yesterday I added a new computer to the network and decided to install Ubuntu 9.04 on it. The Ubuntu box can dig my local IP's, however when I do anything else it can't resolve the name.

JohnSmith@vicious:~$ dig spike.beebop.local

; <<>> DiG 9.5.1-P2 <<>> spike.beebop.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57031
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;spike.beebop.local.		IN	A

;; ANSWER SECTION:
spike.beebop.local.	38400	IN	A	192.168.0.100

;; AUTHORITY SECTION:
beebop.local.		38400	IN	NS	spike.

;; Query time: 0 msec
;; SERVER: 192.168.0.100#53(192.168.0.100)
;; WHEN: Fri May  8 10:02:07 2009
;; MSG SIZE  rcvd: 71



JohnSmith@vicious:~$ ping spike.beebop.local
ping: unknown host spike.beebop.local


I don't get how I can get a response from dig and then not be able to resolve the name for a ping. Any help would be awesome.

---

