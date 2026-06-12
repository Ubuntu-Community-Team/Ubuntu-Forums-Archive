---
title: "pptpd + radius"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Styles on 2010-06-24
**SOLVED** Clear text wasn't enabled " require-pap "


Hi all,

     Think I might need a second pair of eyes, I have racking my brain too long on this one. Anyway here's the issue I'm experiencing. I have PPTPD setup and was working great with chap-secrets, but I'm moving to a radius on a different server for user authentication. I have the radius server setup and I can authenticate via Radius through SSH and libpam-radius-auth just fine. But with my PPTPD server setup to auth against RADIUS, it fails. I don't see any logging on the RADIUS server when I use PPTPD so I'm assuming PPTPD is not send anything to the Radius server. I'm most likely missing something small and need a second pair of eyes to take a look. Here is my setup, pretty standard. 

OS= Ubuntu 9.4
```

Package: pptpd
New: yes
State: installed
Automatically installed: no
Version: 1.3.4-2.1ubuntu1.9.04.1

Package: libradiusclient-ng2
New: yes
State: installed
Automatically installed: no
Version: 0.5.6-1

```
/etc/pptpd.conf
```

option /etc/ppp/pptpd-options
dump
debug
logwtmp
localip 10.0.0.2
remoteip 10.0.0.24-30

```

/etc/ppp/pptpd-options
```

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 10.0.0.1
ms-wins 10.0.0.1
proxyarp
lock
nobsdcomp
novj
novjccomp
nologfd
auth
nodefaultroute
plugin radius.so
radius-config-file /etc/radiusclient-ng/radiusclient.conf
plugin radattr.so

```
/etc/radiusclient-ng/radiusclient.conf
```

auth_order radius
login_tries 4
login_timeout 60
nologin /etc/nologin
issue /etc/radiusclient-ng/issue
authserver 10.0.0.2
acctserver 10.0.0.2
servers /etc/radiusclient-ng/servers
dictionary /etc/radiusclient-ng/dictionary
login_radius /usr/sbin/login.radius
seqfile /var/run/radius.seq
mapfile /etc/radiusclient-ng/port-id-map
default_realm
radius_timeout 10
radius_retries 3
#bindaddr *
login_local /bin/login

```

/etc/radiusclient-ng/servers
```

test             pptpd   password            *

```

I'm going to omit the dictionary files as they are correct, I do see the radius plugins loading, but it's not even attempting to contact my radius server, as my radius server logs don't show any attempt being made. But on the same server if I authenticate via Radius PAM I'm able to login, and my radius logs show the connection. I'm pretty much at a loss now and any help or ideas would be great. I have tried this same setup on Ubuntu 10.4 as well with the same results, which leads me to believe it's something I'm doing.

SysLog file (note: ip's have been sanitized)

```

Jun 24 14:31:01 auth-test pptpd[14877]: MGR: Launching /usr/sbin/pptpctrl to handle client
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: local address = 10.0.0.117
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: remote address = 10.0.0.24
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: pppd options file = /etc/ppp/pptpd-options
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Client 207.109.47.196 control connection started
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 1)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Made a START CTRL CONN RPLY packet
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: I wrote 156 bytes to the client.
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Sent packet to client
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 7)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Set parameters to 100000000 maxbps, 64 window size
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Made a OUT CALL RPLY packet
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Starting call (launching pppd, opening GRE)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: pty_fd = 6
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: tty_fd = 7
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: I wrote 32 bytes to the client.
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Sent packet to client
Jun 24 14:31:01 auth-test pptpd[14878]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
Jun 24 14:31:01 auth-test pptpd[14878]: CTRL (PPPD Launcher): local address = 10.0.0.117
Jun 24 14:31:01 auth-test pptpd[14878]: CTRL (PPPD Launcher): remote address = 10.0.0.24
Jun 24 14:31:01 auth-test pppd[14878]: Plugin radius.so loaded.
Jun 24 14:31:01 auth-test pppd[14878]: RADIUS plugin initialized.
Jun 24 14:31:01 auth-test pppd[14878]: Plugin radattr.so loaded.
Jun 24 14:31:01 auth-test pppd[14878]: RADATTR plugin initialized.
Jun 24 14:31:01 auth-test pppd[14878]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jun 24 14:31:01 auth-test pppd[14878]: pppd 2.4.5 started by root, uid 0
Jun 24 14:31:01 auth-test pppd[14878]: Using interface ppp0
Jun 24 14:31:01 auth-test pppd[14878]: Connect: ppp0 <--> /dev/pts/0
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 15)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Got a SET LINK INFO packet with standard ACCMs
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #0
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #1
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #2
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 15)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #3
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #4
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #5
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #6
Jun 24 14:31:01 auth-test pppd[14878]: Peer test failed CHAP authentication
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 15)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Got a SET LINK INFO packet with standard ACCMs
Jun 24 14:31:01 auth-test pptpd[14877]: GRE: accepting packet #7
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received PPTP Control Message (type: 12)
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Made a CALL DISCONNECT RPLY packet
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Received CALL CLR request (closing call)
Jun 24 14:31:01 auth-test pppd[14878]: Modem hangup
Jun 24 14:31:01 auth-test pppd[14878]: Connection terminated.
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Reaping child PPP[14878]
Jun 24 14:31:01 auth-test pppd[14878]: Exit.
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Client 4.4.4.4 control connection finished
Jun 24 14:31:01 auth-test pptpd[14877]: CTRL: Exiting now
Jun 24 14:31:01 auth-test pptpd[14871]: MGR: Reaped child 14877

```

Thanks for your time, and cheers,

---

