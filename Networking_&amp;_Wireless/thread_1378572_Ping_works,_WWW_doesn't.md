---
title: "Ping works, WWW doesn't"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by co0lingFir3 on 2010-01-11
Hi folks,
i bought a Asus-Netbook Eee Pc 1005HA PU17 recently and am pretty happy with it. As I installed Ubuntu 9.10 on it today I was unable to get the Internet connection to work. I am able to connect to a network (wired as well as wireless) but cannot open Websites (the connection times out) or update my ubuntu install. What's really strange is that pinging IPs and websites works just fine.

I tried different Kernels (2.6.31-16 and 2.6.32) as well as installing backports.

My network chips are Atheros AR8132 for Ethernet and Atheros AR9285 for WLAN.

Furthermore the Internet works perfectly in Windows 7 and even in Moblin 2.1.

Would be great if anyone would have an advice. Thanks!

---

### Post by Iowan on 2010-01-11
My latest favorite villain is MTU - [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread shows a troubleshooting technique.

---

### Post by changingstate on 2010-01-11
I suspect something is blocking outbound connections to port 80 from your machine. 

Do you have something like this in either ~/.profile or /etc/profile? 

```
export  http_proxy=http://proxy-server.mycorp.com:3128/
```To check ~/.profile , please use :

```
gedit ~/.profile 
```For /etc/profile use : 

```
sudo gedit /etc/profile
```It could also be a firewalling rule. A look at what you've got set may be very illuminating. You can list them using :

```
sudo iptables -L
```Additionally, you're connecting via DHCP, yes? This post ( [http://ubuntuforums.org/showthread.php?t=911963](http://ubuntuforums.org/showthread.php?t=911963) ) suggests if you set up a static address, an error in the gateway setting can cause this.

---

### Post by co0lingFir3 on 2010-01-11
Thanks for your hints, but the problem still persists.

@Iowan: I tried pinging -s 32 and -s 1600 and both of them succeeded. So I don't think it's an MTU issue.

@changingstate: I didn't add anything to my profile files since it's a fresh install. There is no export statement in them. Also the iptables seem to be empty. Yes, I am connecting via DHCP.

This is the output of wget www.google.com (it is stuck after that):
```
wget www.google.com > result
--2010-01-12 00:37:58--  http://www.google.com/
Resolving www.google.com... 74.125.39.147
Connecting to www.google.com|74.125.39.147|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.it/ [following]
--2010-01-12 00:37:58--  http://www.google.it/
Resolving www.google.it... 1.0.0.0
Connecting to www.google.it|1.0.0.0|:80...
```
Seems to be a DNS problem imho. I double checked the systems proxy config and it's set to "Direct Connection to the Internet".

---

### Post by changingstate on 2010-01-11
Aaah, I've seen this with a flaky DNS server on an old D-Link router I have floating around somewhere. It utterly loathed the DNS requests from my debian 2.2 system but was quite happy with the windows systems. 

IIRC, I hacked /etc/resolv.conf to access my ISP's nameserver directly, rather than the D-Link router. It produced a little more traffic on the network, but it fixed the issue.

---

### Post by SteveHillier on 2010-01-11
Adding my three ha'p'n'th it does sound a little like DNS issues or firewall.
I hate this answer but have you rebooted your router since setting up the system.  There are times when these bits of kit get their underwear twisted and rebooting can often provide a resolution.

---

### Post by Iowan on 2010-01-11
I was afraid I'd used up my luck on MTU...
What's in */etc/resolv.conf*? (Although you'd think DNS would mess with pings, too)

---

### Post by co0lingFir3 on 2010-01-12
Thanks changingstate! Your solution seems to have fixed my problem. I just modified the setting in the network-manager not in resolv.conf as I just want this to happen for this specific connection/router (and yes it's one from D-Link ;) ).
What's strange though is that pinging works, i.e. the ping program gets the correct DNS response while others arent. Additionally my other notebook works with 9.04 withouth a glitch. Why is that?

Thanks to everyone who helped me solving this!

---

### Post by changingstate on 2010-01-12
co0lingFir3,

I've never, ever managed to find a definitive answer. The posts I read at the time burbled about 'sending requests too fast', from what I remember. My guess is that D-Links DNS server implementation is poor and runs slowly, so unless the client software is willing to wait around ( probably something in the build configuration, I've not checked ), the requests time out and you end up end up with the fault as described. I've only ever seen it with D-Link hardware, not even rubbish like the thompson gear I'm using at the moment.

---

### Post by SteveHillier on 2010-01-12
> **changingstate said:**
> co0lingFir3,

I've never, ever managed to find a definitive answer. The posts I read at the time burbled about 'sending requests too fast', from what I remember. My guess is that D-Links DNS server implementation is poor and runs slowly, so unless the client software is willing to wait around ( probably something in the build configuration, I've not checked ), the requests time out and you end up end up with the fault as described. I've only ever seen it with D-Link hardware, not even rubbish like the thompson gear I'm using at the moment.

Agree with this  I don't even know if there is a definitive answer.  I have had as much trouble with more expensive routers as well as cheaper ones.  Netgear in home use seem to do the job for the most part but I would not risk my neck on it.

I suspect part of the problem is that even if the router is playing up we can't get into it to play and try to fix it.  Shucks!!!!!!!

---

### Post by changingstate on 2010-01-12
I've actually been ruminating on this a little more, Steve, and if you look at the address that comes back, it basically looks like an empty buffer. It'd mean that linux is completing it's read from the network before the D-Link router bothers to finish writing the address it's waiting for. 

*shrug*

There are ways into routers. Buy me a JTAG kit.  :twisted:

---

### Post by SteveHillier on 2010-01-12
> **changingstate said:**
> I've actually been ruminating on this a little more, Steve, and if you look at the address that comes back, it basically looks like an empty buffer. It'd mean that linux is completing it's read from the network before the D-Link router bothers to finish writing the address it's waiting for. 

Isn't there some sort of handshaking that should avoid this happening?

---

### Post by changingstate on 2010-01-12
Handshaking has a resource overhead and DNS was invented in 1983. I didn't get my first ZX Spectrum until 1985ish!

I've been off reading rfc1035 : [http://www.faqs.org/rfcs/rfc1035.html](http://www.faqs.org/rfcs/rfc1035.html)
 
My behind has been concocting a complete fantasy, not an uncommon event. :D I dug this out of the section on resolvers : 

> 
     While local limits on the number of times a resolver will retransmit
     a particular query to a particular name server address are
     essential, the resolver should have a global per-request
     counter to limit work on a single request.  The counter should
     be set to some initial value and decremented whenever the
     resolver performs any action (retransmission timeout,
     retransmission, etc.)  If the counter passes zero, the request
     is terminated with a temporary error.
Let's say upstream debian have built the main resolver library with low values for this counter while moblin, windows and ping are willing to implement higher values.  ( I'm assuming this is a compliation time option, I've not checked the source, so if anyone has a config variable to tweak, SPEAK PLEASE ). If the DNS server on the D-Link router takes a number of operations between the values to return an answer to a query, being rather slow due to underpowered hardware or inefficient code, we might have a candidate the cause here.

Or I might be flatulating again. 

You pays your money and takes your choice.

---

