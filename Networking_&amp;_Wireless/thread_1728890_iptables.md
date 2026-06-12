---
title: "iptables"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by drpsycho on 2011-04-14
Hi, I want to liberate 100% a machine that is behind a firewall via iptables. Or maybe redirect it to not pass trouhgh the thousand rules of the firewall. 
 
I've already put rules like this but anything works:
 
iptables -I FORWARD -s x.x.x.x -j ACCEPT
 
thanks

---

### Post by ajgreeny on 2011-04-14
You can flush the iptables setings to default and then restart networking with:
```
sudo iptables -F 
sudo /etc/init.d/networking restart
```and that should get you back to where you would be before adding any rules.

---

### Post by iponeverything on 2011-04-14
If its behind a firewall, changing the rules on that machine is going to have no effect. It is like opening the sunroof on your car to get some sun when it is inside a garage.


It should also be noted that using the forum for information on subverting access restrictions violates the CoC.

---

### Post by drpsycho on 2011-04-25
> **iponeverything said:**
> If its behind a firewall, changing the rules on that machine is going to have no effect. It is like opening the sunroof on your car to get some sun when it is inside a garage.


It should also be noted that using the forum for information on subverting access restrictions violates the CoC.

I am the firewall administrator!! I want to liberate 100% a machine in my network. You understood everything wrong! hehehe

I don't wanna flush my iptables rules because it would affect the other machines. I just wanna liberate one exclusive machine. I was thinking if I could do some nat or redirection to make the machine go directly by the isp gateway, the firewall serving only as router.

---

### Post by SeijiSensei on 2011-04-25
Changing the FORWARD rule might break masquerading.  Try adding an INPUT rule instead.  You'll still need to masquerade the host (and presumably all the others inside the network) in the nat table.  Probably something like this:

```

EXTI=eth0
EXTIP=192.168.1.1
iptables -A INPUT -s 10.10.10.10 -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTI -j SNAT --to $EXTIP

```

where EXTI and EXTIP are the name and IP address of the Internet-facing interface.

Do you control access with INPUT rules?  That's usually my choice over FORWARD rules.

---

### Post by drpsycho on 2011-04-27
> **SeijiSensei said:**
> Changing the FORWARD rule might break masquerading.  Try adding an INPUT rule instead.  You'll still need to masquerade the host (and presumably all the others inside the network) in the nat table.  Probably something like this:

```

EXTI=eth0
EXTIP=192.168.1.1
iptables -A INPUT -s 10.10.10.10 -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTI -j SNAT --to $EXTIP

```where EXTI and EXTIP are the name and IP address of the Internet-facing interface.

Do you control access with INPUT rules?  That's usually my choice over FORWARD rules.

It didn't worked. Emule works, torrent works, and other stuffs like these works. But the the applicattion they asked me don't. I wanna liberate everything for one machine only without interfering in the other machines.

---

### Post by SeijiSensei on 2011-04-27
Well those were examples of how to go about fixing this.  As I said it depends on how you block access.  You'll need to go through your ruleset with a fine-tooth comb and figure out how to adapt my examples to your particular needs.

I'd start by listing the entire ruleset with "iptables -L -nv" and "iptables -t nat -L -nv" and staring at them for a while.  [http://www.netfilter.org/](http://www.netfilter.org/) is your friend if you need more detailed help than "man iptables" provides.

---

### Post by drpsycho on 2011-04-27
> **SeijiSensei said:**
> Well those were examples of how to go about fixing this.  As I said it depends on how you block access.  You'll need to go through your ruleset with a fine-tooth comb and figure out how to adapt my examples to your particular needs.

I'd start by listing the entire ruleset with "iptables -L -nv" and "iptables -t nat -L -nv" and staring at them for a while.  [http://www.netfilter.org/](http://www.netfilter.org/) is your friend if you need more detailed help than "man iptables" provides.

This firewall is big, has hundreds of rules and the worst is that it was not configured by me. I tried to liberate the machine using shorewall too with no success.
I put this:

ACCEPT:info      adm:x.x.x.x      all+-

---

