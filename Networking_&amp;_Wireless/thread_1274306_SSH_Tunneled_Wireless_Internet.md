---
title: "SSH Tunneled Wireless Internet"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by AN@S on 2009-09-24
Hi,

I've been looking for an answer for this question for a while but didn't find the answer yet. I'll try to describe my question in a very clear and simple way:

I have a dedicated server in a data center, and I create an SSH tunnel to my server from my laptop as follows:

ssh -D 9999 user@host

Then I set up the SOCKS proxy on my laptop with: 
localhost:9999

This works as expected and I enjoy secure surfing, and I can browse websites that are blocked by government (Yes they do censorship the Internet in my country).

OK, now the question is: I have a wireless 3com ADSL router at office, is there some way to let everyone at office benefit from the tunneling through the wireless network without having to open the tunnel from each one's PC to the server? In other words, I want to do something between my laptop and the router, so everyone at office connected to the network will already get an SSH tunneled Internet connection.

I hope my question is clear enough, and any help is appreciated.

Thanks :KS

---

### Post by sedawk on 2009-09-24
A simple solution would be to install a web proxy (like privoxy)
on your laptop so users select that proxy in their browser.

Another (more powerful) solution might be to install
OpenVPN for a point-to-point connection from your
laptop to the server in the data center which tunnels
all traffic in that VPN via the ssh-tunnel.
With IP-forwarding enabled on both ends and
proper gateway settings in the office all 
external traffic will travel via
the (encrypted) vpn tunnel.
(You might also need a DNS server or forwarder so
 people can use addresses like in
 "ssh freeshell.example.net"
 Keep in mind that using a local DNS server (from the government
 or your provider) doesn't tell them which web pages you view,
 but which servers you are trying to connect.)

---

### Post by Lars Noodén on 2009-09-24
You'll want to look at masquerading (aka NAT) in IPTables and look at bridging.  Probably it's a good idea to set up that internal wireless network as IPv6 with IPSec.  

Maybe setting up a proxy/cache like squid might speed up responses in addition to reducing incoming traffic.  

Other tools like dnsmasq might come in handy.

---

### Post by superprash2003 on 2009-09-24
check out SQUID for proxy

---

### Post by e24ohm on 2009-09-24
> **superprash2003 said:**
> check out SQUID for proxyI second SQUID in this deployment. SQUID is very complet and has a nice set of features.

thanks.

---

### Post by Bucky Ball on 2009-09-24
You people are amazing. I'm so happy to be part of this community!

(sorry to jump in but just had to say it :))

---

### Post by AN@S on 2009-09-25
Thank you all for help, as I see there are some options to start playing with, I liked them specially the Squid option which I think I'll start with. :popcorn:

---

