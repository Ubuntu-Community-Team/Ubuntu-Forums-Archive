---
title: "Can't connect to Windows VPN"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by ld.4lpha on 2010-04-02
```
pppd call myvpn
``````
/var/log/messages

Apr  1 19:00:41 ld4lpha pppd[22146]: pppd 2.4.5 started by root, uid 0
Apr  1 19:00:41 ld4lpha pppd[22146]: Using interface ppp0
Apr  1 19:00:41 ld4lpha pppd[22146]: Connect: ppp0 <--> /dev/pts/1
Apr  1 19:00:41 ld4lpha pppd[22146]: Modem hangup
Apr  1 19:00:41 ld4lpha pppd[22146]: Connection terminated.
Apr  1 19:00:41 ld4lpha pppd[22146]: Exit.
```

Details:

```
/etc/ppp/chap-secrets

myUsername PPTP myPassword *
``````
/etc/ppp/peers/myvpn

pty "pptp vpn.myserver.com --nolaunchpppd"
name myUsername
remotename windowsDomainName
require-mppe-128
file /etc/ppp/options.pptp
```In the options.pptp file, I am refusing EAP and PAP.

```
/etc/ppp/ip-up.d/route-traffic

#!/bin/bash
route add -net 192.168.0.0/24 dev ppp0
```The network I am connecting FROM is 192.128.0.  The network I am connecting TO is 10.0.0.  Do I have this right in my routes?

Any suggestions?

Thanks!
LD

---

### Post by prodigy_ on 2010-04-03
Try to use debug mode as described [here](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#debug). Maybe log messages will help you to understand what's going on.

---

### Post by ld.4lpha on 2010-04-05
Thanks for the suggestion; debugging mode is good to know.

Unfortunately, using pppd with debug mode on didn't provide information that points to why my connection is being dropped. 

I did, however start tcpdump -vv and then initiate the connection again (should have thought of this long ago) which gave me plenty of information to work with.

Turns out the policy on the other end is blocking me for some reason; I'll have to look at that tomorrow when I'm in the office.

Thanks again for the input, prodigy.

---

