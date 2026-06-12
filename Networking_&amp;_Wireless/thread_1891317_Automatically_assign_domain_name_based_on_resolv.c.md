---
title: "Automatically assign domain name based on resolv.conf file?"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by cheg11 on 2011-12-05
I am using Ubuntu 11.10 and Wicd as my network manager.

I would like to be able to ping my FQDN from another computer on the network.  I am able to do this on windows but have had trouble accomplishing it on Ubuntu. 

Typically, when I type in dnsdomainname the value is null.  The only way to fix this is to go to /etc/hosts and type in my ip address and then my fqdn.  

However, I want my computer to automatically assign me a domain name based on the content in /etc/resolv.conf  .  

Is there any way to do this?

---

### Post by cheg11 on 2011-12-05
Something to mention...

The DNS domain name resolved when I use Network Manager.  Although Network Manager does not hold the connection for more than 1 minute, thus my decision to switch to wicd.  Perhaps it is some config file in wicd?

---

### Post by cheg11 on 2011-12-06
I decided to focus on using Network Manager and just figuring out why the connection dropped out after a minute. 

This seems to have fixed it:

rmmod iwlagn
modprobe iwlagn 11n_disable=1
(or modprobe iwlagn 11n_disable50=1)

not sure what file I can change to permanently change this.  Apparently there is a known issue with the iwagln driver.

---

