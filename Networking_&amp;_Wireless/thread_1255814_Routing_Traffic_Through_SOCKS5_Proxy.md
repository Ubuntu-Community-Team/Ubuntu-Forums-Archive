---
title: "Routing Traffic Through SOCKS5 Proxy"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by computer13137 on 2009-09-01
Maybe this has been done a thousand times, and I just missed all the tutorials... but I've been playing around with it tonight, and I haven't had very much success.  It looks like it's definitely possible, but I haven't found a foolproof way to do it yet.

Here's what I want to do.

I want to have a Windows virtual machine and a Linux virtual machine on a private host only network.  I already have this setup and have the Windows traffic routing through the Linux machine with some simple IPtables rules that I use on my own LAN.

What I'd like to do is block everything but port 80 and 53 on the Windows box, which I can do easily.  What I'd like to do is create some IPTables rules to route the traffic on port 80 to the SOCKS proxy that I created with a Dynamic SSH tunnel. 

This would mean that all web traffic on port 80 is automatically sent through the proxy.

I'm assuming it's possible, but I can't figure out exactly what IPtables rules I need to look at, or whether I need some kind of third party software to assist.

Any of you done this before, or have any ideas?

Thanks!

---

### Post by fwre01 on 2009-09-15
Where is the SOCKS proxy? could you put together an ascii diagram?

Something like this perhaps?

```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

```

---

### Post by computer13137 on 2009-09-16
The SOCKS proxy would be on the router, on whatever port (8080 is fine) on localhost.

The same system I'd be using as my "router" would also be connected to an SSH session with a dynamic tunnel open on port 8080.

eth0 is my Internet interface, eth1 is my LAN interface.

I want all traffic coming in through eth1 on ports 80, 21, and any others I specify, to be routed through this SOCKS proxy on 127.0.0.1:8080.

I tried revising what you gave me to something like this...
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
```I ended up not being able to access the web at all... what do you suppose I broke with that?

Thanks!

---

### Post by fwre01 on 2009-09-16
Ive tried using the socket after the REDIRECT action and it spits it out as a syntax mistake.

Ive seen a lot of people using the DNAT instead of REDIRECT action. To me this doesnt make sense, but ive seen this example being used...

```
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to x.x.x.x:8080
```

(using the local address and port number that the proxy listens on after the --to flag, (although i wouldnt use the 127.0.0.1 address))

Like i say, this doesnt make sense to me unless before the server DNAT's the packets it actually remembers the original destination.

But try it, and see how you get on...

---

### Post by fwre01 on 2009-09-16
Sorry....to also answer your question. The iptables rule was then changing all your web requests going out to the internet to have a DPORT of 8080 (which the majority of webservers dont reply on)

---

### Post by computer13137 on 2009-09-18
> **fwre01 said:**
>  ```
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to x.x.x.x:8080
```

I gave that a go.  What ended up happening was the browser would load a blank page and say Done no matter what website I tried to visit.  I'm guessing there's either some kind of loss of information - the packet forgot where it was going - or there's a protocol mismatch, and some third party software needs to be in the middle.

Would it be any different if I used Squid?  I believe Squid can proxy through a specified SOCKS5 proxy, and I believe it can do what I'm looking to do... would it be a better option?

Any other suggestions?

Thanks!

---

