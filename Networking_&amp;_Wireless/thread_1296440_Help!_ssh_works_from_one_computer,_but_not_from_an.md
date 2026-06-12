---
title: "Help! ssh works from one computer, but not from another"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by illuzen on 2009-10-20
Hi, I'm setting up openssh-server for my personal desktop.  I can connect to it via my personal laptop, so I know ssh works, but I can't connect from the campus server.

Desktop - Ubuntu 8.10 Intrepid

Laptop - Mac OS X Snow Leopard

Server - Ubuntu 9.04

I can ssh no problem into the campus server, but when I attempt to ssh from the school server into the desktop, the prompt drops to the next line likes it's waiting for more input.  To escape, the kill command (ctrl+c) always works.  I've checked my desktop's /var/log/auth.log and no login attempts from the server are ever logged.

Troubleshooting already attempted:

Looked at the /etc/ssh/ssh_config file for both the destop and the server.  The differences were:

On the desktop: 
```
GSSAPIDelegateCredentials no
(others all default)
```On the server:
```
GSSAPIDelegateCredentials yes
GSSAPIKeyExchange yes
GSSAPITrustDNS  yes
```Created ~/.ssh/config on the server specifying modified behavior for sshing onto my desktop:
```
Host desktop
HostName 000.000.000.000 (my ip address, edited to 0's for my privacy)
User username (edited for my privacy)
GSSAPIAuthentication yes
GSSAPIDelegateCredentials no
GSSAPIKeyExchange no
```Didn't fix the problem. :(

My next thought is that the campus server uses kerberos for authentication.  Would this affect the server's ability to ssh into my machine?

Another thought is that the server uses openVPN as well, which my desktop is not a part of.  Would this affect the server's ability to ssh out?  My desktop doesn't use a VPN or public key authentication or anything that is not a standard, default part of ubuntu.

Any thoughts?  Am I heading in the right direction?  Thanks!

---

### Post by issih on 2009-10-20
First thought, if you have a router in your home setup, does it port forward port 22 (or whatever custom port you listen on) from the wan to your desktop pc on the lan?

Just seems the most obvious possible problem...

---

### Post by illuzen on 2009-10-20
Thanks for the quick response!

The desktop is actually in a dorm room on the same physical network as the server.

---

