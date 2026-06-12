---
title: "Mis-confguration in Bind9"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by ethane on 2011-11-08
Hi

I have kerberos and ldap installed in the same VM. I need Bind9 so that both will resolve "kerberos.example.com" and "ldap.example.com" to this local VM. But when I do a "dig ***", there is no Answer section. So the config should be wrong, but I don't know where.

Here are the files (IP of VM is 192.168.0.101):
-------------------
FILE: /etc/resolv.config
-------------------
search example.com
nameserver 127.0.0.1

-------------------
FILE: example.com.db
-------------------
$TTL 3D
example.com.      IN      SOA     ubuntu.example.com.   root.example.com. (

        5    ;serial
        28800
        3600
        604800
        38400
 )

example.com.      IN      NS      ubuntu.example.com.

www             IN      CNAME   ubuntu.example.com.

localhost       IN      A       127.0.0.1
kerberos        IN      A       192.168.0.101
ldap            IN      A       192.168.0.101

-------------------
FILE: rev.0.168.192.in-addr.arpa
-------------------
$TTL 3D
@ IN SOA ubuntu.example.com. root.example.com. (
                        5;serial
                        28800;
                        604800;
                        604800;
                        86400
)

@               IN      NS      ubuntu.example.com.
1               IN      PTR     ubuntu.example.com.
101             IN      PTR     kerberos.example.com.
101             IN      PTR     ldap.example.com.


And here is the reply from dig:
$: dig kerberos.example.com

; <<>> DiG 9.7.1-P2 <<>> kerberos.example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 38231
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kerberos.example.com.        IN    A

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Nov  7 23:14:37 2011
;; MSG SIZE  rcvd: 38

---

### Post by lisanels47 on 2012-03-26
root@hsic-01:/etc/bind# cat db.hsi.com
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.hsi.com. root.hsi.com. (
                              10        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.hsi.com.
@       IN      A       192.168.2.21
@       IN      AAAA    ::1
ns      IN      A       192.168.2.21
hsic-01 IN      A       192.168.2.21
hsic-02 IN      A       192.168.2.22
hsic-03 IN      A       192.168.2.23
hsic-04 IN      A       192.168.2.24
hsic-05 IN      A       192.168.2.25
hsic-06 IN      A       192.168.2.26
hsic-07 IN      A       192.168.2.27
hsic-08 IN      A       192.168.2.28
hsic-09 IN      A       192.168.2.29
hsic-55 IN      A       192.168.2.10
hsic-20 IN      A       192.168.2.15
root@hsic-01:/etc/bind# 

Maybe this example will help you.  My test domain HSI.COM is setup like the above.  

I can add the following for my domain like you are trying to do:
kerberos IN      A       192.168.2.21
ldap IN      A       192.168.2.21

this would resolve both of them to the same address and the ns.

---

### Post by SeijiSensei on 2012-03-26
Do you have the zone defined in /etc/bind/named.conf or a file included therein like this:

```

zone "example.com" {
     type master;
     file "/path/to/zonefile";
};

```

The file must reside in a path readable by the bind user.  Typically it resides in /etc/bind unless you're running the server in a chrooted environment in which case it needs to be in /path/to/chroot/etc/bind.

---

