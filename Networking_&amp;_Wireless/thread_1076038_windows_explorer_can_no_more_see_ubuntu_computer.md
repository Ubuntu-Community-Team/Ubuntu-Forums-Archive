---
title: "windows explorer can no more see ubuntu computer"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by maitrebart on 2009-02-20
When I was typing \\homer in windows explorer until few days ago, I was getting access to the shares on my ubuntu computer (homer). Since a few days, I am no more able: it fails to connect to the ubuntu computer. Even if I use the IP address.

If I do "net view" in the nt shell, it only show other windows computer.

I guess something happened to my samba config but I have no idea what and I am not sure if it is really the case?

I can ping each other computer. I am able to access the windows shares from my ubuntu computer using smb://... in nautilus. However, nautilus was able to see my windows shares before by navigating through Network Servers. Now it sees nothing but at least I am able to access them via the location bar (smb://...).

Also, I was used to run putty (and xming) to access my ubuntu computer from windows. Now the putty shell starts but nothing happens, except an error message telling a problem with the network connection.

It's all like if samba (???) decided to close its visibility and ignore any access from outside.

If anyone has an idea/hint about how to fix this problem I would really appreciate.

---

### Post by maitrebart on 2009-02-21
I have the impression it could be related to iptables rules that might have changed.

If someone is familiar with iptables rules that may hide a computer on a lan, let me know!

In fact, I'm interested to know what should look like the default iptables rules at ubuntu installation and where they are located (in a file I guess???) so I can revert them back.

---

### Post by maitrebart on 2009-02-21
Here are my iptables rules:

> Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg  /min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


I would appreciate if anyone can tell me what rule(s) to remove or modify in order my ubuntu computer can be seen and can accept all connections from within the lan, I would really appreciate. Since I'm not familiar at all with how to formulate a rule using iptables, if you could give me 1 or 2 examples how to do it, that would be great!


P/S: On its side samba works since I'm able to see and transfer files from ubuntu towards windows.

---

### Post by superprash2003 on 2009-02-21
you could flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

### Post by maitrebart on 2009-02-21
> **superprash2003 said:**
> you could flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

Thanks. I'm not sure if it is safe to flush everything but I'll give it a try (I have a router anyway). 

Perhaps I will have a look at iptables-save/-restore in order to have a quick way to retreive them in case the iptables are not the cause of my problem.

---

### Post by maitrebart on 2009-02-21
It worked! Though my computer is subject to all rootkits in my lan.
I'll try to find out the minimum rules to setup.

---

### Post by maitrebart on 2009-02-21
I would like to mark this thread as solved but I can't find the entry in the thread tools menu???

---

### Post by superprash2003 on 2009-02-22
iptables by default blocks all ports except ones which certain services are using in your machine.. thats only if there are any such services.. apart from that by default all other ports are blocked by iptables..

  the THREAD SOLVED feature is currently disabled.. so i guess the only way out , is to rename the thread title and prefix SOLVED..

---

