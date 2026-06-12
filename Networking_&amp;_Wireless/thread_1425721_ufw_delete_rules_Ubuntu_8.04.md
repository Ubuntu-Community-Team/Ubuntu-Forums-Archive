---
title: "ufw delete rules Ubuntu 8.04"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by mreiter on 2010-03-09
Just to help out in case your cannot delete a rule inserted in the Firewall ufw:
 
With Ubuntu 8.04 (maybe other versions)
 
I had the following rules
22:tcp ALLOW <IP>
22:udp ALLOW <IP>
 
But I was not able to delete the udp rule with the following command:
sudo ufw delete allow proto udp from <IP> to any port 22 
 
So I solved it in the following way
sudo ufw delete allow from <IP> to any port 22
sudo ufw allow proto tcp from <IP> to any port 22

---

