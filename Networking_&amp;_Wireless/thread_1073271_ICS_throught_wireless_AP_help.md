---
title: "ICS throught wireless AP help"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by brian183 on 2009-02-18
Hi everybody, need some help with my network setup.

I have, for a long time, used home built routers for all my network needs because I've determined through many years of using consumer grade routers that they just don't cut it when compared to an old PC setup with a couple NICS in it. I'm in a situation now that I don't have the luxury of an old PC around to use for a router.  What I do have is a modern PC (host) with a couple NICS, one DSL modem that works just fine, one DI-624 dlink router and one client PC that needs to have internet access through wireless connectivity. My goal is to have my client PC connect wirelessly through the DI-624 router to my host PC which is where my DSL connection is going through.

Currently, I'm connected to the DSL modem with my host PC and internet is working fine on it.
This my network setup:
eth0 - My DSL connection, this is working fine.
eth1 - local network, connected to my DI-624 router which is wireless AP.

eth1 has a static IP of 10.0.0.1, DHCP is enabled and iptables are set to pass traffic back and forth to eth0.
DI-624 has a static IP of 10.0.0.2, no DHCP, wireless settings are correct.

Situation so far, i can connect wirelessly through the DI-624 to my host PC.  I get a DHCP IP lease and i can ping 10.0.0.1 and 10.0.0.2 from the wireless client.  I can't ping anything externally from the wireless client pc, both IP and domain so I dont think its a DNS issue.

What I think the issue is, traffic routing.  I think my iptables are set right but I could be wrong.  Here's my output of "iptables -L":
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  10.0.0.0/24          anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

---

### Post by superprash2003 on 2009-02-18
what is the ip of the dlink?? have you disabled DHCP there??[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

