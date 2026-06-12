---
title: "iptables: --rcheck works like --update"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by Sworddragon on 2012-07-26
I have written a bash script for iptables which shall secure my system:

```
#!/bin/bash -eu

typeset -A rule

rule[0]='-P FORWARD DROP'
rule[1]='-P INPUT DROP'
rule[2]='-A INPUT -i lo -j ACCEPT'
rule[3]='-A INPUT -j ACCEPT -m state --state ESTABLISHED'
rule[4]='-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --name SSH --set'
rule[5]='-A INPUT -j DROP -p tcp --dport 22 -m recent --hitcount 4 --name SSH --rcheck --seconds 60'
rule[6]='-A INPUT -j DROP -p tcp --dport 22 -m recent --hitcount 16 --name SSH --rcheck --seconds 3600'
rule[7]='-A INPUT -j ACCEPT -p tcp --dport 22'
for rule in "${rule[@]}"
do
	iptables -C ${rule:3} > /dev/null 2>&1 || iptables $rule
done
```

The rules are droping all incoming connections except SSH. I have even created rules which shall prevent brute force attacks. If an ip address connects for more than 3 times in a minute or 15 times in a hour it will be blocked for this time.

The problem is that on every try the timestamp is updated for example: A user creates within 5 seconds 3 connections and is now blocked for 1 minute. He tries now every 20 seconds to create a new connection but every attempt will update the timestamp. This means even after a few days he couldn't create a successfull connection.

I'm wondering why every blocked attempt updates the timestamp. I thought only --update is doing this. Maybe somebody have an explanation for that.

---

