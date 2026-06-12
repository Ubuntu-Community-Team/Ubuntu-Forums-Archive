---
title: "iptables script ignored on boot - will run manually"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by chip616 on 2009-02-28
I am running Kubuntu 8.04.  I have a custom iptables script that blocks Internet access to all sites except one.  I use this on my work machines to prevent 'silliness' in the use of the shop machines.  The script is as follows:

```
#!/bin/bash
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -N o-eth0
/sbin/iptables -A o-eth0 -j ACCEPT -d 192.168.1.0/24
/sbin/iptables -A o-eth0 -j ACCEPT -d neomedia.micropaint.net
/sbin/iptables -A o-eth0 -j REJECT
/sbin/iptables -A OUTPUT -j o-eth0 -o eth0
```

This script is saved as 'firewall' in the /etc/init.d directory, and has permissions 555.

The following command was used to install it:

```
update-rc.d firewall defaults 99 

```

When the machine does a fresh boot, the output from the command iptables -L yields:

```
frank@office:~$ sudo iptables -L
[sudo] password for root:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
o-eth0     all  --  anywhere             anywhere

Chain o-eth0 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.1.0/24
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
```

Notice that access to the local LAN at 192.168.1.0/24 is registered, but the link to the neomedia site is NOT.  For some reason it is being ignored.

Now, the interesting part is that the script itself works just fine.  I can run that script manually as follows:

```
sudo /etc/init.d/firewall start
```

and everything works just fine.  In fact, here is the output from iptables -L again, AFTER running the manual start of the script as shown above.

```
frank@office:~$ sudo /etc/init.d/firewall start
frank@office:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
o-eth0     all  --  anywhere             anywhere

Chain o-eth0 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.1.0/24
ACCEPT     all  --  anywhere             72.13.190.4
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
frank@office:~$
```

Notice that this time, the script correctly resolves the ip address of the neomedia site (72.13.190.4) and inserts that into the iptables rules.

Remember that this is the exact, same, identical script that is run at boot through the init.d process.  At boot, the ip address of the neomedia site is NOT resolved, and that particular rule is NOT instituted, but is rather ignored.  However, if the script is rerun after the machine is up, THEN it resolves the address of the neomedia site just fine.

Now, one more clue:  I edited the firewall script as follows:

```
#!/bin/bash
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -N o-eth0
/sbin/iptables -A o-eth0 -j ACCEPT -d 192.168.1.0/24
/sbin/iptables -A o-eth0 -j ACCEPT -d 72.13.190.4
/sbin/iptables -A o-eth0 -j REJECT
/sbin/iptables -A OUTPUT -j o-eth0 -o eth0
```

The ONLY change here is that I removed the reference to neomedia.micropaint.net and replaced it with the resolved ip address of 72.13.190.4.  This works on boot as it should.  The neomedia site is available immediately after boot, and so is my local LAN.  All is well if I don't rely on DNS to resolve the ip address of the neomedia site.

To me this suggests that DNS is not available when the script is running at boot, but IS available when the machine is fully up and running, as the script works manually at that point, correctly resolving the ip address of the neomedia site.

I've run out of ideas, unless it has something to do with run levels, and DNS perhaps not being available at the time that the firewall script is run on boot.  However, I have only a hazy understanding of run levels and I have no idea what to do to fix this.

So, I beg for some assistance here.  I'd let it drop and just use the ip address, but it is my understanding that an ip address can change even if the url does not.  I am led to believe that this is what happens if a domain is hosted on a different server.

By the way, I've used this script for years on my Xandros boxes, and they have always resolved the ip address during boot with no problem.  I know that the script works.  It just won't resolve the ip address during boot on 8.04.

Thanks.

Frank.

---

