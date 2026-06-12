---
title: "unable to access webserver via ipv6 address"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by tomski on 2009-08-11
Hi there,

i hope you guy's can help me, my tunnel is all up & working & all my nodes within my LAN are getting a ipv6 address i have 1 problem

one of my nodes 2001:470:1f09:2fc::a/64 which is a Ubuntu Jaunty box (headless) runs apache/mysql/php/cacti & ntop just to give me an idea of what is occurring on my lil lan

problem is i am unable to access cacti/apache or ntop from the ipv6 address above now i would love to be able to have this server accessable via ipv4 & 6 can any of you give me some guidelines on getting this working as i have tried to tell it to listen on the above address on port 80 as well as ::1 (localhost) but it will not play ball

have i made a real dumb error and for got something simple (which it generally is with linux lol) 

i might add that my gateway/router/firewall is m0n0wall and this server is not in a DMZ or seperate LAN 

i use ssh & webmin & occasionaly vnc to admin my headl,ess webserver & eventually i want to be able to provide a ipv6 virtual host on this server but unless i can get the thing to be accessable via both im at a loss

config files are avaliable upon request & will be pre-sanitized for sanity!!

thnx in advance to those who help

---

### Post by sanderj on 2009-08-11
Just checking: you have services running on this machine, but you can't access them over IPv6, right?

If so, I would start by turning of the firewall temporarily and see if you can access the service(s) then.


FWIW: I can ping6 your system.

> ubuntu@ubuntu:~$ ping6 2001:470:1f09:2fc::a
PING 2001:470:1f09:2fc::a(2001:470:1f09:2fc::a) 56 data bytes
64 bytes from 2001:470:1f09:2fc::a: icmp_seq=1 ttl=56 time=329 ms
64 bytes from 2001:470:1f09:2fc::a: icmp_seq=2 ttl=56 time=151 ms
^C
--- 2001:470:1f09:2fc::a ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 151.504/240.282/329.061/88.779 ms
ubuntu@ubuntu:~$ 

However, nmap does not show any services. And I can't access anything via ssh nor http on your system.

---

### Post by gombadi on 2009-08-11
> 
problem is i am unable to access cacti/apache or ntop from the ipv6 address above


This link may be interesting - [http://blogs.turmzimmer.net/2009/08/10#squeeze-3](http://blogs.turmzimmer.net/2009/08/10#squeeze-3)

You have to define what people mean by ipv6 ready? I have ipv6 capable servers running but not all services on them are able to use ipv6.

---

### Post by tomski on 2009-08-12
Thnx for your feed back gent's

> **gombadi said:**
> This link may be interesting - [http://blogs.turmzimmer.net/2009/08/10#squeeze-3](http://blogs.turmzimmer.net/2009/08/10#squeeze-3)

You have to define what people mean by ipv6 ready? I have ipv6 capable servers running but not all services on them are able to use ipv6.

HMMMMMM very interesting indeed

> **sanderj said:**
> Just checking: you have services running on this machine, but you can't access them over IPv6, right?

If so, I would start by turning of the firewall temporarily and see if you can access the service(s) then.


FWIW: I can ping6 your system.



However, nmap does not show any services. And I can't access anything via ssh nor http on your system.

:D thats probably because you are hitting my m0n0wall box first & i don't want to allow ipv6 as a huge backdoor in lol so i only enabled the icmp when i can get to port 80 on that IP from within my 6LAN i'll then sort out a website which will only be visible via IPv6

it already has DNS:
ip6.tomsbox.co.uk  <<<m0n0wall
serv.tomsbox.co.uk <<<<webserver

---

### Post by tomski on 2009-08-12
bingo 
got it working for internal nodes
now i just gotta get port 80 open in m0n0wall!

FYI
if you intend to use both ipv4 & ipv6 on a apache install within ubuntu ONLY use:

Listen [::]:80

within the file:

/etc/apache2/ports.conf

we use this because [::] = any ip on any stack both ipv6 & 4
and if you have Listen 80 apache will see that as any ip4 address BUT if you have both Listen directives present apache will not start as it will get confused & report both sockets as in use

to have the server configured with multiple virtual hosts using different ip types just use the 'allow' & 'deny' directives within its respective .conf file located in the 'sites-enabled' directoy to configure each as you need :)

when i get m0n0wall working to allow traffic in on ipv6:80 i'll document it here also for others

---

