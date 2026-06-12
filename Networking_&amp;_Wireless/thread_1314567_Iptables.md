---
title: "Iptables"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by fusa on 2009-11-04
After upgrading to 9.10 I am having problems with all ports being blocked if I use iptables.  I have no idea of where to begin in fixing this issue.  I tried recreating the iptables using fwbuilder, but it seems that the templates are now broken.

This is the output of "sudo iptables -L"
```

$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       all  --  server.us            anywhere            state NEW 
DROP       all  --  server.us            anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:60000:61000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports ssh,42000,www,https,ircd,24800,21000,5900,smtp,ssmtp,33333,pop3,pop3s,mysql,telnet state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports microsoft-ds,1234,5121,imaps,imap2,netbios-ssn,ftp,nfs,sunrpc,33334,ipp,submission,imaps,spamd,7634 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports 8118,9050,webmin,dict,loc-srv,xmpp-client,8033,8034,http-alt,domain,9001,9030,8123 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp multiport dports 4000,netbios-ns,netbios-dgm,netbios-ssn,loc-srv state NEW 
RULE_3     udp  --  anywhere             anywhere            udp dpts:1024:65535 state NEW 
ACCEPT     all  --  server.us            anywhere            state NEW 
ACCEPT     all  --  server.us            anywhere            state NEW 
RULE_5     all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       all  --  server.us            anywhere            state NEW 
DROP       all  --  server.us            anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
RULE_5     all  --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
RULE_2     all  --  anywhere             server.us           state NEW 
RULE_2     all  --  anywhere             server.us           state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
RULE_5     all  --  anywhere             anywhere            state NEW 

Chain RULE_2 (2 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:60000:61000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports ssh,42000,www,https,ircd,24800,21000,5900,smtp,ssmtp,33333,pop3,pop3s,mysql,telnet 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports microsoft-ds,1234,5121,imaps,imap2,netbios-ssn,ftp,nfs,sunrpc,33334,ipp,submission,imaps,spamd,7634 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports 8118,9050,webmin,dict,loc-srv,xmpp-client,8033,8034,http-alt,domain,9001,9030,8123 
ACCEPT     udp  --  anywhere             anywhere            udp multiport dports 4000,netbios-ns,netbios-dgm,netbios-ssn,loc-srv 

Chain RULE_3 (1 references)
target     prot opt source               destination         
ACCEPT     all  --  192.168.1.100/30     anywhere            
ACCEPT     all  --  192.168.1.104/29     anywhere            
ACCEPT     all  --  192.168.1.112/28     anywhere            
ACCEPT     all  --  192.168.1.128/25     anywhere            

Chain RULE_5 (3 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `RULE 5 -- DENY ' 
DROP       all  --  anywhere             anywhere           

```

and /etc/iptables.conf
```

# Generated by iptables-save v1.4.4 on Wed Nov  4 15:18:08 2009
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:RULE_2 - [0:0]
:RULE_3 - [0:0]
:RULE_5 - [0:0]
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -s 192.168.1.120/32 -i eth0 -m state --state NEW -j DROP 
-A INPUT -s 192.168.1.120/32 -i eth0 -m state --state NEW -j DROP 
-A INPUT -i lo -m state --state NEW -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 11/0 -m state --state NEW -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 11/1 -m state --state NEW -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 0/0 -m state --state NEW -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 3 -m state --state NEW -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 8/0 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 60000:61000 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 6881:6889 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp -m multiport --dports 22,42000,80,443,6667,24800,21000,5900,25,465,33333,110,995,3306,23 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp -m multiport --dports 445,1234,5121,993,143,139,21,2049,111,33334,631,587,993,783,7634 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp -m multiport --dports 8118,9050,10000,2628,135,5222,8033,8034,8080,53,9001,9030,8123 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp -m multiport --dports 4000,137,138,139,135 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 1024:65535 -m state --state NEW -j RULE_3 
-A INPUT -s 192.168.1.120/32 -m state --state NEW -j ACCEPT 
-A INPUT -s 192.168.1.120/32 -m state --state NEW -j ACCEPT 
-A INPUT -m state --state NEW -j RULE_5 
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -s 192.168.1.120/32 -i eth0 -m state --state NEW -j DROP 
-A FORWARD -s 192.168.1.120/32 -i eth0 -m state --state NEW -j DROP 
-A FORWARD -i lo -m state --state NEW -j ACCEPT 
-A FORWARD -o lo -m state --state NEW -j ACCEPT 
-A FORWARD -m state --state NEW -j RULE_5 
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A OUTPUT -o lo -m state --state NEW -j ACCEPT 
-A OUTPUT -d 192.168.1.120/32 -m state --state NEW -j RULE_2 
-A OUTPUT -d 192.168.1.120/32 -m state --state NEW -j RULE_2 
-A OUTPUT -m state --state NEW -j ACCEPT 
-A OUTPUT -m state --state NEW -j RULE_5 
-A RULE_2 -p icmp -m icmp --icmp-type 11/0 -j ACCEPT 
-A RULE_2 -p icmp -m icmp --icmp-type 11/1 -j ACCEPT 
-A RULE_2 -p icmp -m icmp --icmp-type 0/0 -j ACCEPT 
-A RULE_2 -p icmp -m icmp --icmp-type 3 -j ACCEPT 
-A RULE_2 -p icmp -m icmp --icmp-type 8/0 -j ACCEPT 
-A RULE_2 -p tcp -m tcp --dport 60000:61000 -j ACCEPT 
-A RULE_2 -p tcp -m tcp --dport 6881:6889 -j ACCEPT 
-A RULE_2 -p tcp -m tcp -m multiport --dports 22,42000,80,443,6667,24800,21000,5900,25,465,33333,110,995,3306,23 -j ACCEPT 
-A RULE_2 -p tcp -m tcp -m multiport --dports 445,1234,5121,993,143,139,21,2049,111,33334,631,587,993,783,7634 -j ACCEPT 
-A RULE_2 -p tcp -m tcp -m multiport --dports 8118,9050,10000,2628,135,5222,8033,8034,8080,53,9001,9030,8123 -j ACCEPT 
-A RULE_2 -p udp -m udp -m multiport --dports 4000,137,138,139,135 -j ACCEPT 
-A RULE_3 -s 192.168.1.100/30 -j ACCEPT 
-A RULE_3 -s 192.168.1.104/29 -j ACCEPT 
-A RULE_3 -s 192.168.1.112/28 -j ACCEPT 
-A RULE_3 -s 192.168.1.128/25 -j ACCEPT 
-A RULE_5 -j LOG --log-prefix "RULE 5 -- DENY " --log-level 6 
-A RULE_5 -j DROP 
COMMIT
# Completed on Wed Nov  4 15:18:08 2009

```

I have disabled all apparmor profiles for now since it was creating tons of problems with leafnode, mysql and other applications, so that isnt the problem.

---

