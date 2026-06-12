---
title: "squid Proxy server bridge"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by daniele72 on 2009-05-18
Hello everyone,
I'm working with the last Ubuntu release (9.04) and to be honest I recently started working with Linux environment, for a specific needs.
I have to set up a proxy server to share an internet connection with hotspot.

So I thought to use a pC with two ethernet cards and put it in the middle between the wireless access point and the router connected to internet.
I also need to authenticate each user with their own: user and pwd.

The address are:
- Eth0 (vs router) has addr 10.0.0.10
- Eth1 (vs wLAN) has addr 192.168.1.2

I set up Squid as proxy server and I used NCSA to authenticate the user.
The authentication works.
[B]
First question.[/B] Now I don't know what I have to do to bridge traffic coming from Eth1 to Eth0 obviously after and user has been authenticate.

**Secondly**: Using NCSA I need to put all the user and pwd manually by terminal. I heard
that there is a framework GOsa who is a web interface for LDAP authentication. Does anybody know how it work?

**Finally:** Any suggestion would be appreciated

Thanks a lot:KS

---

