---
title: "Ubuntu as Primary NAT Router Questions"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by xtropx on 2012-07-15
Hello. I have successfully tested Ubuntu server as a NAT router, (documented [http://xtropx.blogspot.com/2012/07/best-ubuntu-nat-tutorial.html](http://xtropx.blogspot.com/2012/07/best-ubuntu-nat-tutorial.html)) and I believe I am ready to substitute my current router with Ubuntu. I am also planning on using this as a DNS server using BIND9, an endpoint for a HE.net IPv6 tunnel. (Following: [http://davecoyle.com/documents/ubuntu-ipv6-he-tunnel.html](http://davecoyle.com/documents/ubuntu-ipv6-he-tunnel.html))

However, I am wondering about the potential security implications of this, and what I need to worry about exposing Ubuntu server to the internet as my main router. Perhaps someone can enlighten me or point me in the right direction. I just want one box to do everything primarily due to lack of funds, power consumption and heat production. I might even run SAMBA or APACHE on this box as well, but I can imagine that's an even worse idea. What do you guys think?

---

### Post by Kirk Schnable on 2012-07-15
Just make sure your firewall is well crafted, and you'll be fine.  I have been running a Ubuntu router as the gateway for my house for several years.

If you are going to run services on it, like Samba and Apache, be mindful of which interface they're listening on so you don't accidentally have your personal files accessible to the world.

The best policy for doing a router like this is to tell iptables:
```
iptables -P INPUT DROP
```

Then create exceptions for ports you want to allow in.

I could furnish you with a copy of my "black hole router" iptables commands if you like.

Kirk

---

### Post by Cheesehead on 2012-07-15
If this is a testing or hobby environment, then you can any services you want on your gateway/router/server. The answer for a production environment would be different, of course.

I did something similar about a year ago on my home hobby LAN.
Most days I get about 2000 probes on my router, none have gotten through yet. None have even figured out my ssh port yet.

Document your firewall rules well. The firewall protects both your server and LAN, and you will return to those rules every time you add or remove a new service.

Security should not be a problem as long as you take the basic precautions:
- SSH: Use a different port than 22. Use keys instead of passwords. Disable root login. Use some kind of secondary protection (fail2ban, fwknopd, login notifications, etc)
- Regularly test your firewall with a port scanner (like [Shields Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2")) so you can see your system from an attacker's perspective.
- Backups, backups, backups: Restoring is much faster and easier than rebuilding. Keep nothing on the server that is sensitive, or that you would be sad to lose.

Final precaution is to keep the old router handy in case of a crisis or breakage...

---

### Post by Kirk Schnable on 2012-07-15
> **Cheesehead said:**
> If this is a testing or hobby environment, then you can any services you want on your gateway/router/server. The answer for a production environment would be different, of course.

May I remind you, most datacenter hosted servers don't have any firewall other than the iptables on the box?

As long as you are confident in your firewall, I'd be comfortable running services on a production router.  But that's just me.  I'd think twice about it because of the possibility of performance degradation, but that's about it.  I don't see why production servers in datacenters should be any different than production routers.

Kirk

---

### Post by xtropx on 2012-07-16
Thanks for the great information. I think I will go ahead and try this. If you can survive 2000 probes a day cheesehead it would appear it can safely be done. Should be a good project.

> Then create exceptions for ports you want to allow in.

I could furnish you with a copy of my "black hole router" iptables commands if you like.By exceptions we are talking just port forwarding? I would be most appreciative of a copy; I find that examples of the way other people successfully configure things really helps to get my head around it.

---

### Post by Kirk Schnable on 2012-07-22
Sorry for taking so long to get back to you, it's been really busy around here lately.  Thanks for the PM reminding me to follow up on this.

iptables can be saved and everything, but I usually just run a script in my root crontab @reboot to set the rules.  That makes it easy to design a script that can be re-run at any time to apply the new set of rules.

Now, I will try to guide you through setting this up the first time.  I assume you already have NAT working.  For the purpose of this guide, my eth0 interface is LAN, eth1 is Internet.  

The first part of your iptables script should reset the rules to default so as to allow the script to be re-run to apply rules while the server is on.

```
# Clear Old Rules
/sbin/iptables --flush
/sbin/iptables --table nat --flush
/sbin/iptables --delete-chain
/sbin/iptables --table nat --delete-chain
/sbin/iptables -X
```

Now you want to set your Default policies.  This is what I set.

```
# Setup Default Firewall Rules
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -P INPUT DROP
```

The easiest way to make sure that your black-hole INPUT chain doesn't break your network, is to whitelist that interface.  You'll also need to whitelist lo (loopback) in order to prevent problems with software on the server.  Don't whitelist any other interfaces unless they're trusted (VPN, etc) as this defeats the purpose of a firewall.

```
# Whitelisted Interfaces
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -i eth0 -j ACCEPT
```

I always throw this in there, so my NAT can be setup when the iptables script is run.  You may already be doing this, or something similar, somewhere else.  If so, don't copy my code or you might break your current NAT setup.  

If you have a current NAT setup which works, the only part you'll want to grab from this is the "Allow Established Connections" one. Otherwise you'll have all sorts of weird problems from setting INPUT to DROP.

```
# Enable Packet Forwarding
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# Network Address Translation
/sbin/iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
/sbin/iptables --append FORWARD --in-interface eth0 -j ACCEPT

# Allow Input From Established Connections
/sbin/iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
```.

I have a Squid caching proxy on this gateway, so I also threw this in there.

```
# Squid Caching Proxy
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 13337
```

Now when you want to setup port forwards, they can be done in this style: (10.1.1.1 is one of my inside servers).
```
# Port Forwarding Inside Network
#/ HTTP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 10.1.1.1:80
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 8080 -j DNAT --to 10.1.1.1:8080
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 443 -j DNAT --to 10.1.1.1:443
```

If you want to open a port to your router\gateway itself, you can use a syntax like this:
```
/sbin/iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

If you want to allow incoming ICMP Pings (questionable decision, but I do for troubleshooting), tack this on somewhere:

```
#/ Allow ICMP Pings
/sbin/iptables -A INPUT -p ICMP -j ACCEPT
```

That should be a good start for you.  If you have any questions, please don't hesitate to ask.

Kirk

---

### Post by Cheesehead on 2012-07-22
I quite like that ruleset.
Great explanation, too.

---

### Post by Doug S on 2012-07-23
I would highly recommend another rule at the start of the forward chain:```
/sbin/iptables -A FORWARD -i $INTIF -p tcp -m state --state INVALID -j DROP
```where $INTIF = the internal interface.
DROP can be changed to REJECT, if you prefer.
This rule helps to prevent un_NAT'd packets from escaping to internet. The netfilter stuff does not know what to do with an invalid packet, so passes it untranslated.
There was a case just few weeks ago (see reference below) where someone got in trouble because of spewing unroutable packets.
 
Reference: [http://bugzilla.netfilter.org/show_bug.cgi?id=693](http://bugzilla.netfilter.org/show_bug.cgi?id=693)

---

