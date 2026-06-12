---
title: "DNS problem"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by david_j on 2010-05-26
Hi All,

I am having a DNS issue with my Ubuntu server running BIND9 on Ubuntu8.10.

I am trying to 'dig' a particular domain (ruthpetersen.net) that uses different servers (and IPs) for web and mail and obtain the mx record for the domain. When I dig an external DNS server directly [actually the DNS that is used as my localhost DNS forwarder] I get a good response. Details below...

But when I try to use my localhost DNS to dig this particular domain (ruthpetersen.net)  I do not receive any MX Answer Section.  I would have thought that when my localhost DNS server cannot provide the MX record for a domain that the request would be forwarded on to the ISP's DNS server which is recorded in my DNS server as a forwarder. This DNS problem also means that my mail server cannot pass mail onto this domain because the mail server (Qmail) only ever gets the IP address of the domain A record and not the MX record.

Anyone able to tell why my local DNS does not return the correct response to an mx query? What changes to my bind conf files should be made to fix this issue?

Many thanks
DJ...


*****************************************************************************
# dig mx localhost ruthpetersen.net

; <<>> DiG 9.5.0-P2 <<>> mx localhost ruthpetersen.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12083
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;localhost.         IN   MX

;; AUTHORITY SECTION:
localhost.      604800   IN   SOA   localhost. root.localhost. 2 604800 86400 2419200 604800

;; Query time: 0 msec
;; SERVER: 172.16.1.252#53(172.16.1.252)
;; WHEN: Thu May 20 17:26:13 2010
;; MSG SIZE  rcvd: 68

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3091
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ruthpetersen.net.      IN   MX

;; ANSWER SECTION:
ruthpetersen.net.   296   IN   CNAME   ghs.google.com.
ghs.google.com.      74397   IN   CNAME   ghs.l.google.com.

;; AUTHORITY SECTION:
l.google.com.      60   IN   SOA   ns3.google.com. dns-admin.google.com. 1415933 900 900 1800 60

;; Query time: 182 msec
;; SERVER: 172.16.1.252#53(172.16.1.252)
;; WHEN: Thu May 20 17:26:13 2010
;; MSG SIZE  rcvd: 132
*****************************************************************************
# dig mx @220.233.0.3 ruthpetersen.net

; <<>> DiG 9.5.0-P2 <<>> mx @220.233.0.3 ruthpetersen.net
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23147
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 2, ADDITIONAL: 8

;; QUESTION SECTION:
;ruthpetersen.net.      IN   MX

;; ANSWER SECTION:
ruthpetersen.net.   21600   IN   MX   20 alt2.aspmx.l.google.com.
ruthpetersen.net.   21600   IN   MX   30 aspmx2.googlemail.com.
ruthpetersen.net.   21600   IN   MX   30 aspmx3.googlemail.com.
ruthpetersen.net.   21600   IN   MX   30 aspmx4.googlemail.com.
ruthpetersen.net.   21600   IN   MX   30 aspmx5.googlemail.com.
ruthpetersen.net.   21600   IN   MX   10 aspmx.l.google.com.
ruthpetersen.net.   21600   IN   MX   20 alt1.aspmx.l.google.com.

;; AUTHORITY SECTION:
ruthpetersen.net.   21393   IN   NS   ns2.enetica.com.au.
ruthpetersen.net.   21393   IN   NS   ns1.enetica.com.au.

;; ADDITIONAL SECTION:
aspmx.l.google.com.   275   IN   A   72.14.213.27
alt1.aspmx.l.google.com. 43   IN   A   74.125.67.27
aspmx2.googlemail.com.   447   IN   A   209.85.135.27
aspmx3.googlemail.com.   3514   IN   A   72.14.213.27
aspmx4.googlemail.com.   2289   IN   A   209.85.229.27
aspmx5.googlemail.com.   1441   IN   A   74.125.157.27
ns1.enetica.com.au.   5364   IN   A   203.17.36.33
ns2.enetica.com.au.   1489   IN   A   203.17.36.4

;; Query time: 38 msec
;; SERVER: 220.233.0.3#53(220.233.0.3)
;; WHEN: Thu May 20 17:31:55 2010
;; MSG SIZE  rcvd: 391

*****************************************************************************

---

