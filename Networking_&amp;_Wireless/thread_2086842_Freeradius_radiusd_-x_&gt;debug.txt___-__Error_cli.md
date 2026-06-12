---
title: "Freeradius radiusd -x &gt;debug.txt   -  Error: clients file /usr/conf/clients not found"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by Ubonti on 2012-11-22
Hi Sir,

Hello and good day to you.

I am setting up freeradius server in a latest ubuntu one linux environment, until I encounter and stop at this problem.
Please look into it.

root@user-ThinkPad-T400:/home/user# radiusd -x > debug.txt
Thu Nov 22 19:18:46 2012: [2680] initializing dictionary
Thu Nov 22 19:18:46 2012: [2680] Starting dumping of Vendors Dictionary

Thu Nov 22 19:18:46 2012: [2680] Starting dumping of Attributes Dictionary

Thu Nov 22 19:18:46 2012: [2680] initializing configuration values
Thu Nov 22 19:18:46 2012: [2680] Disconnecting from session
Thu Nov 22 19:18:46 2012: [2680] Disconnecting from tty
Thu Nov 22 19:18:46 2012: [2680] radiusd : YARD Radius Server 1.1 $Date: 2004-08-02 20:40:07 +0200 (lun, 02 ago 2004) $  SHADOW i686-pc-linux-gnu flat_users
Thu Nov 22 19:18:46 2012: [2680] debug mode 1
Thu Nov 22 19:18:46 2012: [2680] using udp port 1812 for radius
Thu Nov 22 19:18:46 2012: [2680] using udp port 1813 for radacct
Thu Nov 22 19:18:46 2012: [2680] using udp port 1817 for radius-proxy
Thu Nov 22 19:18:46 2012: [2680] using udp port 1818 for radacct-proxy
Thu Nov 22 19:18:46 2012: [2680] Error: clients file /usr/conf/clients not found
Thu Nov 22 19:18:46 2012: [2680] proxy file /usr/conf/proxy not found; not using proxy

inside  /usr/conf/ folder I have all the following files :

user@user-ThinkPad-T400:~$ sudo su
[sudo] password for user: 
root@user-ThinkPad-T400:/home/user# cd /usr/conf/
root@user-ThinkPad-T400:/usr/conf# ls
attrs.access_challenge     clients.conf       ldap.attrmap  radiusd.conf
attrs.access_reject        dictionary         policy.conf   sql.conf
attrs.accounting_response  eap.conf           policy.txt    sqlippool.conf
attrs.pre-proxy            experimental.conf  proxy.conf    templates.conf
root@user-ThinkPad-T400:/usr/conf# 

Would anyone please help me ?  I already have clients.conf inside   /usr/conf/ folder,  
but still freeradiusus unable to find clients.conf

Thank you.

Best Regard,
Sam

---

