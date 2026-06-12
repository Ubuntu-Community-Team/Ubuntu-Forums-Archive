---
title: "problem with deluge"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by gugu88 on 2012-01-30
Hi everybody,
i have a problem with deluge. it constantly shows the message "no incoming connections" and if i test the active port in the preference menu it does not work. I tried to follow some threads but without any result. It should not be a router problem because bittorrent on windows works perfectly. I tried to test several port either with high number (more then 45000) and with low number (less then 10000) and either with deluge and with trasmission but the result is the same: PORT CLOSED!!! I tried also to deactivate the firewall with the command ```
sudo ufw disable
``` but it didn't change anything so i reactivated it, then i tried the following command to restore the iptables ```
sudo iptables -F
``` but with no results. I read that by default ubuntu have every port opened so i can not understand the problem. How can i test which port are open and how can i open other ports??? 
I'm using ubuntu 10.04 64 bit.

Any help or suggestion will be appreciated.

Thanks

bye

---

