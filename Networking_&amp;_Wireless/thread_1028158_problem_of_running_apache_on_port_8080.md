---
title: "problem of running apache on port 8080"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by mitjab on 2009-01-02
tcp      306      0 mitjab.homelin:webcache crawl-66-249-67-1:43983 ESTABLISHED


or with numers

tcp      306      0 192.168.123.171:8080    66.249.67.140:43983     ESTABLISHED

becouse of this i can not run apache on port 8080. What is this, how can i stop it?

---

### Post by mitjab on 2009-01-02
any idea?

---

### Post by superprash2003 on 2009-01-02
have you configured apache to listen on 8080??have you port forwarded 8080??try this online port scanner to confirm [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by mitjab on 2009-01-02
yes server works fine, then apache start crashing and when i try to restart it i get this

sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                        [Fri Jan 02 19:33:12 2009] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs
                     

then i see that port 8080 is used by another crawl-66-249-67-1:43983

i scan port now and i get

82.149.25.222 is responding on port 8080 (webcache).

What is this?

Thx

---

### Post by superprash2003 on 2009-01-03
some other service is already running on 8080.. try with another port..

---

