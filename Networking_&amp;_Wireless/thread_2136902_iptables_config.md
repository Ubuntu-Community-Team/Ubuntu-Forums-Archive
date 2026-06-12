---
title: "iptables config"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by Capslock118 on 2013-04-19
I have a headless server at home and I'd like to tighten it's firewall so that only connections through the vpn or connections to/from the local network are allowed. I've read through a handful of iptables documentation, and [read this one]("http://bodhizazen.net/Tutorials/iptables") twice. Still, the server being headless and all, I'd like an extra set of eyes to be sure that when I put this configuration in I don't lose SSH access.

My goal is to have the host machines WAN access go through the VPN only, so if the VPN is down there is no WAN communication with the host machine. All local connections are allowed. I've put in comments to outline what my intentions for each set were, in case I wrote it so backwards that it doesn't make any sense.

```

#Accept all TUN connections (tun is the virtual adaptor for VPN)
iptbales -A OUTPUT -o tun0 -j ACCEPT

#Allow initialization of VPN
iptables -A OUTPUT -d VPN_IP_ADDRESS --dport VPN_IP_PORT -j ACCEPT

#Allow all local network communication
iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT
iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT

#Drop everything else
iptbales -A OUTPUT -j DROP
iptbales -A INPUT -j DROP

```


Thank you for your review.

---

### Post by SeijiSensei on 2013-04-19
Is FORWARDing allowed by default?  If not, packets cannot move from one interface to another.  You might want to set this explicitly using "policies" for all three rulesets at the top:

```

/sbin/iptables -P INPUT DENY
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -P OUTPUT ACCEPT

```

If you want to ensure that you can connect over the local network even if there is a problem with the VPN rule, then put the VPN rules below the rules for 192.168.0.0/24.  The rules are evaluated sequentially so even if there were a problem in the VPN rule, you'd still have network access.

iptables is misspelt in the last two rules.

You need to have net.ipv4.ip_forward in /etc/sysctl.conf set to true as well in order to forward packets between interfaces.  See the instructions in that file.

---

### Post by Capslock118 on 2013-04-22
Thanks for your review. I'm not sure if forwarding policy is set to ACCEPT but I like taking the explicit approach anyways :)

Three things.

1) After your comments I am wondering if it makes more sense (semantically and practically) to have a INPUT and OUTPUT policy to drop by default then open as needed rather than dropping at the end.

2) Turns out I connect to a different IP address when connecting to my VPN provider each time I re-establish a connection so I don't actually know the IP address ahead of time. I'm thinking a general rule to accept at the port level would be best.

3) I'm not sure, but I think I had a flaw. Do I would want to allow INPUT to my vpn port as well so data can come back in? In other words does INPUT apply to established connections?


Here is a revised layout:
```
#Set default policies to reject all INPUT and OUTPUT unless explicitly allowed
#Allow forwarding to/from physical interface with virtual one (eth0 to/from tun0)
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD ACCEPT

#Allow all local traffic
iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT
iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT

#Accept all TUN connections (tun is the virtual adaptor for VPN)
iptables -A OUTPUT -o tun+ -j ACCEPT

#Is this needed? Or would this effectively make my iptables worthless by allowing all incoming connections? (since eth0 would be forwarded to tun0)?
iptables -A INPUT -i tun+ -j ACCEPT

#Allow initialization of VPN
iptables -A OUTPUT -p udp --dport 1194 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1194 -j ACCEPT
```

---

### Post by SeijiSensei on 2013-04-23
First, you are missing an important rule which governs traffic sent in reply to TCP requests.  As it stands now, you could send a request to a website but not see the page.  In addition, if you adopt INPUT DROP as the policy, you're going to need more rules.  Traffic originating on the localhost (127.0.0.1) interface, for instance, will be blocked.  You'll also be blocking ICMP traffic so pings won't work.  To fix these, add these three lines at the top of the ruleset, right after the policies:

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A INPUT -p icmp -j ACCEPT

```

You can either drop by default or drop by rule.  If you want to log all the nonconforming traffic, you are better off with ACCEPT as the policy and dropping by rule.  Use these rules at the end of the ruleset:

```

/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j DROP

```

And, yes, you want both an INPUT and an OUTPUT rule for the tun interfaces.  I don't know what you mean by eth0 being forwarded to tun0.  That doesn't happen by default, and frankly, I don't know why you would want to do that.

---

### Post by Capslock118 on 2013-04-23
Thanks for your help!

I pretty much understand everything you have said. 

The only confusing part (which in turn I have confused you) is this:
>  I don't know what you mean by eth0 being forwarded to tun0. That doesn't happen by default, and frankly, I don't know why you would want to do that.

Basically my script comment was based on your previous statement:
> Is FORWARDing allowed by default? If not, packets cannot move from one interface to another. You might want to set this explicitly using "policies" for all three rulesets at the top:

I took this to mean that the FORWARD chain was required because in the case of a VPN, it represented moving communication from the physical device (eth0) to the virtual device (tun0) and that this was required in order for communication to occur within tun0. In other words, if eth0 was locked down by iptables, then tun0 would never see any communication.

Does the FORWARD chain represent something else?

---

### Post by SeijiSensei on 2013-04-24
I need a bit of clarification.  Does this machine have multiple ethernet adapters, or just the one connected to the Internet?  If it just has one, and is not acting as a router, then FORWARDing is less important.  

If this box is acting as a router, with another connection to a LAN "behind" it, then the LAN clients would not be able to reach out past the router if FORWARDing is disabled.  

If net.ipv4.ip_forward is not enabled in /etc/sysctl.conf, which is the default for security reasons, you cannot forward packets across interfaces at all, so the FORWARD rules are irrelevant.

---

### Post by Capslock118 on 2013-04-24
ok no it's not acting as a router.

one ethernet adapter (eth0) and one openvpn adapter (tun0).

That said I'm not sure now if forwarding is required or not.

---

### Post by SeijiSensei on 2013-04-25
Probably not. The simplest way to find out is experimentation.

---

### Post by Capslock118 on 2013-05-03
Hi SeijiSensei,

Just to update you I believe everything I wanted out of iptables is setup and working.

This is is what has so far been working for me:
```


#Set default policies to drop all other communication
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
 
#Allow loopback (internal communication)
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT -o lo -j ACCEPT

#Allow all local traffic
sudo iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT
sudo iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT

#Allow VPN establishment
sudo iptables -A OUTPUT -p udp --dport 1194 -j ACCEPT
sudo iptables -A INPUT -p udp --sport 1194 -j ACCEPT

#Accept all TUN connections (tun = VPN tunnel)
sudo iptables -A OUTPUT -o tun+ -j ACCEPT
sudo iptables -A INPUT -i tun+ -j ACCEPT
```


Thanks for all of your help with this.

---

