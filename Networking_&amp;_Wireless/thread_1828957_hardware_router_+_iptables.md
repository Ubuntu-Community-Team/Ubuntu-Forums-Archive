---
title: "hardware router + iptables"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by Roque on 2011-08-19
My net setup is as follows: 
```

adsl modem --- adsl router --- PC1
                            |
                            |
                            -- PC2  

```

The router's built-in firewall is minimal, so it does not allow for complex filtering rules like iptables does.
My question is: is it possible to setup iptables so it does the filtering in PC1 and PC2 instead of filtering at the router level?

Thanks for any answers

---

### Post by lmarmisa on 2011-08-20
> **Roque said:**
> My net setup is as follows: 
```

adsl modem --- adsl router --- PC1
                            |
                            |
                            -- PC2  

```

The router's built-in firewall is minimal, so it does not allow for complex filtering rules like iptables does.
My question is: is it possible to setup iptables so it does the filtering in PC1 and PC2 instead of filtering at the router level?

Thanks for any answers

If PC1 and PC2 are Linux machines, they will run iptables and you will be able to add the rules you want. But PC1 and PC2 are located in your LAN and they have private IP addresses. Your router is the only responsible for the NAT function and you can not define rules related to NAT in your computers PC1 or PC2.  

Another interesting option would be to check if your ADSL router is able to run a Linux firmware like [DD-WRT]("http://www.dd-wrt.com") or [Tomato]("http://www.polarcloud.com/tomato").

---

### Post by Roque on 2011-08-20
Thanks Imarmisa. Yes they are Linux PCs, so you say I should be able to add non-NAT filter rules to PC1 and PC2 for opening/closing certain ports, for example? 
Because it seems that I can't use iptables to filter ping requests for PC1 or PC2 (the router's firewall seems to take exclusive care of this)

Regarding your Linux firmware comment, this is not an option for now.

---

