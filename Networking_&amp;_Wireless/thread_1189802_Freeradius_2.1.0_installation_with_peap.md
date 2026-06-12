---
title: "Freeradius 2.1.0 installation with peap"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by elichan on 2009-06-17
I installed freeradius 2.1.0 with 
 
#apt-get install freeradius
#./configure --disable-share
#make
#make install
 
when I change the "default_eap_type = peap",
 
#radiusd -x
 
error message:
.......
Ignoring EAP-Type/tls because we do not have OpenSSL support.
Ignoring EAP-Type/ttls because we do not have OpenSSL support.
Ignoring EAP-Type/peap because we do not have OpenSSL support.
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
     with_ntdomain_hack = no
   }
rlm_eap: No such sub-type for default EAP type peap
/etc//raddb/eap.conf[482]: Instantiation failed for module "eap"
/etc//raddb/sites-enabled/inner-tunnel[223]: Failed to find module "eap".
/etc//raddb/sites-enabled/inner-tunnel[176]: Errors parsing authenticate section. 
Errors initializing modules

Please suggest solution!

---

### Post by Highl1 on 2009-06-17
I have the same problem. I've read on some other how-to tutorials how to fix this problem before installation, but I wouldn't like to need to reinstall everything from scratch. Problem is something with licensing, and I've heard you can rebuild FreeRadius once you've downloaded OpenSSL dev libraries. I installed them with Packet Manager (Synaptic), but how can I rebuild the server. I am a total linux noob, just started to get familiar with this few days ago, so any help is needed. 
Thanks in advance

---

### Post by liaommx on 2010-01-15
in actually , 
i  use apt-get install freeradius.
to install freeradius ,
without problem,
only edit some file,

like radiusd.conf
you need to #, all sql setting,
because default setting is for sql manage user and pass

edit clients.conf,
add the username and password.

edit eap.conf,
default_eap_type=md5, (if edit it as ttls, it will need some cert..,i still don't know how to use)

freeradius -X    
it start, and can pass the test,

---

