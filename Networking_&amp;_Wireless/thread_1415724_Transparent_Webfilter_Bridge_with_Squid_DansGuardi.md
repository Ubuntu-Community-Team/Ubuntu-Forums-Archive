---
title: "Transparent Webfilter Bridge with Squid DansGuardian Problems"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by topanaris on 2010-02-25
Question trying to setup a transparent filter bridge with Dans Guardian ver 2.9.9.7, Squid 2.7 Stable 3 with the help of some iptables and ebtables statements. So Basically i have configured the ubuntu 9.04 machine as a bridge with the following commands 

ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig br0 x.x.x.x netmask 255.255.255.0 up
route add default gw x.x.x.x dev br0

I have only made the following change to the Squid Config

http_port 3128 transparent
http_access allow localnet
http_access allow localhost
acl localnet src (my network address/24)
everything else unchanged

The changes made to dansguardian are are follow

#UNCONFIGURED

everything else remained as default.

And the follow iptables and ebtables commands
#ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 \
--ip-destination-port 80 -j redirect --redirect-target ACCEPT

# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
-j REDIRECT --to-port 3128

Now for the problem if i manually configure a client browser the filter works fine however when i remove the proxy settings squid still works (as i did a # tail -f /var/log/squid/access.log and squid was processing web traffic) but then dansguardian doesnt work. I am somewhat new to this but i am stumped any help would be highly appreciated

---

### Post by topanaris on 2010-02-25
and as usual with my linux queries - no responses do i smell bad or something? *sniffs armpits*

---

### Post by topanaris on 2010-02-26
Cmon guys i know this isnt impossible somebody please just give me something - anything

---

### Post by toosneaky on 2010-03-15
simple - change

# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
-j REDIRECT --to-port 3128

to

# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
-j REDIRECT --to-port **_*8080*_**

it works like this

(80) external -> (8080) dansguardian > (3128) squid -> (80) internal

does that help?

---

### Post by topanaris on 2010-04-07
Yup it worked like a charm thanks a mill

---

### Post by wizard210 on 2011-03-16
> **topanaris said:**
> Question trying to setup a transparent filter bridge with Dans Guardian ver 2.9.9.7, Squid 2.7 Stable 3 with the help of some iptables and ebtables statements. So Basically i have configured the ubuntu 9.04 machine as a bridge with the following commands 

ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig br0 x.x.x.x netmask 255.255.255.0 up
route add default gw x.x.x.x dev br0

I have only made the following change to the Squid Config

http_port 3128 transparent
http_access allow localnet
http_access allow localhost
acl localnet src (my network address/24)
everything else unchanged

The changes made to dansguardian are are follow

#UNCONFIGURED

everything else remained as default.

And the follow iptables and ebtables commands
#ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 \
--ip-destination-port 80 -j redirect --redirect-target ACCEPT

# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
-j REDIRECT --to-port 3128

Now for the problem if i manually configure a client browser the filter works fine however when i remove the proxy settings squid still works (as i did a # tail -f /var/log/squid/access.log and squid was processing web traffic) but then dansguardian doesnt work. I am somewhat new to this but i am stumped any help would be highly appreciated

this is exaclty what i'm trying to do. Did you following a how to? If so can you link to it. I'm a linux newbie.

---

