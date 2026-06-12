---
title: "problem about pptp vpn"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by scegg on 2013-03-18
hi, as a newbie of linux, i need some help about create a pptp vpn client by command line.

OS: Ubuntu Server 12 x64

All i've done:
1 network check: I can ping to the remote pptp server and it's ok to connect to it by a windows client, by using windows internal pptp client with mschap-v2 protocol.

2 chap-secrets in /etc/ppp:
# Secrets for authentication using CHAP
# client         server        secret             IP addresses
MyAccount    MyVPN        MyPassword    *

3 MyVPN in /etc/ppp/peers
remotename MyVPN
linkname MyVPN
ipparam MyVPN
pty "pptp my.vpn.ip.address.here --nolaunchpppd "      /////(I hided the ip address here)
name MyAccount
noauth
require-mppe-128
require-mschap-v2
refuse-eap
refuse-pap
refuse-chap
refuse-mschap
noauth
debug
persist
maxfail 0
defaultroute
replacedefaultroute
usepeerdns

Problem:
After running sudo pon MyVPN nodetach, i got lots of message:
using channel 503808
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sh: 1: pptp: not found
Modem hangup
Connection terminated.
using channel 503809
sh: 1: pptp: not found
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Script pptp my.hided.vpn.address --nolaunchpppd  finished (pid 17260), status = 0x7f
Script pptp my.hided.vpn.address --nolaunchpppd  finished (pid 17261), status = 0x7f
Modem hangup
Connection terminated.
using channel 503810
sh: 1: pptp: not found
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Script pptp my.hided.vpn.address --nolaunchpppd  finished (pid 17262), status = 0x7f
Modem hangup
Connection terminated.
sh: 1: using channel 503811
Using interface ppp0pptp: not found


How can I make it work?

Thanks a lot.

---

### Post by scegg on 2013-03-20
lack of pptp-linux

after apt-get it, it's back to normal.

---

