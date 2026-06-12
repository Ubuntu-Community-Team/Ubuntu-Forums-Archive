---
title: ";; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: SERVFAIL, id: 17359"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by anthar on 2013-04-14
i'm using ubuntu 12.04 LTS

I want to host certain domain name, example.com to my server:

Note: i've replace the real domain name to example.com and the server ip to 198.23.xx.xx

$ vi resolv.conf

nameserver 8.8.8.8



$ vi named.conf.local

zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
};

zone "example2.com" {
        type master;
        file "/etc/bind/zones/example2.com.db";
};



$ vi db.example.com
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     dns1.example.com. root.example.com. (
                        2013041413      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       NS      dns1
dns1    A       198.23.xx.xx
@       A       198.23.xx.xx
@       AAAA    ::1


$ named-checkzone example.com /etc/bind/db.example.com
zone example.com/IN: loaded serial 2013041413
OK


$ dig example.com

; <<>> DiG 9.8.1-P1 <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 62392
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.          IN      A

;; Query time: 1017 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Apr 14 20:23:54 2013
;; MSG SIZE  rcvd: 38


May I know if something is wrong with my configs?

Thanks

---

### Post by Doug S on 2013-04-14
> **anthar said:**
> I want to host certain domain name, example.com to my server:...i've replace the real domain name to example.comDo you own "example.com"? More typically, you wouldn't run a local DNS, but rather would register either your ISP name server or your static IP address lookup details with your domain name registrar.

If you want to do it the way you are trying, you should have two public facing DNSs and you still need to point your domain name to them at your domain name registrar. Then the DNS at google that you are using will know where to find the authoritative information.

---

### Post by anthar on 2013-04-15
"rather would register either your ISP name server or your static IP address lookup details with your domain name registrar."   <---- where do i do this 2?
in my control panel it only has NS settings.

I followed this tutorial [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Yes i own the domain name and it has 2 dns set at the hosting control panel (from hosting account A)

NS: dns1.example.com
IP : 198.23.xx.xx     <--- ip of my server from hosting account B

NS: dns2.example.com
IP : 198.23.xx.xx   <--- ip of my server from hosting account B


Based on your comment "you should have two public  facing DNSs and you still need to point your domain name to them at your  domain name registrar. Then the DNS at google that you are using will  know where to find the authoritative information." I added 2 lines to my zone file
@                       IN      NS      dns2.example.com.
dns2                    IN      A       198.23.xx.xx

restart bind 9

but I still get the same error. below is my new zone file.

$ORIGIN example.com.
$TTL    604800
@       IN      SOA     dns1.example.com. root.example.com. (
                        20130417        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@                       IN      NS      dns1.example.com.
@                       IN      NS      dns2.example.com.
dns1                    IN      A       198.23.xx.xx
dns2                    IN      A       198.23.xx.xx
@                       IN      A       198.23.xx.xx
www                     IN      A       198.23.xx.xx
@                       IN      AAAA    ::1


ERROR

$ dig example.com

; <<>> DiG 9.8.1-P1 <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 31088
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.          IN      A

;; Query time: 1016 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Apr 16 00:53:30 2013
;; MSG SIZE  rcvd: 38


but when i dig at localhost there's no error


$ dig example.com @localhost

; <<>> DiG 9.8.1-P1 <<>> example.com @localhost
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19332
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;example.com.          IN      A

;; ANSWER SECTION:
example.com.   604800  IN      A       198.23.xx.xx

;; AUTHORITY SECTION:
example.com.   604800  IN      NS      dns2.example.com.
example.com.   604800  IN      NS      dns1.example.com.

;; ADDITIONAL SECTION:
dns1.example.com. 604800 IN    A       198.23.xx.xx
dns2.example.com. 604800 IN    A       198.23.xx.xx

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Apr 16 00:53:00 2013
;; MSG SIZE  rcvd: 124

---

### Post by Doug S on 2013-04-15
Does "dig dns1.example.com" work?
See t[his thread f]("http://ubuntuforums.org/showthread.php?t=2135421")rom yesterday for an example forward zone file for a possible way to make for to make "dig example.com" work.
I have never had succes with the $ORIGIN directive.

> "rather would register either your ISP name server or your static IP address lookup details with your domain name registrar."   <---- where do i do this 2?
in my control panel it only has NS settings.It seems you have done what is required.

Edit: Perhaps have a look to see if your are getting any DNS lookups coming from the WAN. Example:```
sudo tcpdump -n -nn -tttt -i eth1 port 53
```Change the interface, eth1, to whatever your WAN facing interface is.

---

### Post by anthar on 2013-04-16
your right, my incoming port 53 was close. I opened port 53 and it solved the problem.

Thanks :popcorn:

---

