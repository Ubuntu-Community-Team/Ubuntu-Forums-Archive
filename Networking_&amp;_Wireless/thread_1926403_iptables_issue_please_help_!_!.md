---
title: "iptables issue please help ! !"
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by satishkumar432 on 2012-02-16
Hi there,

I am trying to block few networks to access the twiki onto my ubuntu server using iptables. I googled and went through the below steps.


[LIST=1]
[*]Make the INPUT policy as DROP.
[*]Then add the 2 ip address networks which i need to disable...
[/LIST]
            172.0.0.0/24 and 134.0.0.0/24...
      3. My machine is currently in 10.X.X.X network...after adding these rules.. I am not able to access twiki application on my machine as well ......... :( . Basically it is dropping all the packets from 10 network also which i have not mentioned in the iptable.


Can somebody help me out here..


This is how my iptable configuration looks like....





[sudo] password for sysadmin:
Chain INPUT (policy DROP)
target     prot opt source               destination


DROP     all  -- 172.0.0.0/24          anywhere
DROP     all  -- 134.0.0.0/24          anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
sysadmin@TWiki:~$




Any response is highly cherished  :D ! ! !

---

### Post by SeijiSensei on 2012-02-16
> Chain INPUT (policy DROP)
target prot opt source destination


You set the default policy to DROP as well.  That drops all packets from anywhere.  Make the default ACCEPT like the other chains, then just have rules for the specific packets you want to drop.

Are you sure you want to drop 172.0.0.0/24?  That covers the address range from 172.0.0.1 to 172.0.0.255; your other network address covers an equivalent range of hosts.

---

