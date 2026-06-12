---
title: "VNC working but no SSH"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by pimpys on 2010-10-15
Hi again,

I have another issue, I can manage my Linux computer from my windows 7 computer using TightVNC, but I can't access my linux machine with SSH.

Ports 5900 and 22 are open on the linux IP on my linksys wifi router,
openssh server is installed on linux machine as well
ssh as well

Thanks,
Regards

---

### Post by luvshines on 2010-10-15
You are trying to ssh from Windows machin or Linux machine ??

Can you ssh from server to itself. Try this on the server:
```
ssh <user>@localhost
```

If it works, check if any firewalls rules are there.
```
sudo iptables -L
sudo ufw status
```

If they are, try switching them off and then give it a shot

---

### Post by pimpys on 2010-10-15
I am trying to SSH from my Windows to the Linux machine,

first code says :

> pimpy@pimpytux:~$ ssh pimpy@localhost
pimpy@localhost's password: 
Linux pimpytux 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Thu Oct 14 11:45:09 2010 from dd-wrt2nd says :

> pimpy@pimpytux:~$ sudo iptables -L
[sudo] password for pimpy: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

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
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
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

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5900 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination 
and sudo ufw status

>  pimpy@pimpytux:~$ sudo ufw status
État : actif

Vers                       Action      Depuis
----                       ------      ------
5900                       ALLOW       Anywhere

---

### Post by luvshines on 2010-10-15
Edit: Sorry got drifted away with another thread and posted something wrong here.

Try switching all iptables off, since I am no expert with them:
```
## Take a backup of the rules
sudo iptables-save > ~/iptables.bak

## Now switch them off
sudo service iptables stop
sudo ufw disable
```

Then check if SSH works or not from Windows

---

### Post by pimpys on 2010-10-16
No problem,

I did what you said :

> pimpy@pimpytux:~$ sudo iptables-save > ~/iptables.bak
[sudo] password for pimpy: 
pimpy@pimpytux:~$ sudo service iptables stop
iptables: unrecognized service
pimpy@pimpytux:~$ sudo ufw disable
Le pare-feu est arrêté et désactivé lors du démarrage du système
pimpy@pimpytux:~$ 

And I could connect via SSH to linux machin from my windows :)

What I need to do then to have always SSH open ?

---

### Post by luvshines on 2010-10-16
> **pimpys said:**
> No problem,

I did what you said :



And I could connect via SSH to linux machin from my windows :)

What I need to do then to have always SSH open ?

Gud !! So the firewalls rules are blocking the SSH traffic.
For making this permanent, you can have 2 methods:
1. Disable firewall rules forever (not secure method, **but you already did that when you say 'ufw disable'**. enable them back if you like)
2. Add a firewall rule to allow SSH traffic

But since my iptable skills suck(I always keep them off), I can't guide you with the appropriate rule to be added :(

---

### Post by pimpys on 2010-10-16
> **luvshines said:**
> Gud !! So the firewalls rules are blocking the SSH traffic.
For making this permanent, you can have 2 methods:
1. Disable firewall rules forever (not secure method, **but you already did that when you say 'ufw disable'**. enable them back if you like)
2. Add a firewall rule to allow SSH traffic

But since my iptable skills suck(I always keep them off), I can't guide you with the appropriate rule to be added :(

Thanks for your great support :)

So this is the Firewall from Linux right ?

As I don't know how to add a firewall rule to allow SSH traffirce, as I am a bit too noob, I will then disable the firewal every time, this is not a problem,

How do I edit the post as this is resolved ?

---

### Post by luvshines on 2010-10-16
> **pimpys said:**
> Thanks for your great support :)

So this is the Firewall from Linux right ?

As I don't know how to add a firewall rule to allow SSH traffirce, as I am a bit too noob, I will then disable the firewal every time, this is not a problem,

How do I edit the post as this is resolved ?

You don't have to disable it everytime. Once 'sudo ufs disable' should do it. From man page of ufw:
```

disable
  unloads firewall and disables firewall on boot
```

You can mark it solved by choosing it in 'Thread Tools', upper right corner, first drop down menu, just above your 1st post for this thread

---

### Post by gradinaruvasile on 2010-10-16
Be careful with vnc - it can be hacked easily (one option is to make vnc accept connections only from localhost and use it via ssh tunnel - but i dont know what clients you get on Windows with ssh tunneling).
Also dont leave ssh running on the default 22 port.

---

### Post by CharlesA on 2010-10-16
> **gradinaruvasile said:**
> Be careful with vnc - it can be hacked easily (one option is to make vnc accept connections only from localhost and use it via ssh tunnel - but i dont know what clients you get on Windows with ssh tunneling).
Also dont leave ssh running on the default 22 port.

Using port 22 for SSH is fine, as long as it's secured properly. If it's allowed access to the internet use a strong password at least. I recommend using keys, since you can't bruteforce them.

---

### Post by gradinaruvasile on 2010-10-16
> **CharlesA said:**
> Using port 22 for SSH is fine, as long as it's secured properly. If it's allowed access to the internet use a strong password at least. I recommend using keys, since you can't bruteforce them.

Using a random upper port (10000+) dont hurt...

---

### Post by CharlesA on 2010-10-16
> **gradinaruvasile said:**
> Using a random upper port (10000+) dont hurt...

True. It's still security thru obscurity. If someone really wanted to attack you, they'd find what port SSH is running on and attack it on that port.

---

### Post by gradinaruvasile on 2010-10-16
If someone really wants that is another issue. But if its only a drive-by-ish attack i dont think that they will scan all ports.
And strong password (or certificate) is recommended in any case.

---

### Post by pimpys on 2010-10-16
Thanks for the messages,

So my password is quite strong so this is fine for the usage I need on my Linux in Local or to give access to my friend when support is needed,

---

