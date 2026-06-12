---
title: "iptables help - ftp passive mode not working"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by tgrux on 2013-03-19
I have searched for a few days to try and fix this and I'm at the point of going crazy!  I'm trying to setup an FTP TLS/SSL (Passive) connection using vsftpd.

When I do an "iptables -F" everything works fine, so I'm assuming it is with my iptables.  Here is what I have:
[HTML]      
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             127.0.0.0/8         reject-with icmp-port-unreachable 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:8587 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain FORWARD (policy ACCEPT)target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp-data 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state RELATED,ESTABLISHED 
[/HTML]

Note: I SSH via port 8587, for added security.

I have this in my vsftpd.conf file:
[HTML]
pasv_min_port=64000
pasv_max_port=65535
[/HTML]

I also added the following lines to my /etc/modules file and rebooted, but I'm not sure if that was the right way to do it.
[HTML]ip_nat_ftp
ip_conntrack_ftp[/HTML]

Also note, I'm a new to iptables so if you have any suggestions on locking the server down, I'm open to suggestions.  I'm the only one using FTP regularly  and I may have other people from time to time, so I don't need many ports open for it.  The only other connections I have are for websites over http and https and I SSH in through the command line.

I'm running Ubuntu 11.04 (host hasn't upgraded to 12 yet).

---

### Post by tgrux on 2013-03-19
Update:  I'm not receiving an error message, it either times out or the connection is rejected.

---

