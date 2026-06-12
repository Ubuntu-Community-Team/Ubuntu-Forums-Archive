---
title: "Need Help with re-pppoe as a PPPoE server on 9.10"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by beterhans on 2010-04-06
Hello all
I'm trying to setup a PPPoE server on my 64bit Ubuntu server 9.10

looks like everything is ok 
I use a windows 7 32bit as a ppp client
Ubuntu 9.10 server 64bit as the ppp server

but I got a 629 error code 629 on windows

for log on server as following
```

Apr  7 03:02:44 EDGEPOWER pppd[13266]: pppd 2.4.5 started by root, uid 0
Apr  7 03:02:44 EDGEPOWER pppd[13266]: Using interface ppp0
Apr  7 03:02:44 EDGEPOWER pppd[13266]: Connect: ppp0 <--> /dev/pts/3
Apr  7 03:02:46 EDGEPOWER pppd[13266]: user npi logged in on tty  intf ppp0
Apr  7 03:02:46 EDGEPOWER pppd[13266]: PAP peer authentication succeeded for npi
Apr  7 03:02:47 EDGEPOWER pppd[13266]: Connect time 0.1 minutes.
Apr  7 03:02:47 EDGEPOWER pppd[13266]: Sent 58 bytes, received 78 bytes.
Apr  7 03:02:47 EDGEPOWER pppd[13266]: Terminating on signal 15
Apr  7 03:02:47 EDGEPOWER pppd[13266]: Child process /usr/sbin/pppoe -n -I eth0 -e 2:00:24:e8:a9:bd:05 -T 60 -S 'pppoe' (pid 13267) terminated with signal 15
Apr  7 03:02:53 EDGEPOWER pppd[13266]: Connection terminated.

```


and here is my configuration
/etc/ppp/pppoe-server-options
require-pap
login
lcp-echo-interval 10
lcp-echo-failure 2

pppoe-up           the startscript
#!/bin/bash
# ----------------------------------------------------
# Starts the PPPoE server and turns on NAT
# ----------------------------------------------------
# MAX is the maximum number of addresses your server
# is allowed to hand out.
PROV=pppoe
MAX=5

# BASE is the lowest IP address your server is allowed
# to hand out.

#BASE=192.168.1.238
#PLA=192.168.1.0/24

BASE=192.168.11.101
PLA=192.168.11.0/24

# NAT is the set of addresses which your server will

# NAT behind it. Other addresses behind your server

# WILL NOT be NATed.

NAT=192.168.11.0/24

# MYIP is the public IP address of this server.

MYIP=192.168.11.1

##########################################

# Here is where the script actually starts executing.
##########################################

# Disable IP spoofing on the external interface.

#/sbin/iptables -A INPUT -i eth0 -s $NAT -j DROP

# Enable NAT for the private addresses we hand out.

#/sbin/iptables -t nat -A POSTROUTING -s $NAT -j $NAT --to-source $MYIP

# Launch the server.

/usr/sbin/pppoe-server pty -T 60 -I eth0 -L $MYIP -N $MAX -C $PROV -S $PROV -R $PLA

#echo "1" > "/proc/sys/net/ipv4/ip_forward"



any idea ? please help

---

### Post by beterhans on 2010-04-07
solved

just modify the pap-secrets

username     *       password *

---

