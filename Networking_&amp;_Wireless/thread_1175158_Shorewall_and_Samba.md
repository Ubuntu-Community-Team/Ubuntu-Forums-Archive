---
title: "Shorewall and Samba"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by creamcheeze77 on 2009-05-31
Hey guys,
I was trying to set up a firewall on my little samba server for some security, by adding the following to /etc/shorewall/rules :
```

#ACTION   SOURCE   DEST   PROTO    DEST PORT(S)   SOURCE
#                                                 PORT(S)
AllowSMB  fw       loc
AllowSMB  loc      fw

```
however, when i try to restart shorewall, i get the following error:
```
Starting "Shorewall firewall": not done (check /var/log/shorewall-init.log).
```
anyone know what's going on?  samba's installed and running perfectly

---

### Post by dmizer on 2009-05-31
Have a look here: [http://www.shorewall.net/samba.htm](http://www.shorewall.net/samba.htm)

---

### Post by creamcheeze77 on 2009-05-31
> Have a look here: [http://www.shorewall.net/samba.htm](http://www.shorewall.net/samba.htm)
I actually tried that first, exact same problem.

---

### Post by dmizer on 2009-05-31
Please post the output of:
```
sudo iptables -L
```
Are you using Jaunty? I wonder if there's perhaps some interference between UFW and Shorewall?

Anything revealing in /var/log/shorewall-init.log?

---

### Post by creamcheeze77 on 2009-05-31
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

the output of the log is:

```
Shorewall has detected the following iptables/netfilter capabilities:
   NAT: Available
   Packet Mangling: Available
   Multi-port Match: Available
   Extended Multi-port Match: Available
   Connection Tracking Match: Available
   New Connection Tracking Match Syntax: Available
   Packet Type Match: Available
   Policy Match: Available
   Physdev Match: Available
   Physdev-is-bridged Support: Available
   Packet length Match: Available
   IP range Match: Available
   Recent Match: Available
   Owner Match: Available
   Ipset Match: Not available

```
this is with shorewall disabled, if it makes a difference.  and yes, i'm using 9.04

---

### Post by jvleta on 2011-02-13
Were you ever able to resolve this issue?  I'm having the EXACT same problem right now with ubuntu server 10.04.

---

### Post by dmizer on 2011-02-13
If you're sharing files over samba, that probably means you're on a LAN with only indirect (usually via a firewalled gateway/router) access to the Internet. This means that you probably don't need a firewall at all. If you think you DO need a firewall, you should really think about how wise it is to poke holes in it to facilitate samba file sharing. By poking holes in your firewall for samba sharing, you're essentially removing all the protection the firewall offers.

I know this really isn't a direct answer to the problem asked in this thread, but it's something to seriously consider.

---

### Post by duceduc on 2012-02-25
I am having same issue after I upgrade shorewall from 4.2 to 4.5. After which, I am unable to see my server network. When I was on 4.2, I didn't have to set a rule for samba and it was working.

At any rate, I also tried the link dmizer have provided, but it didn't solve my issue. The only thing seems to work if I disabled shorewall completely.

---

