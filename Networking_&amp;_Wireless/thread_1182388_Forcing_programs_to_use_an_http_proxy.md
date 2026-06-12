---
title: "Forcing programs to use an http proxy"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by BrokenMemories on 2009-06-08
Hi All,

Here's my problem, I'm a PhD student and as such I spend the vast majority of my waking hours at the university.

The university has an authorised http proxy which must be used.

I currently have the Gnome global settings and .bashrc setup as follows:

hhtp://username;password@uniprox;port (or : I forget)

this works for the majority of programs. However there are a number of programs that I wish to use that a) don't have the option to use a proxy, b) have issues using authentication (Mono/python based programs) c) has some other funky stuff that otherwise doesn't recognise the proxy.

So what do I want from you all?

How can I set up my computer such that ALL attempts to use the internet (ftp/http/https) from ALL programs are forwarded/routed through to the university proxy server? 

In essence I don't want to set up proxy settings for any programs (including GNOME global settings) just have one global...well firewall I guess... that sends everything to my uni proxy no matter the source.

Thanks in advance

BM

EDIT: Currently using Ubuntu 9.04

EDIT: A possible Fix/Work around

Downloaded Squid.

Edited the squid.config file by adding the following lines to the appropriate places

acl localnet src 10.X.X.X #where 10.X.X.X is the ip adress of the eth0 or wlan0

http_access allow localnet

http_port XXXX # changed port to my own port default is 3128

cache_peer proxy.foo.domain.com parent XXXX 0 no-query proxy-only login=user:password name=fooProxy #change foo and XXXX to appropriate settings

cache_peer_access uniProxy deny localhost # stops localhost going through proxy
always_direct allow localhost

never_direct allow localnet #force my computer to use the uni proxy

# Caching stuff all defaults except for cache_mem and max object
cache_mem 100 MB
maximum_object_size_in_memory 100 KB

cache_replacement_policy heap GDSF
cache_dir ufs /var/spool/squid 100 16 256
maximum_object_size 20000 KB


And finally... Set all proxy settings in (GNOME, firefox, bashrc etc) too locolnet:port, where localnet is the eth0/wlan0 ipadress and port is the http_port of Squid.

If anyone has any ideas on how to make it transparent proxy I would appreciate it greatly.

BM

---

### Post by BrokenMemories on 2009-06-09
Just so this isn't a shameless bump,

This problem may seem straight forward to some. However, I don't know exactly what the technology/programs I need are, nor what I should be searching for in the way of guides.

I have done some searching for guides/solutions however I've been unable to find what I want. If anyone could point me in the right direction that would be great.

Cheers,
BM

---

### Post by Dr Small on 2009-06-09
If privoxy can act as a HTTP proxy (which, I think it may be able to), then all you would need is a few firewall rules to redirect all outbound traffic to privoxy. Privoxy would then take the request, and forward it to the HTTP proxy server.

---

### Post by BrokenMemories on 2009-06-09
Cool thanks for the reply I'll give it a go

---

### Post by BrokenMemories on 2009-06-10
Mkay so still stuck fumbling in the dark but..

How does using iptables to redirect all tcp port 80 sound? Would that work

e.g.

$ sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to [http://username:](http://username:) [email]password@proxyaddress.com[/email]: port

I'm very much a novice at iptables and still trying to get my head around the various commands.

---

### Post by BrokenMemories on 2009-06-11
> **BrokenMemories said:**
> Mkay so still stuck fumbling in the dark but..

How does using iptables to redirect all tcp port 80 sound? Would that work

e.g.

$ sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to [http://username:](http://username:) [email]password@proxyaddress.com[/email]: port

I'm very much a novice at iptables and still trying to get my head around the various commands.

Well I tried the iptables thing... that doesnt work. It neeeds to have IPaddress:port only and cant take authentication.

I did a little bit more digging and found privoxy (as above post suggested) but that doesn't work either, because its Forwarding function is incapable of handling authenticated http proxies!!??! sigh...

So... onto the next thing.. tried using another program called proxychains.. that flat out didnt work. And finally tried another program called simpleproxy. limited success.

Simpleproxy sets up a proxy based on 127.0.0.1:port then forwards all traffic on the port to the HTTP proxy you specify in the config file. As a test I set Firefox proxy to 127.0.0.1:myport and simpleproxy picked it up, but was incapable of forwarding it because it can not use authentication for standard HTTP only HTTPS!! sigh again...

So now I'm really stuck. Does anyone have any suggestions at all?

---

