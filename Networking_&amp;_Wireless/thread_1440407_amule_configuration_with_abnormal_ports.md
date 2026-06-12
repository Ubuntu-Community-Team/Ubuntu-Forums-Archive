---
title: "amule configuration with abnormal ports"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by CDrewing on 2010-03-27
Hey there,

I read [this article about the correct amule configuration]("http://ubuntuforums.org/showpost.php?p=2148795&postcount=2") in Ubuntu.

But I have to connect with different ports via OpenVPN due to... well it's more secure and costs less a year than to pay these MAFFIA-Letters. ;)

So my VPN provider gives me ports 40018, 41018, 42018, 43018 and 44018 to be my ear on the world (means: open ports). I entered one of these ports for TCP in amule and one of them in UDP. uPNP is deactivated as the port for extended server queries, too.

But when I start amule, it tries to connect and - after checking all the 200 IP addresses in the queue - it shuts down the connection process and fails at all.

When I do a network port scan with the above mentioned ports, I receive a "closed port" answer. What does this mean? My router is set to NAT but Ubuntu is still rejecting on these ports?

Here's my iptables:
```
cdrewing@cdrewing-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         

```

Perhaps sb can help me. Something seems to be wrong here.

Thanks a lot
Christian

---

### Post by Enigmapond on 2010-03-27
Have you tried manually forwarding the ports on your router?

---

### Post by CDrewing on 2010-03-27
Well, yes:

[IMG]http://i44.tinypic.com/20tffcl.png[/IMG]

---

### Post by CDrewing on 2010-04-04
It works!!
As soon as I enter the NAT information in the application menu, amule is working perfectly with Kademlia.

---

