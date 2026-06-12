---
title: "Ubuntu in Amazon AWS + pptpd"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by blackmelon on 2012-04-23
Hello everyone, really need help the community, as my head is not enough. 

Given: The machine in Amazon EC2 on Ubuntu withe default pptpd installation. After setting up I was able to connect to the VPN and try session, it was the first and the last connection, and then when I try to connect to the VPN log now this error: GRE: read (fd = 7, buffer = 8056b60, len = 8260) from network failed: status = -1 error = Protocol not available

I google a lot (as I understand the error quite standard, and there is a standard set of her decision: [http://poptop.sourceforge.net/dox/gre-protocol-unavailable.phtml](http://poptop.sourceforge.net/dox/gre-protocol-unavailable.phtml)), tried different settings in iptables - nothing helps.

**Error:**
```

Apr 23 03:04:12 ip-10-226-134-198 pptpd[811]: CTRL: Client 194.100.173.6 control connection started
Apr 23 03:04:13 ip-10-226-134-198 pptpd[811]: CTRL: Starting call (launching pppd, opening GRE)
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: pppd 2.4.5 started by root, uid 0
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Using interface ppp0
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Connect: ppp0 <--> /dev/pts/1
Apr 23 03:04:13 ip-10-226-134-198 pptpd[811]: GRE: read(fd=7,buffer=6095a0,len=8260) from network failed: status = -1 error = Protocol not available
Apr 23 03:04:13 ip-10-226-134-198 pptpd[811]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Apr 23 03:04:13 ip-10-226-134-198 pptpd[811]: CTRL: Reaping child PPP[813]
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Modem hangup
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Connection terminated.
Apr 23 03:04:13 ip-10-226-134-198 pppd[813]: Exit.
Apr 23 03:04:13 ip-10-226-134-198 pptpd[811]: CTRL: Client 194.100.173.6 control connection finished

```

My settings

**/etc/pptpd.conf**
```

option /etc/ppp/pptpd-options
logwtmp
bcrelay eth0
#noipparam

```

**/etc/ppp/pptpd-options**
```

auth
name pptpd

refuse-pap
refuse-chap
refuse-mschap
#require-mppe
require-mschap-v2
require-mppe-128


ms-dns 8.8.8.8
#ms-dns 8.8.4.4

#proxyarp
nodefaultroute
lock
nobsdcomp

```


**/etc/rc.local**
```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
exit 0

```


](*,)

---

