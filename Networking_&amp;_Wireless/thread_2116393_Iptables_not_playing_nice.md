---
title: "Iptables not playing nice"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by Image0fman on 2013-02-15
I am trying to setup my iptables on an ubuntu 10.04 box.. I want to restrict  access to only one host on ports 22 and 80. But they are not working for me.. I am kind of a n00b with iptables so if anyone can check these out and see where I've gone wrong would be greatly appreciated

Thank YOU!! 

here are the rules 

```

*filter
:INPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [10:646]

-A INPUT -i lo -j ACCEPT
-A INPUT -i wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i wlan0 -p tcp -s x.x.x.x/24 -m multiport --dports 22,80 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -j LOG --log-level 7
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "** Dropped Inbound: "
-A INPUT -j REJECT --reject-with icmp-port-unreachable

-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -o wlan0 -p tcp -m multiport --sports 22,80 -m state --state ESTABLISHED -j ACCEPT
COMMIT

```

---

### Post by Doug S on 2013-02-16
Please help us to help you by giving more information. What exactly is not working? Do you have some examples? Does your computer use DHCP? (You might need a rule for udp source port 68 and dest port 67) Your OUTPUT chain rule doesn't make sense, because the default poilicy is ACCEPT anyhow. However, it is not clear to me why it isn't doing what you want (which I'm not 100% clear on). Unless you meant this line:```
-A INPUT -i wlan0 -p tcp -s x.x.x.x/[COLOR=red]24[/COLOR] -m multiport --dports 22,80 -m state --state NEW,ESTABLISHED -j ACCEPT
```to be this```
-A INPUT -i wlan0 -p tcp -s x.x.x.x/[COLOR=red]32[/COLOR] -m multiport --dports 22,80 -m state --state NEW,ESTABLISHED -j ACCEPT
```or even this:```
-A INPUT -i wlan0 -p tcp -s x.x.x.x/[COLOR=red]32[/COLOR] -m multiport --dports 22,80 -m state --state NEW,ESTABLISHED[COLOR=red],RELATED[/COLOR] -j ACCEPT
```

---

### Post by Image0fman on 2013-02-16
Thanks for the reply! 

Please allow me to clarify. I am running ssh and apache on the 10,04 box. I am trying to setup my iptables to only allow a specific address or subnet to access those ports. With my above mentioned rules, I keep getting a connection refused error on the host I am allowing in iptables. 

BTW as per your instructions mentioned above, the /24 was when I was allowing the whole subnet, I did try x.x.x.x/32 for a specific host and still no luck. I will add the RELATED option but shouldn't NEW,ESTABLISHED be all I need for INPUT? 


Thanks!

---

### Post by Doug S on 2013-02-16
Focusing on ssh, for now, do you see any entries that might help in /var/log/auth.log? Also, I find it very helpful to observe the packet counters in iptables so as to know which path packets take. I.E. are packets taking the ACCEPT path for a new SSH connection?```
sudo iptables -v -x -n -L
```

---

### Post by Image0fman on 2013-02-16
Ok, I will give this a try. Unfortunately I am away until Tuesday so I won't have access to my box til then.. thanks for the help!

---

