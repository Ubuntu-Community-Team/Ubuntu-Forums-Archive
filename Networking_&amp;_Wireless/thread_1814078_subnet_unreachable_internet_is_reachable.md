---
title: "subnet unreachable internet is reachable"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by fodon on 2011-07-28
I have a strange problem and I dont even know where to start looking on Google ... perhaps you have a clue.

The network topology is:
www - modem (lanIp:192.168.1.254) - router (Lan IP :192.168.1.64 AND 2nd level lan : 192.168.2.1 ) 
The router is connected wirelessly to 
Laptop : 192.168.2.101
PC : 192.168.2.114

The problem is that my PC can ping 192.168.1.254 
... but not 192.168.2.1  !!!
In contrast the laptop can ping 192.168.2.1 and 192.168.1.254
Just in case this matters, for completeness, .. I've an inactive eth0 (wired ethernet link) with static IP   

Other possibly relevant details:
I'm using an old 802.11b card. Cant imagine this is relevant, because the internet is working fine as far as pinging anything outside the local network goes.

Thanks,
-Ajo.

---

### Post by lkjoel on 2011-07-28
> **fodon said:**
> I have a strange problem and I dont even know where to start looking on Google ... perhaps you have a clue.

The network topology is:
www - modem (lanIp:192.168.1.254) - router (Lan IP :192.168.1.64 AND 2nd level lan : 192.168.2.1 ) 
The router is connected wirelessly to 
Laptop : 192.168.2.101
PC : 192.168.2.114

The problem is that my PC can ping 192.168.1.254 
... but not 192.168.2.1  !!!
In contrast the laptop can ping 192.168.2.1 and 192.168.1.254
Just in case this matters, for completeness, .. I've an inactive eth0 (wired ethernet link) with static IP   

Other possibly relevant details:
I'm using an old 802.11b card. Cant imagine this is relevant, because the internet is working fine as far as pinging anything outside the local network goes.

Thanks,
-Ajo.
Could you give me the output of these commands?
```
lsb_release -a
``````
uname -a
``````
lspci  -vv
``````
nm-tool
``````
sudo /etc/init.d/network* restart
!!
``````
sudo /etc/init.d/network-manager restart
``````
sudo  /etc/init.d/network-interface restart
``````
sudo  /etc/init.d/network-interface-security restart
``````
ifconfig
```

---

### Post by fodon on 2011-07-28
Thanks for the suggestions. The bug was obvious once I looked carefully at the ifconfig output. The address 192.168.2.5 was associated with the eth0 interface even though the ethernet cable was removed. I removed the eth0 section from /etc/interfaces and things are perfect !

---

