---
title: "Restricting VPN over virtual interface to one application?"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by syphax on 2012-04-18
Ubuntu Server 11.10 Oneiric, latest updates
AMD E-350 CPU/Chipset; single gigabit NIC

I do my best to Google things before asking but I have an unusual scenario. I'm not sure if this is even possible but if so your assistance is appreciated:

So what I would like to do is set up a VPN that should be considered untrusted and restrict it to communicating with a single process/application/whatever. This app can bind to a specific interface. I am comfortable with creating basic VPNs and virtual NICs (i.e., eth0:1) but I'm not sure how to do this setup securely. I would prefer to stay away from running the process in a hypervisor/VPS to save resources but it may come down to that eventually.

The remote end of the VPN should be considered untrusted, really the VPN is just being used as a tunnel - I would use an SSH tunnel but it is not available for this scenario. So what I would like to do is bind the VPN to eth0:1, bind the app to the same, and restrict all other communication on this virtual port, e.g. disallow access to Samba share, SMTP, WWW, etc. I could go the difficult route and set up a firewall but the rules would be a chore to maintain and it wouldn't provide the level of "hard" security I'm looking for.

I'm thinking there must be an easier way, maybe with VPN routing? I don't have much experience with that. Am I going about this the wrong way? Unfortunately the remote site must be OpenVPN and no other tunneling service is available. Any ideas? Thank you.

---

### Post by SeijiSensei on 2012-04-18
> **syphax said:**
> The remote end of the VPN should be considered untrusted, really the VPN is just being used as a tunnel

I'm not sure why you think it it should be considered "untrusted" unless you want to access the application from multiple arbitrary clients.  If you're always connecting from a known client, use a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") that exists only on the machines at both ends of the tunnel.

Beyond that you can block all other types of connections with iptables.  Suppose the server has an OpenVPN connection assigned to the tun0 interface, and your application listens on port 12345.  First, I'd try and configure the application to bind solely to the IP address on tun0.  Then for extra protection I'd add the following to the server's iptables ruleset:

```

iptables -A INPUT -i tun0 -p tcp --dport 12345 -j ACCEPT
iptables -A INPUT -i tun0 -j REJECT

```

(Replace "-p tcp" with "-p udp" if the application uses UDP, or add another rule with "-p udp" if it uses both.)

I'm not sure why you think a firewall would be a "chore," but if the machine is a server and visible over the public Internet, a firewall is de rigeur.  Even if you don't want to install a complete set of firewalling rules, you could simply run these commands from /etc/rc.local at boot to protect the application.

---

### Post by syphax on 2012-04-18
Connecting from multiple arbitrary clients is indeed the aim. The server sits behind a m0n0wall box and until now only allowed 10.x.x.x connections.

> **SeijiSensei said:**
> 
Beyond that you can block all other types of connections with iptables...


This and the following solution is more or less what I was looking for. I wasn't sure if it would be safe to merely place a "reject" on tun0 and call it a day but then again I suppose it's no less safe than being behind any other firewall. I call it a chore only because I thought maybe I would have to do more than that, but that wouldn't be any trouble at all.

This is probably what I will implement, thanks for your time.

Of course other suggestions are welcome but I have to accept at some point that arbitrary clients are hitting this particular server... :neutral: Most likely I'm being unrealistically cautious but it's just a personal preference.

---

