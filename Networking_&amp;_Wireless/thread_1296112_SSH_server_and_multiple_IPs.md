---
title: "SSH server and multiple IPs"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by Mets on 2009-10-20
I have a VPS that I host websites on, and I have two IP addresses associated with the account.  I would like to run an instance of ssh on both IPs, but running on different ports.  Specifically, I am using ip #1 to host an https site and ip #2 to host ssh on port 443, since you cannot host more than one https connection on the same ip..Both IPs point to the same box.

How can I set this up?

---

### Post by Lars Noodén on 2009-10-20
https and ssh are different protocols.  [https](http://tools.ietf.org/html/rfc2818) is http over tls or ssl.  For that, different IP addresses are needed.

> **Mets said:**
>   I would like to run an instance of ssh on both IPs, but running on different ports. ...Both IPs point to the same box.


How separate do you need to keep things?  If it is the same operating system, then just have OpenSSH server listen to the two IP addresses.
By default, it will listen to port 22 on all the IP addresses on the system.  ListenAddress in [sshd_config](http://linux.die.net/man/5/sshd_config) does that.

```
ListenAddress 0.0.0.0
```

You can verify that by testing from an outside machine:

[INDENT][FONT="Courier New"]ssh -l username *xx.yy.zz.aa*
ssh -l username *xx.yy.zz.bb*[/FONT][/INDENT]

If you want to exclude one address, then you must explicitly list the ones to listen on.  The one(s) not listed will be excluded.

```
ListenAddress *xx.yy.zz.aa*
ListenAddress *xx.yy.zz.bb*

```

---

### Post by Mets on 2009-10-20
> **Lars Noodén said:**
> https and ssh are different protocols.  [https](http://tools.ietf.org/html/rfc2818) is http over tls or ssl.  For that, different IP addresses are needed.
Thanks - it is the same operating systems, so for that I can just use the ListenAddress.

I have my one https website, which, obviously, is listening on port 443.  When I try to have my ssh server run on that port though, nothing is able to connect to it (port forwarding setup right).  So I assumed there was some conflict, and I thought I\'d need a second IP to connect to the box on the same encrypted port.

---

### Post by Lars Noodén on 2009-10-21
Right.  For all practical purposes only one service can use a port at the same time.  So the port 443 will be in use for HTTPS.  Port 22 will be for SSH.  

The default configuration for SSHd does not worry about which IP number it listens on.  Leave ListenAddress as 0.0.0.0 and it should work for port 22 for both IP numbers.

---

