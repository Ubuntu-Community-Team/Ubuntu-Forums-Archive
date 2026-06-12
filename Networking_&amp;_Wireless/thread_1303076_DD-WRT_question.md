---
title: "DD-WRT question"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by Loki57701 on 2009-10-27
I already posted this question in the DD-WRT forum but I never got a reply so I'm hoping someone here has the answer..

I flashed my Linksys WRT54G router with the mini-build required for initial flashing of the router. Everything went great but now I'm wondering if I need to upgrade from the mini-build on to the standard-generic build? Should I do this or is it not necessary unless I want more features ect..

---

### Post by Lars Noodén on 2009-10-28
No need to unless there are features you are missing that keep you from working.  That assumes that your hardware can handle the standard-generic build.

---

### Post by Loki57701 on 2009-10-28
Do you know if the default iptables setup for DD-WRT is secure for a small home network, or do I need to make changes? For instance I know that port 8080 is kept open for web GUI management (I think).
Basically I'm just trying to make sure that after setting up the basic networking stuff, new admin password, and wireless security, that its secure enough out of the box so to speak. There are alot of options and configuration settings that I don't know much about. I've read the dd-wrt wiki pages but there not much help really.

Again sorry about posting this on here but the dd-wrt community forum is just non-responsive.

---

### Post by kevdog on 2009-10-29
You know you can run commands using DD-WRT within the execute window to see what your current Iptables are right?

For example in the 

Administration->Commands Tab

Within the Command dialog box I typed:

iptables -L

And got the following:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       udp  --  anywhere             anywhere            udp dpt:route 
DROP       udp  --  anywhere             anywhere            udp dpt:route 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:route 
DROP       icmp --  anywhere             anywhere            
DROP       igmp --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state NEW 
logaccept  0    --  anywhere             anywhere            state NEW 
DROP       0    --  anywhere             anywhere            
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     gre  --  192.168.1.0/24       anywhere            
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:1723 
ACCEPT     0    --  anywhere             anywhere            
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
lan2wan    0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
TRIGGER    0    --  anywhere             anywhere            TRIGGER type:in match:0 relate:0 
trigger_out  0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state NEW 
DROP       0    --  anywhere             anywhere            
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
Chain advgrp_1 (0 references)
target     prot opt source               destination         
Chain advgrp_10 (0 references)
target     prot opt source               destination         
Chain advgrp_2 (0 references)
target     prot opt source               destination         
Chain advgrp_3 (0 references)
target     prot opt source               destination         
Chain advgrp_4 (0 references)
target     prot opt source               destination         
Chain advgrp_5 (0 references)
target     prot opt source               destination         
Chain advgrp_6 (0 references)
target     prot opt source               destination         
Chain advgrp_7 (0 references)
target     prot opt source               destination         
Chain advgrp_8 (0 references)
target     prot opt source               destination         
Chain advgrp_9 (0 references)
target     prot opt source               destination         
Chain grp_1 (0 references)
target     prot opt source               destination         
Chain grp_10 (0 references)
target     prot opt source               destination         
Chain grp_2 (0 references)
target     prot opt source               destination         
Chain grp_3 (0 references)
target     prot opt source               destination         
Chain grp_4 (0 references)
target     prot opt source               destination         
Chain grp_5 (0 references)
target     prot opt source               destination         
Chain grp_6 (0 references)
target     prot opt source               destination         
Chain grp_7 (0 references)
target     prot opt source               destination         
Chain grp_8 (0 references)
target     prot opt source               destination         
Chain grp_9 (0 references)
target     prot opt source               destination         
Chain lan2wan (1 references)
target     prot opt source               destination         
Chain logaccept (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
Chain logdrop (0 references)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            
Chain logreject (0 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            tcp reject-with tcp-reset 
Chain trigger_out (1 references)
target     prot opt source               destination

---

### Post by Loki57701 on 2009-10-29
Yes, I used telnet to check the rules for iptables but unfortunately I don't know enough about it to really make sense of it.

---

### Post by Lars Noodén on 2009-10-29
Another way to make use of kevdog's suggestion would be to see if you can run [iptables-save](http://manpages.ubuntu.com/manpages/karmic/en/man8/iptables-save.8.html). It will give you the same data as [iptables -L](http://manpages.ubuntu.com/manpages/karmic/en/man8/iptables.8.html) but in another way of looking at it.

To start with IPTables, there are not so many tutorials around but here are two to start with.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[http://www.frozentux.net/documents/iptables-tutorial/](http://www.frozentux.net/documents/iptables-tutorial/)

You might take a look at **OpenVAS** and practice scanning inside your network.  Then, if you can do it safely, use a machine outside your network to scan your gateway for vulnerabilities.  

Working with IP Tables can be fun, but unless you are doing hosting there's not a whole lot these filters can do beyond allowing packets from the inside go out and allow packets that appear to be associated with the outgoing packets in.  You can limit rates and a few other things, but if there is a way out, there is a way in.  

For example, if you connect to sites that inflict scripts (javascript or worse activex) on your browser, you are in effect running programs on your machine.  If you are doing that over IPv4 and without either IPSEC or HTTPS then other parties can inject their own programs, saying they are some other site.  

Take a look at the output from traceroute to see the number of hops from your machine to ubuntuforums.org. 
```

# the regular way
traceroute -n ubuntuforums.org

# or if the network is broken, use TCP SYN to port 80 (www)
sudo traceroute -n -T -p 80 ubuntuforums.org

```

Mine shows that my packets pass through over 25 networks today. :(  Yours will probably show some other number, larger or smaller, but any of those will be able to throw something over the fence into your yard.

---

