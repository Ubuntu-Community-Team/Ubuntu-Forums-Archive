---
title: "Bind 9.8.1-P1 problem on Ubuntu 12.04"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by vitronix on 2013-04-14
I have done the complete configuration using the Ubuntu serverguide


contents of named.conf.local:

```

zone "vitronix.lan" {
        type master;
        file "/etc/bind/db.vitronix.lan";
        };

zone "10.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.10.168.192";
};

```

contents of db.vitronix.lan:

```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.vitronix.lan. (
                     2013041100         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                          2419200         ; Expire
                            604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.vitronix.lan.
@       IN      A       192.168.10.36
ns      IN      A       192.168.10.36

```

Contents of db.10.168.192:
```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.vitronix.lan. (
                     2013041100         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                          2419200         ; Expire
                            604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
36      IN      PTR     ns.vitronix.lan.

```

Output of dig vitronix.lan:

```

; <<>> DiG 9.8.1-P1 <<>> vitronix.lan
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 20895
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;vitronix.lan.                  IN      A

;; Query time: 4 msec
;; SERVER: 192.168.10.36#53(192.168.10.36)
;; WHEN: Thu Apr 11 03:09:01 2013
;; MSG SIZE  rcvd: 30

```

now when i run 

```

host -l 192.168.10.36
Host 36.10.168.192.in-addr.arpa not found: 2(SERVFAIL)

```


After adding 192.168.10.254 (my firewall) to the dns-nameservers I get this

```

host -l 192.168.10.36
Host 36.10.168.192.in-addr.arpa. not found: 3(NXDOMAIN)

```

Hope anyone can help, I am getting frustraded :(

---

### Post by Doug S on 2013-04-14
If you run your db.vitronix.lan file through named-checkzone it will fail, and it should have failed to load with named.
Anyway, you are missing the valid e-mail address partion of the SOA line. Once I added that, then named-checkzone works (at least for me).

O.K. so even if that fix is made, the "dig" example you used will not have an answer. There is no answer for "vitronix.lan" the way the zone file has been done, which differs from how the Ubuntu serverguide, 12.04, does it. Just delete the "ns." from the SOA line of your forward zone file, define the lookup, and then "dig vitronix.lan" should work. Summary:```
;
; BIND data file for vitronix.lan
;
$TTL    604800
@       IN      SOA     vitronix.lan. email.vitronix.lan. (
                        2013041400      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
                IN      A       192.168.10.36
;
@               IN      NS      ns.vitronix.lan.
ns              IN      A       192.168.10.36

```It is not clear to me why your reverse lookup is not working.

Edit: Oh, your reverese file has the same issue with the missing valid e-mail. It should have failed to load also, and it does fail named-checkzone. Summary:```
;
; BIND reverse data file for vitronix.lan
;
$TTL    604800
@       IN      SOA     ns.vitronix.lan.[COLOR=#ff0000] email.vitronix.lan. ([/COLOR]
                        2013041400      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
;
@       IN      NS      ns.vitronix.lan.
36      IN      PTR     ns.vitronix.lan.
```

---

