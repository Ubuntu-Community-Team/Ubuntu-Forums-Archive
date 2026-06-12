---
title: "xl2tpd unix authentication"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by daniele75 on 2009-07-30
Hello all.
I've setup an ubuntu server with ipsec and xl2tpd.
All works properly if I use plain text authentication (/etc/ppp/chap-secrets).
I want to use /etc/passwd for user authentication, but if I setup

unix unix authentication = yes

into /etc/xl2tpd/xl2tpd.conf, it doesn't work.

I can't see any useful information into logs...

Anyone can help me?

Thanks
Daniele

---

### Post by daniele75 on 2009-07-30
sorry, I've forgot my actual configuration

/etc/xl2tpd/xl2tpd.conf 

[global]                                                               
ipsec saref = yes
listen-addr = 1.1.1.1
[lns default]                                                  
ip range = 172.16.255.1-172.16.255.20  
local ip = 172.16.255.254   
require chap = yes 
require pap = yes  
require authentication = yes  
unix authentication = yes
name = Ubuntu    
ppp debug = yes   
pppoptfile = /etc/ppp/options.xl2tpd

---

### Post by daniele75 on 2009-08-06
anyone that can help me?

---

### Post by scandella on 2013-01-02
Daniele: I know it's quite an old post. Did you solve the problem?

Has anyone else a hint? I have the same problem with Ubuntu 12.04 LTS. IPSEC/L2TP works perfect when storing the password as plaintext in the chap-secrets file but that's not the solution I prefer.

---

### Post by scandella on 2013-01-03
I had to change several things to make unix authentication work with Ubuntu 12.04 (LTS):

1. Settings in /etc/pam.d/ppp weren't correct. The following works:

auth    required        pam_nologin.so
auth    required        pam_unix.so
account required        pam_unix.so
session required        pam_unix.so

2. It seems that you have to use PAP insted of CHAP(v2). This should be no problem since we have an IPSEC tunnel which encrypts everything.

3. You have to make an entry to pap-secrets (l2tpd name is set in the ppp options.xl2tpd file):
*         l2tpd           ""              *

Content fo the options.xl2tpd file:
name l2tpd

4. In the options the login parameter seems to be needed.

---

