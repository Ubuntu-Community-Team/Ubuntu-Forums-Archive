---
title: "Cannot Access Local Area Network Websites on Ubuntu 8.10"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by skhalil on 2008-12-09
Hello Freinds, This is the first time that I am requesting help from you guys directly. I have upgraded recently from 8.04 to 8.10 and now I have a strange problem. I my web browsers does not open the websites on my LAN. I am using a DSL cable internet connection and I have to turn it off in order to access the websites on my LAN. But since I have upgraded to 8.10 I can't access any of them. I have tried the live cds of Ubuntu and Kubuntu both have the same problem. While the live cds of 8.04 works fine and I have access to these websites. Please help me if there have been any change in the networking structure of the new 8.10 version or any software or service is dropped or turned off by default. Please help! otherwise I have to downgrade to 8.04.

Regards,

Khalil

---

### Post by dragos_iliescu_2005 on 2008-12-09
Check the settings in Network Manager. Setting here correct, it should enable the Internet connection

---

### Post by skhalil on 2008-12-09
Sorry, But, as I have already mentioned the internet connection is not a problem. I use cable DSL connection and it is working fine. the problem is the websites on my LAN, which I cannot open from Ubuntu Intrepid 8.10, while I was easily openning it on my previous Ubuntu Hardy system. Please consider this and help me out.

---

### Post by Iowan on 2008-12-09
Check network settings (ifconfig) when machine is powered up without internet connection.  Network Manager continues to evolve, but before casting blame on it, check other possibilities: avahi sometimes kicks in and assigns address in 169.254.X.X. Since this is most likely not in the same subnet as your other machines, it can't see them.  But that's just one possibility.

---

### Post by jonobr on 2008-12-09
Im guessing you can ping the websites.

Did you try telnet <IPaddress of server> 80
then try telnet <servname> 80

after both, when you get in type get and see if it responds to you.
You could also try using w3m to name and ip address, see what happens

---

### Post by dragos_iliescu_2005 on 2008-12-10
In this case I think you should offer informations about your LAN configuration.

---

