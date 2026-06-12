---
title: "Blocking msn only to one computer"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by brunoskrebs on 2009-07-18
Hi there,

actually I'm just wondering if it is possible to block the msn usage to a single computer. The company that administers the network in the place that I work told me that this is not possible...

Oh by the way they use iptables and squid.

---

### Post by lensman3 on 2009-07-18
Using IPTABLES you could block packets from msn to an internal host and visa-versa.  If msn uses multiple IP numbers a rule would have to be setup for each IP number.  The rule could block ICMP, TCP, and UDP packets.

The form would be similar to:
# US-DOD
DOD_NET="214.0.0.0/8 \
         215.0.0.0/8" 

   for NET in $DOD_NET; do
       $IPTABLES -A no-way -s $NET -j special
   done

   $IPTABLES -A no-way -j RETURN

This is a code snippet where I block all packets coming from the U.S. Department of Defense Networks.

This code line routes SKYPE to an interal network machine:
${IPTABLES} -A OK-Pass -i ${EXTERNAL} -o ${INTERNAL} -p tcp --sport 1024:65535 -d 192.168.200.10 --dport $SKYPE -m state --state NEW -j ACCEPT

To change it to drop then change ACCEPT to DROP.  

Another way would be to set in the hosts file on the computer you want blocked 

msn.com 127.0.0.1

That way all msn.com dns requests go to the localhost.  Unfortunately, the workaround would be to enter msn's IP address number.  (MSN's home page would probably be accessed OK, but subpages would probably fail if MSN couldn't be resolved. 

It actually might be easier to block all your machines from going to msn, and then re-permit the machines that should have access.

---

### Post by brunoskrebs on 2009-07-20
Ok thanks lensman. I'm going to study these rules, cause I'm (still) not an expert :D

---

