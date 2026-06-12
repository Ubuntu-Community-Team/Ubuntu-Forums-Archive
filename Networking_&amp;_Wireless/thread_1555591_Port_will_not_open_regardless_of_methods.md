---
title: "Port will not open regardless of methods"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Klyx on 2010-08-18
No matter what I do, i cannot get port 3100 to open. This is for a new MMO i am CBT on. I know it works on windows because that is how I installed it and played. But I prefer being on Linux. Majority of all other MMOs work fine. Just this one has to have udp 3100 open.

the following is a rough output of all the methods I have tried with no success. As you can see I have done some extensive research first before posting here. Now its become a lil bit of an obsession.

 iptables -A INPUT -p udp --sport xxxx -j ACCEPT
 iptables -A INPUT -p tcp --dport xxxx -j ACCEPT
i have also tried ipatables -A I and iptables -A OUTPUT

i cannot get the following command to work:
netstat -nap | grep: 3100
i get the following error:
No command 'grep:' found, did you mean:
 Command 'grep' from package 'grep' (main)

and yes I tried the "spaces" in different places thinking that was the prob. So i cannot see if 3100 is in the list or not



then to save
iptables-save

i eventually turned on the firewall "ufw enable" add the port there, and output:
To                         Action      From
--                         ------      ----
3100                       ALLOW       Anywhere
3100/udp                   ALLOW       Anywhere

some references

[http://www.justlinux.com/forum/showthread.php?t=151424](http://www.justlinux.com/forum/showthread.php?t=151424)
firewall stuff: [https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

I even manually went into the router and turned it on there.


i add these lines for startup purposes.
post-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules
to this file:
/etc/network/interfaces

do I need to do something in "wine" ?

any help would be great as I feel i am starting to repease myself

ps
results of "iptables -L"
```

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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3100 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:3100 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:3100 

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

```

as you can see it DOES show the udp 3100 but for some reason the game still says either firewall is blocking the server or udp is not enabled. I suppose worse case I can just boot back to windoze uhg.

thank you in advance for anyone that can clear up this mess.
-----------------
Definition of insanity: repeating the exact same process over and over expecting different results

---

### Post by madverb on 2010-08-18
Have you allowed that port through your modem/router firewall to your computer?

Also, the command is grep not grep:
> netstat -nap | grep: 3100

No command '**grep:**' found, did you mean:
Command '**grep**' from package '**grep**' (main)

---

### Post by Klyx on 2010-08-18
> **madverb said:**
> Have you allowed that port through your modem/router firewall to your computer?

Also, the command is grep not grep:

Hi!
thanks for the fast reply
yes I did that as well as mentioned in the first post:
> 
I even manually went into the router and turned it on there.
However, I am not sure if that was nessassary as the game works in windows - just not linux due to the udp error i keep getting.


i forgot to mention that when i use the following:
netstat -nap | grep 3100
that it does nothing but give me a new prompt (forgot to mention that I was doing it with and without the ":")

:-)

---

### Post by madverb on 2010-08-19
If you receive no message it means the command ran successfully. It just means that there was nothing found to print to screen.

Have you tried completely disabling iptables just to check?

---

### Post by herteljt on 2010-12-05
Hi Klyx,
I was wondering if you were able to find a solution for this.

I have a similar problem.

I have been able to open the port (temporarily) using netcat. For example, for port 25565

```
 netcat -l 25565 
```

will allow me to verify that my router is forwarding the port.

---

