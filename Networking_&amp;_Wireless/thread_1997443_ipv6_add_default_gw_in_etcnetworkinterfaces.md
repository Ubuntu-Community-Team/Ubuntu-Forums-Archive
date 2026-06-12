---
title: "ipv6: add default gw in /etc/network/interfaces ?"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by sanderj on 2012-06-05
Hi,

My IPv6 is working, after a manual "sudo ip -6 route add default via fe80::21e:13ff:fef9:af0 dev eth0".

I want it to work automatically, also after a reboot. I guess that means I have to add a command to  /etc/network/interfaces. I tried a few different formats, but none work: nothing afters in my "ip -6 route show".

So: what is the correct format?


things tried:

iface eth0 inet6 static
 gateway fe80::21e:13ff:fef9:af0


and

  up route add default gw fe80::1

---

### Post by ratcheer on 2012-06-05
I don't recall having to do anything like that. IPv6 just works, for me. Maybe I had to change a firewall setting, but nothing in the routing.

However, my IPv6 is controlled at my router, not by Ubuntu. Ubuntu just receives the router advertisement and uses it. Maybe that is the difference.

Tim

---

### Post by sanderj on 2012-06-05
> **ratcheer said:**
> I don't recall having to do anything like that. IPv6 just works, for me. Maybe I had to change a firewall setting, but nothing in the routing.

However, my IPv6 is controlled at my router, not by Ubuntu. Ubuntu just receives the router advertisement and uses it. Maybe that is the difference.

Tim

Yep, that's true for the IPv6 at home. And it was true for the IPv6 on my VPS. However, the VPS provider apparently has some problem, and I need to add the route-add command. Therefor my question.

---

### Post by papibe on 2012-06-05
Have you tried putting the ip command in your interfaces file?

```
iface eth0 inet6 static
    ...
    up ip -6 route add default via fe80::21e:13ff:fef9:af0 dev eth0
    ...
```

Regards.

---

### Post by sanderj on 2012-06-05
> **papibe said:**
> Have you tried putting the ip command in your interfaces file?

```
iface eth0 inet6 static
    ...
    up ip -6 route add default via fe80::21e:13ff:fef9:af0 dev eth0
    ...
```

Regards.


That results in this error:

```
sander@R540:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet6 static
    up ip -6 route add default via fe80::21e:13ff:fef9:af0 dev eth0


sander@R540:~$ 
sander@R540:~$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting
sander@R540:~$

```

:-(

---

### Post by papibe on 2012-06-05
For an static entry to work you would need also the fields 'address', 'netmask', and 'gateway'. Check [this]("http://www.cyberciti.biz/faq/ubuntu-ipv6-networking-configuration/") example.

Do you have that information to set it up?

Regards.

---

### Post by sanderj on 2012-06-05
> **papibe said:**
> For an static entry to work you would need also the fields 'address', 'netmask', and 'gateway'. Check [this]("http://www.cyberciti.biz/faq/ubuntu-ipv6-networking-configuration/") example.

Do you have that information to set it up?

Regards.

I changed /etc/network/interfaces to:

```
auto lo
iface lo inet loopback

### Start IPV6 static configuration
iface eth0 inet6 static
pre-up modprobe ipv6
address 2607:f0d0:2001:000a:0000:0000:0000:0010
netmask 64
gateway 2607:f0d0:2001:000a:0000:0000:0000:0001
### END IPV6 configuration
```

I did a

```

sudo service networking restart

```
and no errors, but nothing had changed in ifconfig or the route table. :-(

Just to be sure I could add anything to eth0, I did a manual:

```
sudo ip addr add 1.2.3.4 dev eth0
sudo ip -6 addr add 2001::4 dev eth0

```

and that worked.

So the suggested method does not work, alas

I use 12.04. Are the config table the same as in earlier Ubuntu versions? FWIW: /etc/network/interfaces is (was) almost empty ...

Your help is very appreciated

---

### Post by papibe on 2012-06-05
The link on my previous post had the intention to show you an example of the structure of an static IPv6 entry. However, you should not use those address, use the one you are going to use (the ones on post #1).

I also noticed that you assign an IPv4 address to eth0 after boot. You can define both IPv4 and IPv6 in the 'interfaces' file, check this other [example]("http://codingmyself.wordpress.com/2010/03/26/how-to-set-the-static-ipv4-and-ipv6-address-in-ubuntu/").

I hope that helps.
Regards.

---

### Post by sanderj on 2012-06-05
> **papibe said:**
> The link on my previous post had the intention to show you an example of the structure of an static IPv6 entry. However, you should not use those address, use the one you are going to use (the ones on post #1).

I also noticed that you assign an IPv4 address to eth0 after boot. You can define both IPv4 and IPv6 in the 'interfaces' file, check this other [example]("http://codingmyself.wordpress.com/2010/03/26/how-to-set-the-static-ipv4-and-ipv6-address-in-ubuntu/").

I hope that helps.
Regards.

Even with the 'wrong' address, they should appear in the ifconfig as shown by my 'manual' example: the fake IPv4 and IPv6 address appear in the ifconfig. But, alas, the example in your previous post and in your last post do not result in anything in ifconfig. Sorry.

---

### Post by hawkmage on 2012-06-05
This is basically what I have in my interfaces file for my IPv6 config on eth0:
```
iface eth0 inet6 static
     address 2001:1234:1234::40
     netmask 64
     up ip -6 route add default via 2001:1234:1234::1
     down ip -6 route del default via 2001:1234:1234::1
```This is working for me without the "dev eth0"

---

### Post by sanderj on 2012-06-07
> **hawkmage said:**
> This is basically what I have in my interfaces file for my IPv6 config on eth0:
```
iface eth0 inet6 static
     address 2001:1234:1234::40
     netmask 64
     up ip -6 route add default via 2001:1234:1234::1
     down ip -6 route del default via 2001:1234:1234::1
```This is working for me without the "dev eth0"

OK, I'll try that out on my machine as soon as I've access to it again. Thanks.

---

