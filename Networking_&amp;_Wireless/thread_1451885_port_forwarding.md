---
title: "port forwarding"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by boondocks on 2010-04-11
I have a Ubuntu system that has 2 network cards.

[INDENT]eth0 with ip address [COLOR="Red"]192.168.1.23[/COLOR]

eth1 with ip address [COLOR="Green"]192.168.7.15[/COLOR]
[/INDENT]

I would like do port forwarding such that anything for
[INDENT][COLOR="Red"]192.168.1.23:19320[/COLOR][/INDENT]
is forwarded to
[INDENT][COLOR="Green"]192.168.7.15:19340[/COLOR][/INDENT]
and it should stay that way after rebooting.

How do you do this?

---

### Post by Iowan on 2010-04-11
**iptables** comes to mind. **ufw/gufw** may be another approach to the same thing. (Unfortunately, another area I have yet to learn...)

---

### Post by stilling on 2010-04-11
see this

[http://ubuntuforums.org/showthread.php?t=93420](http://ubuntuforums.org/showthread.php?t=93420)


mybe this will help you

---

### Post by boondocks on 2010-04-11
> **Iowan said:**
> **iptables** comes to mind. **ufw/gufw** may be another approach to the same thing. (Unfortunately, another area I have yet to learn...)

Currently, ufw is not enabled on this Ubuntu system and I want to keep it that way.
So, is it possible to use gufw so that:
[LIST]
[*]The firewall is NOT enabled.
[*]But this one port is forwarded.
[/LIST]

---

### Post by boondocks on 2010-04-11
> **stilling said:**
> see this

[http://ubuntuforums.org/showthread.php?t=93420](http://ubuntuforums.org/showthread.php?t=93420)


mybe this will help you
I am looking at it.

While I was waiting for responses to this post, I found:
[http://shahidz.com/iptables-port-forwarding-on-ubuntu/](http://shahidz.com/iptables-port-forwarding-on-ubuntu/)

Looks more like what I need.
Right?

---

### Post by stilling on 2010-04-11
you can try this i`m not relly sure about it but

sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.1.23 --dport 19340 -j DNAT --to 192.168.7.15:19340
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.7.15 --dport 19340 -j ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward

test and if that is ok 

sudo gedit /etc/sysctl.conf
find net.ipv4.ip_forward = 1 remove the # that is placed in front
and add the 2 lines with iptables in /etc/rc.local before exit 0


hope this helps

---

### Post by boondocks on 2010-04-11
> **stilling said:**
> you can try this i`m not relly sure about it but

sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.1.23 --dport 19340 -j DNAT --to 192.168.7.15:19340
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.7.15 --dport 19340 -j ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward

test and if that is ok 

sudo gedit /etc/sysctl.conf
find net.ipv4.ip_forward = 1 remove the # that is placed in front
and add the 2 lines with iptables in /etc/rc.local before exit 0


hope this helps
To confirm - this will ensure that all requests will port forwarded (not just mine), correct?

---

### Post by stilling on 2010-04-11
that forwards from eth0 ip to eth1 ip that port

---

### Post by boondocks on 2010-04-11
I need to do the same thing on another Ubuntu system but instead of eth0 and eth1
we have eth0 and TUN virtual network device

Will the same script work?
(Since your script mentions eth0 but not eth1.)

---

### Post by stilling on 2010-04-11
now you know how to do it the problemis that TUN virtual network device must have a name or a ip something like eth1 .... if you understand

---

### Post by boondocks on 2010-04-11
Yes, the TUN virtual network device does have a IP address 192.168.42.7

---

### Post by stilling on 2010-04-12
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.1.23 --dport 19340 -j DNAT --to 192.168.42.7:19340
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.42.7 --dport 19340 -j ACCEPT

and to start after restart add the linest in /etc/rc.local

---

