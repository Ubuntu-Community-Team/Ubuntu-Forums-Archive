---
title: "How to check/measure your Internet speed via Command Line ?"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by patrick295767 on 2006-05-31
How to check/measure your Internet speed via Command Line ?
  
Thank you !!

Patrick

---

### Post by xyz on 2006-12-17
I don't really know but
```
th@luser:~$ dig www.google.com 
; <<>> DiG 9.3.2 <<>> www.google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7088
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         603171  IN      CNAME   www.l.google.com.
www.l.google.com.       273     IN      A       209.85.129.99
www.l.google.com.       273     IN      A       209.85.129.104
www.l.google.com.       273     IN      A       209.85.129.147

;; Query time: 20 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Dec 17 14:02:48 2006
;; MSG SIZE  rcvd: 100

```
I'm sort of bumping this to see if anyone has any ideas.
A bit off topic but I found this interesting:
[Local DNS Cache for Faster Browsing]("http://ubuntu.wordpress.com/tag/administration/")

---

### Post by patrick295767 on 2006-12-17
> **xyz said:**
> I don't really know but
```
th@luser:~$ dig www.google.com 
; <<>> DiG 9.3.2 <<>> www.google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7088
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         603171  IN      CNAME   www.l.google.com.
www.l.google.com.       273     IN      A       209.85.129.99
www.l.google.com.       273     IN      A       209.85.129.104
www.l.google.com.       273     IN      A       209.85.129.147

;; Query time: 20 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Dec 17 14:02:48 2006
;; MSG SIZE  rcvd: 100

```
I'm sort of bumping this to see if anyone has any ideas.
A bit off topic but I found this interesting:
[Local DNS Cache for Faster Browsing]("http://ubuntu.wordpress.com/tag/administration/")

THis is an example of dsl test :
[http://www.zdnet.com.au/broadband/speedtest.htm](http://www.zdnet.com.au/broadband/speedtest.htm)
  
I am sure there is some way somehow ...

---

### Post by tturrisi on 2006-12-17
~# wget -c [ftp://mirror.d-jacobs.com/ubuntu/edgy/ubuntu-6.10-desktop-i386.iso](ftp://mirror.d-jacobs.com/ubuntu/edgy/ubuntu-6.10-desktop-i386.iso)
and look at the screen
also, test other links:
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
also, view the wget-log in your home dir to see a print out of rates.
you can use System Monitor to end the wget process.
also, ~# wget -h will give more uses.

---

### Post by patrick295767 on 2006-12-27
maybe a """sort""" of wget of this :

[http://speedtest.macbidouille.com/speedtest5.php](http://speedtest.macbidouille.com/speedtest5.php)

no ? has someone an idea / script  made ?

---

