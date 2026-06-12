---
title: "IPTABLES - Remote access to PostgreSQL blocked"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by jmedurey on 2012-02-03
Sorry if my question is to simple.



I've been looking  for a solution through different forums but I haven't found a solution.
I have Ubuntu 11.10 with Postgresql 9.0.6. I need to access the  database (port 5432) from out of my network. I hope the next diagram can  show what I want: 
 

Remote Pc <----> Internet <---Dyndns---> router (dynamic IP) <---NAT---> local PC with posgresql
 

I can access, from  the remote PC, the local PC. But it's imposible  to access any TCP/IP port. Watching the logs from the iptables with  dmesg,  I think the system is blocking the access.
 

I've tried to access port 80 but  I wasn't able to connect the local  PC. My only succes have been to access the symple web server of my  router. And watch the blocked packages at the iptables log. 
 I began my tests from an empty iptables.  And following different  blogs and manuals I have built the iptable with the next commands:


 #the ip 193.150.1.216 was the dynamic IP during my tests...


 # accept established connection 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
 #acceso puerto 80 oruga 
iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT 
iptables -I INPUT 2 -p tcp --sport 80 -j ACCEPT 
#acceso puerto 5432 oruga 
iptables -I INPUT 1 -p tcp --dport 5432 -j ACCEPT 
iptables -I INPUT 2 -p tcp --sport 5432 -j ACCEPT 
#iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 193.150.1.216 --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT 
#iptables -A OUTPUT -p tcp -s 193.150.1.216 --sport 80 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT 
# accept local traffic 
iptables -A INPUT -i lo -j ACCEPT 
#iptables -A INPUT -s <server> -j ACCEPT 
# log and drop remaning packets 
iptables -I INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7 
iptables -P INPUT DROP 
iptables -P FORWARD DROP
 

Anybody could explain me how to afford this little project?



I know I'm doing something wrong, but I don't know if the problem is at  the iptables or if  I'm completely lost with the concepts...
 

Thank you in advance,
Miguel

---

