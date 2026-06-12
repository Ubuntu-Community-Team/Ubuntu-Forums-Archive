---
title: "Native IPv6 Howto"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2011-02-07
Hi,

On my setup, I have something that looks like this..

-- ISP  ---> Ubuntu Router/Gateway/Firewall (eth0 = ISP, eth1 = private net) ---> Home Network

Pretty basic setup.  My ISP has given me a /64 IPv6 address space along with my usual IPv4 space.  I can configure the router/gateway/firewall to use IPv4 and IPv6, and I can ping external ipv6 space, but for whatever reason, I can't get it to be used on my "Home Network" machines.  I've tried to configure radvd and set the ipv6 forwarding with sysctl, but no luck.  

Does anybody out there know of a good (and easy) howto to get this working?  

Thanks!

---

### Post by herdwick on 2011-02-08
I'm currently reading [http://www.debian-administration.org/article/Running_IPv6_in_practice](http://www.debian-administration.org/article/Running_IPv6_in_practice)

apart from the tunnelling bit which you won't need there might be some useful stuff there.

---

### Post by wiz561 on 2011-02-09
thanks, i'll check it out.

It seems like the majority of tutorials out there are for tunneling.  I would imagine that, within time, there will be some guidance on a dual-stack setup.  From what I read, comcast is doing a trial with this exact setup.

---

### Post by annoyingrob on 2011-02-10
Interestingly, IPv4 and IPv6 routing are handled separately under linux. You will need to set up ip6tables to forward IPv6 packets between the two interfaces. You will also need to use radvd to tell machines which prefix and gateway to use, but it sounds like you've already done that.

For example, here's my /etc/ip6tables.up.rules

I have ssh and http open to my router, and then I have some rules to only allow IPv6 traffic OUT that has my prefix, as well as allowing incoming pings, and established connections. The forward ones are the important ones. They tell my routing machine that it needs to forward packets from the external network to my internal network. Note: There is NO NAT on my IPv6 network.
 
```


*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
#Allow internal traffic
-A INPUT -s 2001:470:XXXX:XXXX::/64 -j ACCEPT

#Allow SSH and WWW from outside
-A INPUT -i he-ipv6 -p tcp -m multiport --dports 22,80 -j ACCEPT
-A INPUT -p icmpv6 -j ACCEPT

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT

#Allow outgoing connections from network
-A FORWARD -s 2001:470:XXXX:XXXX::/64 -j ACCEPT

#Allow internal machines to be pinged
-A FORWARD -p icmpv6 -j ACCEPT 

#Allow non-reserved connections into network
#-A FORWARD -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state RELATED,ESTABLISHED -j ACCEPT 

COMMIT
# Completed on Sat Dec 18 13:07:00 2010

```

Edit: Just re-read your post that mentioned that you have set up forwarding in IPv6 already. Are you SURE it set up IPv6 forwarding, and not just IPv4?

---

### Post by HiddenFly on 2011-03-15
I'm having this exact same problem - Did you get it solved?

---

