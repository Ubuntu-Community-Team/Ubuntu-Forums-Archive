---
title: "[android] iptables, what's with the 101com.com thing?"
date: 2015-01-27
forum: Mobile Technology Discussions (CLOSED)
---

### Post by azzamite on 2015-01-27
I've been trying to add com custom lines to the firewall of my phone
```
iptables -A OUTPUT -o droidwall -d partnerad.l.google.com -j droidwall-reject
iptables -A OUTPUT -o eth0 -d googlesyndication.com -j DROP
iptables -A OUTPUT -o eth0 -d pagead.l.google.com -j DROP
```
But it doesn't matter what the destination is, when I list the rules, they always shows as 101com.com
```
droidwall-reject  all  --  anywhere             101com.com          
DROP       all  --  anywhere             101com.com
```

Any idea what's going on?

---

### Post by Doug S on 2015-01-27
That is strange. What do you get for forward and reverse lookups? i.e.```
doug@desk-dev:~$ [COLOR=#ff0000]nslookup googlesyndication.com[/COLOR]
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   googlesyndication.com
Address: 74.125.28.99
Name:   googlesyndication.com
Address: 74.125.28.103
Name:   googlesyndication.com
Address: 74.125.28.104
Name:   googlesyndication.com
Address: 74.125.28.105
Name:   googlesyndication.com
Address: 74.125.28.106
Name:   googlesyndication.com
Address: 74.125.28.147

doug@desk-dev:~$ [COLOR=#ff0000]nslookup 74.125.28.99[/COLOR]
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
99.28.125.74.in-addr.arpa       name = [COLOR=#ff0000]pc-in-f99.1e100.net[/COLOR].

Authoritative answers can be found from:
125.74.in-addr.arpa     nameserver = ns3.google.com.
125.74.in-addr.arpa     nameserver = ns2.google.com.
125.74.in-addr.arpa     nameserver = ns1.google.com.
125.74.in-addr.arpa     nameserver = ns4.google.com.

doug@desk-dev:~$
```Becuase when I try to do what you did, I get:```
sudo iptables -A OUTPUT -o eth0 -d googlesyndication.com -j DROP
``````
doug@desk-dev:~$ [COLOR=#ff0000]sudo iptables -v -x -L[/COLOR]
Chain INPUT (policy ACCEPT 98412 packets, 145267767 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 55874 packets, 3454342 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f105.1e100.net
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f106.1e100.net
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f147.1e100.net
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f99.1e100.net
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f103.1e100.net
       0        0 DROP       all  --  any    eth0    anywhere             pc-in-f104.1e100.net


doug@desk-dev:~$ [COLOR=#ff0000]sudo iptables -v -x [/COLOR]-n[COLOR=#ff0000] -L[/COLOR]
Chain INPUT (policy ACCEPT 98454 packets, 145271858 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 55923 packets, 3461122 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.105
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.106
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.147
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.99
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.103
       0        0 DROP       all  --  *      eth0    0.0.0.0/0            74.125.28.104
doug@desk-dev:~$
```

---

### Post by azzamite on 2015-01-27
> **Doug S said:**
> That is strange. What do you get for forward and reverse lookups?

Thanks, with the reverse lookup (and reading a little about iptables) I discovered the problem:

- iptables lookups the IP when the host is provided
- I had 127.0.0.1 googlesyndication.com in /etc/hosts, hence that was being blacklisted
- iptables reverse lookups the hostname from the IP when listing the rules
- I had 127.0.0.1 101com.com as the first entry in /etc/hosts, thereof that was showing

So I just cleaned my hosts file, and it's now showing the hosts Doug S got.

Regards

---

