---
title: "'netsed' not updating the incoming data packets"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by Suresh_Rajachar on 2013-08-12
Hi Experts, 

I am trying to manipulate incoming data packets to my localhost (destination). 

I have configured iptables as shown below:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10101

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  wb-in-f94.1e100.net  localhost  tcp dpt:https

And my netsed is as below:
sudo netsed tcp 10101 0 0  s/Set/Suresh/

When i ran this netsed, nothing happens to the data packets. I verified this using wireshark. 

Please tell me what has went wrong ? 

Regards,
-Suresh

---

