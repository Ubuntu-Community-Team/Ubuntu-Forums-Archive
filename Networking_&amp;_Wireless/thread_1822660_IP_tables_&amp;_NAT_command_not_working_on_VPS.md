---
title: "IP tables &amp; NAT command not working on VPS"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by iamacup on 2011-08-10
Hi all

My Aim: I want to use my VPS as an OpenVPN server. 

My Problem: IP tables wont accept my rule

I have been following this tutorial: [http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu#comment-15684](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu#comment-15684)

I get to the stage where I need  to put this command in 

```
 sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE 
```

And I get this error

```
 WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module ip_tables not found.
iptables v1.4.10: can't initialize iptables table `nat': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

I have looked all over but can't find a solution to this problem.

Is this a symptom of using a VPS (I have been unable to use some of IPtables more advanced features before purely because I am running in a virtualised OS) or is there something I can do to fix this from my end.

Uname –a
```
 Linux www 2.6.18-194.26.1.el5.028stab079.2 #1 SMP Fri Dec 17 19:25:15 MSK 2010 i686 i686 i386 GNU/Linux
```

Running Ubuntu 11.04 in OpenVZ

Cheers

Tom

---

