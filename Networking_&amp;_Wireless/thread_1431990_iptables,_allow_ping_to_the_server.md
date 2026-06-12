---
title: "iptables, allow ping to the server"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by gryzzly on 2010-03-17
Hello,
I have a VPS running Karmic (9.10).

I can ssh it and it serves :80 (http traffic) very well.

I have followed the tutorial from here:
[http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_Setup](http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_Setup)

I would like to ask what should I do in order to get ping to that machine working? (now I can't ping it, I get timeouts)

```

misha@tataata:~$ sudo iptables -L 
[sudo] password for misha: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

---

### Post by DGortze380 on 2010-03-17
> **gryzzly said:**
> Hello,
I have a VPS running Karmic (9.10).

I can ssh it and it serves :80 (http traffic) very well.

I have followed the tutorial from here:
[http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_Setup](http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_Setup)

I would like to ask what should I do in order to get ping to that machine working? (now I can't ping it, I get timeouts)

```

misha@tataata:~$ sudo iptables -L 
[sudo] password for misha: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

You need to allow protocol icmp

---

### Post by gryzzly on 2010-03-25
I have done this:
```
root@tataata:/home/misha# iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -d 123.203.213.229 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
root@tataata:/home/misha# iptables -A OUTPUT -p icmp --icmp-type 0 -s 123.203.213.229 -d 0/0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

And this:
```
root@tataata:/home/misha# SERVER_IP="123.203.213.229"
root@tataata:/home/misha# iptables -A OUTPUT -p icmp --icmp-type 8 -s $SERVER_IP -d 0/0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
root@tataata:/home/misha# iptables -A INPUT -p icmp --icmp-type 0 -s 0/0 -d $SERVER_IP -m state --state ESTABLISHED,RELATED -j ACCEPT
```


And here the -L output:
```
root@tataata:/home/misha# iptables -LChain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
DROP       all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             tataata.com         icmp echo-request state NEW,RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             tataata.com         icmp echo-reply state RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     icmp --  tataata.com          anywhere            icmp echo-reply state RELATED,ESTABLISHED 
ACCEPT     icmp --  tataata.com          anywhere            icmp echo-request state NEW,RELATED,ESTABLISHED 

```

So, as you can see, "drop all" was above the "allow icmp", and that's the reason why I still didn't get incoming pings.

So what I did is that I've backed up my existing rules from /etc/iptables.rules:
```
sudo cp /etc/iptables.rules /etc/iptables.rules.backup
```
Then I've saved the incorrect iptables -L ruleset from above:
```
iptables-save > /etc/iptables.rules
```
Then I've opened the /etc/iptables-rules in vim and just placed the "allow icmp" rules, above the "drop all" ruleset. So it reads like this:
```
:OUTPUT ACCEPT [88367:17378177] 
-A INPUT -i lo -j ACCEPT  
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT  
-A INPUT -d 123.203.213.229/32 -p icmp -m icmp --icmp-type 8 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -d 123.203.213.229/32 -p icmp -m icmp --icmp-type 0 -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -j DROP  
-A OUTPUT -s 123.203.213.229/32 -p icmp -m icmp --icmp-type 0 -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A OUTPUT -s 123.203.213.229/32 -p icmp -m icmp --icmp-type 8 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT  
COMMIT 
# Completed on Thu Mar 25 19:37:59 2010
```

---

### Post by DGortze380 on 2010-03-25
> **gryzzly said:**
> I have done this:
```
root@tataata:/home/misha# iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -d 123.203.213.229 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
root@tataata:/home/misha# iptables -A OUTPUT -p icmp --icmp-type 0 -s 123.203.213.229 -d 0/0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

And this:
```
root@tataata:/home/misha# SERVER_IP="123.203.213.229"
root@tataata:/home/misha# iptables -A OUTPUT -p icmp --icmp-type 8 -s $SERVER_IP -d 0/0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
root@tataata:/home/misha# iptables -A INPUT -p icmp --icmp-type 0 -s 0/0 -d $SERVER_IP -m state --state ESTABLISHED,RELATED -j ACCEPT
```


And here the -L output:
```
root@tataata:/home/misha# iptables -LChain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
DROP       all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             tataata.com         icmp echo-request state NEW,RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             tataata.com         icmp echo-reply state RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     icmp --  tataata.com          anywhere            icmp echo-reply state RELATED,ESTABLISHED 
ACCEPT     icmp --  tataata.com          anywhere            icmp echo-request state NEW,RELATED,ESTABLISHED 

```

So, as you can see, "drop all" was above the "allow icmp", and that's the reason why I still didn't get incoming pings.

So what I did is that I've backed up my existing rules from /etc/iptables.rules:
```
sudo cp /etc/iptables.rules /etc/iptables.rules.backup
```
Then I've saved the incorrect iptables -L ruleset from above:
```
iptables-save > /etc/iptables.rules
```
Then I've opened the /etc/iptables-rules in vim and just placed the "allow icmp" rules, above the "drop all" ruleset. So it reads like this:
```
:OUTPUT ACCEPT [88367:17378177] 
-A INPUT -i lo -j ACCEPT  
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT  
-A INPUT -d 123.203.213.229/32 -p icmp -m icmp --icmp-type 8 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -d 123.203.213.229/32 -p icmp -m icmp --icmp-type 0 -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A INPUT -j DROP  
-A OUTPUT -s 123.203.213.229/32 -p icmp -m icmp --icmp-type 0 -m state --state RELATED,ESTABLISHED -j ACCEPT  
-A OUTPUT -s 123.203.213.229/32 -p icmp -m icmp --icmp-type 8 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT  
COMMIT 
# Completed on Thu Mar 25 19:37:59 2010
```

That's why I prefer not to use a 'drop all' rule.
Maybe utilize the default policy instead? Just don't lock yourself out.

---

### Post by psykro on 2010-08-17
I had a similar problem, contact Rackspace support.
They suggested using the following from the command line to allow ping traffic

```
iptables -A INPUT -p icmp -j ACCEPT
```

Worked well for me, so posting here for anyone else to use.

---

