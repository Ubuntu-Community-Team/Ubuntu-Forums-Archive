---
title: "IPTables now showing port open"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by DragonDon on 2010-09-22
Greetings all!

Slowly, but surely, I am getting the hang of IPTables.

I've setup to open certain UDP ports but they simply refuse to show when I iptables -L.

iptables file:

$IPT -A INPUT -p udp --dport 13000 -j ACCEPT
$IPT -A INPUT -p udp --dport 13001 -j ACCEPT
$IPT -A INPUT -p udp --dport 5060 -j ACCEPT
$IPT -A INPUT -p udp --dport 5061 -j ACCEPT
$IPT -A INPUT -p udp --dport 6060 -j ACCEPT
$IPT -A INPUT -p udp --dport 6061 -j ACCEPT

Out of iptables -L:

Chain INPUT (policy DROP)
target     prot opt source               destination         
pgl_in     all  --  anywhere             anywhere            state NEW mark match !0x14 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:xmpp-client 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55535 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:55535 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55332 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:39932 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:2082 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sip 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sip-tls 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6060 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6061 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:13000 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:13001 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 


It is annoying that 4 out my defined 6 UDP ports are showing.

So what am I missing here?

Full IPTables file: [http://paste.ubuntu.com/498615/](http://paste.ubuntu.com/498615/)
Full 'iptbles -L' output: [http://paste.ubuntu.com/498617/](http://paste.ubuntu.com/498617/)

---

### Post by gzarkadas on 2010-09-22
The lines with "sip" and "sip-tls" are your "missing" ports. You can verify it by doing:
```

cat /etc/services | grep 506[01]

```You may also supply the -n switch to iptables -L to show numbers instead of names.

---

### Post by DragonDon on 2010-09-22
Ah, that would make sense.  I saw those but mentally just glossed over them without associating them.  Thanks.

Now I just have to figure out where the hold up is on my voip program not getting any sound (company said it's usually blocked UPD ports).  So now that's cleared up, onto further troubleshooting!

Thanks again.

Don

---

