---
title: "Bind Help."
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by CosmicSea on 2009-10-23
I am running a linux VPS with ubuntu 8.04. My VPS provider doesn't have domain services so i have to host my own domain. I am using bind9 and cant "catch or grab or whatever you want to call it", my domain name. I used go daddy to create my domain and I created my own name servers with the ip's I use on my VPS. I have been trying to go at this all week, all i need to do is get my domain running and then my site will be good to go cause I already have everything else running smoothe it seems. any help at all is very appreciated. I dont know what kind of info you need from me so ask whatever you need to. I am going to use a fake domain and ip in on here just to protect myself.

when i type dig example.com this is what it tells me.

dig example.com

; <<>> DiG 9.4.2-P2 <<>> example.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 3480
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.                 IN      A

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Oct 23 17:07:26 2009
;; MSG SIZE  rcvd: 31

---

### Post by CosmicSea on 2009-10-23
Also I have tried many tutorials and have been searching around the net and forums with no luck.

---

