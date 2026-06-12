---
title: "Firehol, NFS pass my firewall?"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by Epeli on 2006-04-12
Hi!

How do I make a rule in Firehol config to allow NFS traffic? NFS uses so many ports that I don't know which one to open to make it work.

I'm denying all unnessesary traffic with firehol and I need to make a rule which allows NFS traffic.


I'm using [this]("http://ubuntuforums.org/showthread.php?t=132039") howto as base for my config. Attached my config.

Ps.Please excuse my english ;)

---

### Post by frodon on 2006-04-13
You will find information on which port use a service in the file : /etc/services.
Why not configuring iptables rules yourself, it's not really complicated, see my guide (nearly finished) : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by Epeli on 2006-06-18
--

---

### Post by Epeli on 2006-06-18
Argh, I can't get it working...

I've put this in my firewall script:
```

# NFS

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 2049 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 2049 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 111 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 111 -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1014:1017 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 1014:1017  -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 940 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 937 -j ACCEPT

iptables -A TRUSTED -i eth0 -p udp -m udp --dport 369 -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 51247 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 32768 -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 890:900 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 890:900 -j ACCEPT



```

And still can't get it working.

```
epeli@kumikone:~$ sudo /etc/init.d/nfs-common restart ; sudo /etc/init.d/nfs-kernel-server restart
 * Stopping nfs statd...                                                                                     [ ok ]
 * Starting nfs statd...                                                                                     [fail]
 * Stopping rpc mountd...                                                                                    [ ok ]
 * Stopping rpc nfsd...                                                                                      [ ok ]
 * Unexporting directories for NFS kernel daemon...                                                          [ ok ]
 * Exporting directories for NFS kernel daemon...                                                            [ ok ]
 * Starting rpc nfsd...                                                                                      [fail]
```

---

