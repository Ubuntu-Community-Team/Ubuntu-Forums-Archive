---
title: "Exception ip in tinyproxy"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by Zubairinfo on 2011-01-10
Hi Can any one tell me how to add a exception for a particular IP for not to do content filtering in Tinyproxy ?

Thanks in advance.... :D

---

### Post by sj1410 on 2011-01-11
i dont see any such feature in tinyproxy. You need to use dansguardian for extended content filtering.

---

### Post by Zubairinfo on 2011-01-11
Hi, Thanks for the response.

I have configured the content filtering by adding the domains and urls into /etc/filters file which works fine, but issue is that i want to exclude 2 IP of my manager who don't want any filters in his internet browsing and he want to access all the websites..

Suggest me...

Thanks...




> **sj1410 said:**
> i dont see any such feature in tinyproxy. You need to use dansguardian for extended content filtering.

---

### Post by sj1410 on 2011-01-11
tinyproxy wont allow you to do that. but what you can do is dont make any proxy settings in the managers browser and add a iptables masquerading rules based on the managers ip address.

---

### Post by Zubairinfo on 2011-01-11
OK Thanks,

But Iam poor at iptables, can you please help me ?

This is the iptables command i have used for my server, based on this kindly suggest me the iptables command.

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080


Thanks,




> **sj1410 said:**
> tinyproxy wont allow you to do that. but what you can do is dont make any proxy settings in the managers browser and add a iptables masquerading rules based on the managers ip address.

---

### Post by sj1410 on 2011-01-11
oh so you are using a  transparent proxy. than you need to add a redirect rule excluding the source ips.

---

### Post by Zubairinfo on 2011-01-11
Can you please send me the command ....
Its a bit urgent, my manager is behind me about the status...



> **sj1410 said:**
> oh so you are using a  transparent proxy. than you need to add a redirect rule excluding the source ips.

---

### Post by sj1410 on 2011-01-11
```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.2 -p tcp --dport 80 -j REDIRECT --to-port 8080
.
.
.
.
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.10 -p tcp --dport 80 -j REDIRECT --to-port 8080

```

this are the the rules for each ip address of the PCs which you need to redirect to tinyproxy except the managers ip.

hope this works for you. you can also do an inverse entry, but you can do it for only one.

```

iptables -t nat -A PREROUTING -i eth1 ! -s 192.168.0.47 -p tcp --dport 80 -j REDIRECT --to-port 8080

```
in this rule except 0.47 all will be redirected to tinyproxy

good luck

---

### Post by Zubairinfo on 2011-01-21
> **sj1410 said:**
> ```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.2 -p tcp --dport 80 -j REDIRECT --to-port 8080
.
.
.
.
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.10 -p tcp --dport 80 -j REDIRECT --to-port 8080

```this are the the rules for each ip address of the PCs which you need to redirect to tinyproxy except the managers ip.

hope this works for you. you can also do an inverse entry, but you can do it for only one.

```

iptables -t nat -A PREROUTING -i eth1 ! -s 192.168.0.47 -p tcp --dport 80 -j REDIRECT --to-port 8080

```in this rule except 0.47 all will be redirected to tinyproxy

good luck

Hi,

Sorry for the late response, the command above did not work, after this command from 0.47 machine i was not able to access internet either from proxy or without, so simple remove tiny proxy and configured suid, it worked...
Thanks for your support...

Now i have got a new requirment from my boss,
He wants a new network  pool working with the same proxy server and the DHCP, with diffrent IP POOL i.e.. 192.168.1.0/24..
i have configured a new lan card eth2 and made the dhcp to listen to eth2 with the new Ip pool, it works !
But the issue is that users on 192.168.0.0/24 should not be able access the machines from 192.168.1.0/24 network and vise versa...

Is ther a way to restrict this...
Thanks in advance...

---

