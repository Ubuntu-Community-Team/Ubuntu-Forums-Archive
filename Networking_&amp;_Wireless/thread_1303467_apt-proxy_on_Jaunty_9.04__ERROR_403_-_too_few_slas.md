---
title: "apt-proxy on Jaunty 9.04  ERROR 403 - too few slashes in URI /"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by LarryJ2 on 2009-10-28
My apt-proxy does not function:

1.  ifconfig shows that my ip is 192.168.1.101.  This is what I have set into ***/etc/network/interfaces*** and what ifconfig shows after I did  ***/etc/init.d/networking  restart***

2. my ***/etc/apt-proxy/apt-proxy-v2.conf*** file has the following stanzas
> ;; Server IP to listen on
address = 192.168.1.101

;; Server port to listen on
port = 9999
and later in that file
> [ubuntu]
;; Ubuntu archive
backends = [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
min_refresh_delay = 15m

and I also did 
***sudo /etc/init.d/apt-proxy restart***


3.  So why when I put ***[http://192.168.1.101:9999/](http://192.168.1.101:9999/)***  in my FireFox address text window do I get > ERROR 403 - too few slashes in URI /  I was expecting to see directory /ubuntu and then under /ubuntu directory  all the packages.

4. I've tried  [http://192.168.1.101:9999/ubuntu](http://192.168.1.101:9999/ubuntu)  and [http://127.0.0.1:9999](http://127.0.0.1:9999)  and [http://192.168.1.101:9999//](http://192.168.1.101:9999//).   Nothing except the Error 403.

Any idea of what I am doing wrong?  Thanks.
Larry

---

### Post by jaros1 on 2009-10-31
deleted

---

