---
title: "Need to open UDP ports on firewall"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by Alnico on 2009-07-17
I have configured Firestarter to pass the SheildsUp! Test.

Now I need to configure my system to allow inbound and outbound UDP to ports 5198 and 5199, and outbound TCP to port 5200. 

([http://www.echolink.org/firewall_solutions.htm](http://www.echolink.org/firewall_solutions.htm)) 

How do I do this in Ubuntu? And is there a where I can close the opened ports after I am done so as not to leave a possible security hole?

Thanks!

---

### Post by jasonsjunk on 2009-07-17
Your answer is here [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

However you may need to configure your router if you are using one.  To configure your router you can look here [http://portforward.com/](http://portforward.com/) this should have information specific to your router.

Additional information on port forwarding for your router can be found here: [http://www.ehow.com/how_4550488_open-router-ports.html](http://www.ehow.com/how_4550488_open-router-ports.html)

---

### Post by Alnico on 2009-07-17
Thanks, from what I understood, would this be the correct syntax then?

```
$ # iptables -A INPUT -p udp --dport 5198 -j ACCEPT$ # iptables -A INPUT -p udp --dport 5199 -j ACCEPT
$ # iptables -A OUTPUT -p udp --dport 5199 -j ACCEPT
$ # iptables -A OUTPUT -p udp --dport 5198 -j ACCEPT
$ # iptables -A INPUT -p tcp --dport 5200  -j ACCEPT
```

---

### Post by Alnico on 2009-07-22
Anyone?

---

### Post by jasonsjunk on 2009-07-24
Yes it looks good to me.

---

