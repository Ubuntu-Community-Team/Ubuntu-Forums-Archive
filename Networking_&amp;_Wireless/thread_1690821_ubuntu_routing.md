---
title: "ubuntu routing"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by barrybtec on 2011-02-19
Hi I have had a look at the the information on the ubuntu forum about this but am having trouble getting the server to do what i want it to do.
 
I have a VPS running ubuntu 9.10 and i am trying to set it up to redirect port 25 to a remote machine via a VPN connection (remote machine connected via VPN)
 
i have tried setting this up in the firewall using webmin but it is not working.

---

### Post by mips on 2011-02-19
Try using fwbuilder.

[http://www.fwbuilder.org/4.0/docs/users_guide/ch15s03s04.html](http://www.fwbuilder.org/4.0/docs/users_guide/ch15s03s04.html)
[http://www.fwbuilder.org/4.0/docs/users_guide/index.html](http://www.fwbuilder.org/4.0/docs/users_guide/index.html)
[http://www.linuxjournal.com/article/6625](http://www.linuxjournal.com/article/6625)
[http://www.linuxjournal.com/article/6715](http://www.linuxjournal.com/article/6715)

If your network is natted also look in to the NAT section of th documentation.

---

### Post by barrybtec on 2011-02-19
I dont think that will work in my situation as it is a VPS and has no GUI
 
I have been trying to set up via the nat documentation. even when i go through the step by step settings word for word i get a criptic meeningless excuse of a failure message as below. probably because it is the correct settings
 
 
iptables-restore v1.4.4: Need TCP, UDP, SCTP or DCCP with port specificationError occurred at line: 6Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 
 
Why does something that is so easy to do in windows require a degree in software engineering to do it in linux?

---

### Post by mips on 2011-02-20
> **barrybtec said:**
> I dont think that will work in my situation as it is a VPS and has no GUI

Did you read the documentation at all? You don't run fwbuilder on the server. You run it on any linux or windows desktop and then export the config to the machine of your choice.

---

