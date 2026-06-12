---
title: "Internet ftp &quot;connection refused&quot; works loacally"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by PeggySue on 2010-03-23
Hi,
I am trying to set up an ftp server on my home machine so a friend and I can exchange large files.  I have set up pure-ftp server and gftp client.

Pure-ftp works fine behind my Dlink DSL 2740B router using host name '192.168.1.100' but not over the internet using host name '80.47.xxx.xxx'  I get the message> 
Looking up 80.47.xxx.xxx
Trying 80.47.xxx.xxx:21
Cannot connect to 80.47.xxx.xxx: Connection refused
Operation cancelled

I have set up port forwarding as per the attachment.

I haven't set up a software firewall and my iptables -L looks like:> 
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

The username I am using is part of "ftpgroup" and is the same user that works behind the router.

Putting the computer in the DMZ doesn't help.

I have a similar problem with SSH so I assume the problem is with the router.

Other threads suggest the culprits should be port forwarding or a firewall but I can't see what is wrong.  Any ideas would be most welcome.

---

### Post by PeggySue on 2010-03-29
The answer was a router issue.
The instructions that say you can test your internet access from your home machine are not always true. You need NAT Loopback.
Quote from DLINK DSL-2740B Support Pages:> 
Question :
Why can I not access my webserver using the WAN IP address?
 
Answer :
Your router has no support for NAT Loopback, and can therefore not view a server by its WAN IP, from the LAN.
To view your servers from a LAN computer, use the LAN IPaddress of the server.
To view your servers from the internet, use the WAN IPaddress.

---

