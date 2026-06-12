---
title: "command line proxy"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by chunkxzor on 2009-03-29
I know there is a way to set an http proxy using the command line, I just down know how. I'm sure someone around here knows how to do it, if you'd be so kind to help me out here i'd be very grateful :)

---

### Post by BkkBonanza on 2009-03-29
The easiest proxy I know by command line is the one built in to ssh.
Type,

ssh -D 8080 user@proxy_ip

sshd needs to be running on the target proxy machine and then all requests (any protocols) made to localhost 8080 on your machine will get proxied to the remote machine (at proxyip). After doing that you need to tell the program you want to use the proxy as SOCKS 5 proxy.

---

