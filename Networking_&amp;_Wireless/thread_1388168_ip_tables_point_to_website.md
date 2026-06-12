---
title: "ip tables point to website"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2010-01-22
hello, i have an AP set up and would like to have all requests for a website sent to a specific ip address.. and am trying to get this to work in IP tables

user-->AP-->google.com

no matter what site they try to goto it takes them to google.com
i want to use this to require people to login to my server when they connect to my AP before they can go any further. 

thanks.

---

### Post by kidders on 2010-01-23
Hi there,

You could use destination NAT to rewrite the target addresses of packets passing through your AP. For example...```
iptables -t nat -I PREROUTING -p tcp --dport 80 -i eth2 -j DNAT --to 12.34.56.78
```

---

### Post by randumnumber on 2010-01-24
I have tried to use the code you provided and it didn't work could you maybe help me further? here is what ive got

```
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1 # DNS
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE # gateway to ext. router
iptables --append FORWARD --in-interface at0 -j ACCEPT # AP
```

if i just use this code it will forward all page requests out to the internet just fine, but if i add your code 

```
iptables -t nat -I PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 12.34.56.78
``` it breaks. Obvoisly i changed the ip address.

one question i have is should -i be set to the internet facing interface? or should it be set to at0 which is where all the traffic is comming from. i tried it both ways and it didnt work either way.

thanks for any farther help you can give.

---

### Post by kidders on 2010-01-24
Hey again,

> **randumnumber said:**
> ```
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1 # DNS
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE # gateway to ext. router
iptables --append FORWARD --in-interface at0 -j ACCEPT # AP
```I'm not sure what you're up to there ... are you trying to spoof DNS resolutions as well, for some reason?

> **randumnumber said:**
> should -i be set to the internet facing interface?No. You're interested in mangling packets *destined* for the internet, not ones originating there. Can you post your complete firewall configuration? One of your other rules could be causing problems.

---

### Post by randumnumber on 2010-01-24
I dont have a firewall setup on my system its on my router and its very permissive, I thought i should be passing dns to my internal network so they can find webpages. the address is on my home router which in turn points to a dns server on the internet. 

internal pc --> dns request to my iptables --> passed to the router on 192.168.1.1 --> passed to the internet 

should i not have to do this? 

here is my complete iptables readout

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```and my nat

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             anywhere            udp dpt:domain to:192.168.1.1 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```let me recap to say what i want to be doing, i want all traffic comming from inside the network that is attaching to my soft AP to be directed at an ip address on the internet.

i just studied a little of dns spoofing, maybe i could setup a bind server on my box and spoof dns to point to whatever page? or is there any easier way though ip tables?
i hope there is an easy way. lol.
thanks again

---

