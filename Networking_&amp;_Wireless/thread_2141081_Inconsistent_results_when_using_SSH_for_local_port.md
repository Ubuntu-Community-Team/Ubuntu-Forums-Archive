---
title: "Inconsistent results when using SSH for local port forwarding"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by VforVincent on 2013-05-01
Hi,

I'm trying to test my understanding of port forwarding and there's an issue that currently has me stumped. I've installed the OpenSSH client and daemon on my local machine and I'd like to try routing my HTTP and HTTPS traffic through a tunnel. I connect to my own machine via SSH as follows: ```
ssh -L 8080:www.google.com:80 vince@sokrates
```. That way, when I go to localhost:8080 I end up at Google. I guess it's not fool-proof yet because my browser indicates that HTTPS is used here and I'm not doing anything with port 443 yet, but I digress... The problem is that this approach doesn't work for every website. For instance, if I try [www.ubuntuforums.org](www.ubuntuforums.org), I get redirected to canonical.com. And if I try ubuntu.com, I get an error page. So clearly, I'm missing some of the finer details.

Does anyone know what could cause this lack of transparency?

Thanks!

V.

---

### Post by ahallubuntu on 2013-05-01
~

---

### Post by papibe on 2013-05-01
Hi VforVincent.

The usual way to tunnelling all browser traffic is by using both a dynamic application-level port forwarding (option -D), and the browser capabilities to proxy its traffic.

First, create the tunnel:
```
ssh -D8080 vince@sokrates
```
Then, in Firefox:
```
Preferences -> Advanced -> Network -> Connection Settings
```
there, set a manual proxy configuration:
```
Socks: 127.0.0.1      Port: 8080
```
That should do it. Browse normally.

Let us know how it goes.
Regards.

---

### Post by VforVincent on 2013-05-01
I'm trying to figure out how port forwarding works by going over a few use cases. Right now, I'm trying to simulate a setup where I'd like to do some secure browsing through a remote machine. I don't have the infrastructure available to really set this up (no public IP where I can set up an SSH server), so I'm running everything locally. Normally, you'd have a tunnel from my machine which is an SSH client (e.g. at work) to an SSH server (e.g. my machine at home) and I'd like to browse on the client without anyone being able to monitor my traffic. I know this sort of setup could get you in trouble if it violates security policies, but I have no plans to do anything of the sort.

---

### Post by VforVincent on 2013-05-01
Hi Papibe,

Looks like that did the trick. I hadn't come across dynamic port forwarding before yet. I'm a bit surprised that it's the recommended solution to this kind of problem, given that it doesn't get the same coverage local and remote forwarding get, but I'll read up on it to see what makes it more appropriate. Thanks!

V.

---

