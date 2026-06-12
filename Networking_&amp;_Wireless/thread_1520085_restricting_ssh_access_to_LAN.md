---
title: "restricting ssh access to LAN"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by HyperFlexed on 2010-06-29
Hi, I have a desktop (picard), and I want to be able to connect to it from my sisters laptop (zuma) to quickly scp files from my machine to hers.

At the same time I don't want the whole world to be able to connect to my machine via SSH. We're connected through a router.

I've tried adding the line

"ListenAddress 192.168.0.0"

to /etc/ssh/sshd_config, but this prevents me from being able to connect to my machine from another on the network. From my understanding of the ListenAddress directive, I would assume "ListenAddress 192.168.0.0" would allow my sister's address through (192.168.0.192).

Am I missing something?

---

### Post by prshah on 2010-06-29
> **HyperFlexed said:**
> from my sisters laptop (zuma) to quickly scp files from my machine to hers.

I don't want the whole world to be able to connect to my machine via SSH. We're connected through a router.

"ListenAddress 192.168.0.0"

Am I missing something?

Yes; you cannot use the ListenAddress directive for this. The correct usage of ListenAddress will be in a case where you have multiple networks connected to your SSH server (ie, with multiple network cards). (Simplistic example, don't take literally) In this case, the default operation of the SSH server will be to listen (on it's given port) to every one of the network cards. You can restrict this by using ListenAddress to tell sshd to listen to only one (or more) networks (and hence only the corresponding network cards).

To have machines from the Internet connect to your SSH machine via the router requires configuration on the router (aka NAT, port forwarding etc). If you haven't done this, your ssh server will not be accessible. 

Or you can use a "Match" block to set MaxSessions to 0 for IP address that are not in your network range (See man sshd_config for details).

Or you can setup /etc/hosts.deny to deny all machines access, then /etc/hosts.allow to allow machines in a specific IP range (Eg 192.168.0.5/250). Note that if you allow your router's IP address (Eg 192.168.0.1) then you effectively allow all Internet access (if your router is setup to use Port Forwarding / NAT).

Please post back if you need any clarifications.

---

