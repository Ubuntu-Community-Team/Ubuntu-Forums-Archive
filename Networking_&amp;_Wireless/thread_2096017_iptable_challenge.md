---
title: "iptable challenge"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by supernater on 2012-12-18
I know this forum is reserved for questions related to Ubuntu, but I though some of you might know how to solve a problem I have related to iptables.  

I'm running Openwrt Backfire 10.03.1, which is a linux based router firmware.  It uses iptables to manage network traffic.  Since it's linux base, you can install applications on it.  One application that I was interested in is amule, so I installed it on my router and attached a USB drive to my router.  Since my router is on all the time it is the perfect solution for downloading files on the emule network. 

The problem is that amule always has lowid indicating that port 4662 is not forwarded properly.  Openwrt has a web interface that enables me to forward ports so I tried forwarding external traffic on port 4662 to 192.168.1.1:4662.  However, I still get lowid.  I can ssh into my router and create iptable rules, so I'm guessing that I have to create a rule to forward external traffic on port 4662 to the router itself, but I dont' know enough about iptables to do this.  Can anyone give me hand with this?

---

### Post by Doug S on 2012-12-18
From your description it sounds as though you do not want port forwarding but rather you just want to allow port 4662 to be accepted by the IP tables input chain for use within the router itself.

---

### Post by supernater on 2012-12-18
> **Doug S said:**
> From your description it sounds as though you do not want port forwarding but rather you just want to allow port 4662 to be accepted by the IP tables input chain for use within the router itself.

Yes, this is correct.  However, I have practically zero skill with iptables.  I was thinking I wanted something like....

iptables -A INPUT --dport 4662 -p tcp -j ACCEPT

However, I still get lowid with this

---

### Post by supernater on 2012-12-18
Okay, I made some progress.  My INPUT table looks like this...
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
syn_flood  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
input_rule  all  --  anywhere             anywhere            
input      all  --  anywhere             anywhere 
```

If I run this I get highid...

```
iptables -I INPUT 2 -p tcp --dport 4662 -j ACCEPT
```

After running this my INPUT table looks like...

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
syn_flood  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
input_rule  all  --  anywhere             anywhere            
input      all  --  anywhere             anywhere  
```

Notice the position. If I try to make it the 1st or 2nd rule in the chain, it gives me highid.  If I go anywhere below that (rules 3-6) I still get lowid.  I'm not sure why that command works or what I did.  I'd hate to be poking holes in my firewall without fully understanding what I'm doing exactly.

---

