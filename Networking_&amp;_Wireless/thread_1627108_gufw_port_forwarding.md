---
title: "gufw port forwarding"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-11-21
Ok here is what I have, ! server Firewalled ,Gufw, connects to internet laptops connects via etho cable lan ip, another laptop connects via wireless DIFFERENT lan ip, I want to ssh from 1st laptop to 2nd laptop if firewall is of it works on it dosn't. What sort of rule do I need to put in firewall. The laptops have different port numbers for ssh

---

### Post by spiky001 on 2010-11-22
Bump

---

### Post by spiky001 on 2010-11-23
O i,m bumping again if more info required let me know

---

### Post by spiky001 on 2010-11-24
Someone must know how to set fw to allow pass through from lan to wireless

---

### Post by cariboo on 2010-11-24
Open gufw  and unlock, then go to Edit->Add Rule, click the preconfigured tab and set:

Allow in Service SSH

on each system you want to ssh into. You don't have to allow it out, as ssh uses a random port for outbound connections.

BTW if you are using a router with a builtin firewall, you really don't need to use firewalls on your internal network

---

### Post by spiky001 on 2010-11-25
Ok that didn't work I dont have a router so thats why there is a FW, now I have a laptop ip 10.42.43.10....eth0....>server **10.42.43.1 eth0/&.10.42.44.1wlan0/**wlan0..10.42.44.1........>laptop2 10.42.44.11. I allowed on server (only pc with firewall) allow ssh in anywhere, Now server has different ssh port, lap2 has port 22. So I want to go from 1st laptop (ip **10.42.43.10** eth0) to laptop2 (ip **10.42.44.11** wlan0). Now I dont think FW is stopping me as I have tried again cant get through, So I need to hop on to the other ip address to complete connection

---

