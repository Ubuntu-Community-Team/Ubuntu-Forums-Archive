---
title: "internet access from subnet on 2nd nic"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by xardoz on 2012-12-18
I'm not sure whether this question relates to bridging or routing but I've searched in vain for both as a solution.

I have a pc that has 2 nics.  One nic has a dhcp assigned address in the 192.168.0.x range and has a gateway at 192.168.0.250, and dhcp server at 192.168.0.1.  This nic is part of the main corporate network.

The other nic has been set up as a head node in a compute cluster, with a fixed address of 192.168.2.1.  
There are three headless machines hanging from this second nic and are only accessible from the head node, typically via ssh.  They all have a fixed address in the 192.168.2.x range and a gateway of 192.168.2.1.

These three machines are woefully out of date and I would like them to be able to access the internet so they can be upgraded but I can't figure out how to do it.  I've tried bridging and adding static routes but all I have managed to do is break all internet connectivity from my pc.

I'm sure this is possible and am equally convinced that it is simple and I am just missing something.  I would be grateful for any help.

---

### Post by SeijiSensei on 2012-12-18
You need to add a "masquerading" rule to the dual-homed machine.  The simplest solution is to add this command to /etc/rc.local:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.0.x
```

This assumes that eth0 points upstream.  Replace 192.168.0.x with the IP of the address assigned to eth0.

---

### Post by xardoz on 2012-12-18
I just tried that as a command line to test and have lost all network connections. How do I undo that command? I'm having to use my phone to post.

Rebooted because all connected users lost their connection and it is restored.  Needless to say that didn't work!  I only need it temporarily so a command would be better.  I can't find options -o and --to-source in the man page so can't really work out what the command is doing.

---

### Post by xardoz on 2012-12-18
That post gave me an idea so I searched for masquerading and found the following that seems to work:

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

Thanks for the hint.

---

