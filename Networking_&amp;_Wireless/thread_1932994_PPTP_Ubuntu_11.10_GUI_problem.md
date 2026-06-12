---
title: "PPTP Ubuntu 11.10 GUI problem"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by alscdz on 2012-02-28
Hi,
when I try to connect to PPTP windows VPN (over GUI) I get the following in syslog:


Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> Starting VPN service 'pptp'...
Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 10865
Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> VPN service 'pptp' appeared; activating connections
Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> VPN plugin state changed: 1
Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> VPN plugin state changed: 3
Feb 28 17:50:36 ales-laptop NetworkManager[931]: <info> VPN connection 'VPN espro' (Connect) reply received.
Feb 28 17:50:36 ales-laptop pppd[10867]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Feb 28 17:50:36 ales-laptop pppd[10867]: pppd 2.4.5 started by root, uid 0
Feb 28 17:50:36 ales-laptop pppd[10867]: Using interface ppp0
Feb 28 17:50:36 ales-laptop pppd[10867]: Connect: ppp0 <--> /dev/pts/2
Feb 28 17:50:36 ales-laptop NetworkManager[931]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
**Feb 28 17:50:36 ales-laptop NetworkManager[931]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.**
Feb 28 17:50:36 ales-laptop pptp[10870]: nm-pptp-service-10865 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Feb 28 17:51:07 ales-laptop pppd[10867]: LCP: timeout sending Config-Requests
Feb 28 17:51:07 ales-laptop pppd[10867]: Connection terminated.
Feb 28 17:51:07 ales-laptop avahi-daemon[933]: Withdrawing workstation service for ppp0.
Feb 28 17:51:07 ales-laptop NetworkManager[931]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 28 17:51:07 ales-laptop NetworkManager[931]: <warn> VPN plugin failed: 1
Feb 28 17:51:07 ales-laptop pppd[10867]: Modem hangup
Feb 28 17:51:07 ales-laptop NetworkManager[931]: <warn> VPN plugin failed: 1

I have gateway,username and password set (no NT Domain) and 
MPPE 128bit encrytion checked.

Any ideas what is wrong?

---

