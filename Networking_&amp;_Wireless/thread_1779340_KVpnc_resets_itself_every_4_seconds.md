---
title: "KVpnc resets itself every 4 seconds?"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by DaleEMoore on 2011-06-10
When I KVpnc into a client VPN I connect, but every 4 minutes, or so, I am reconnected. Since I'm RDPing into their server remmina (and rdesktop too) loose their mind and I have to manually reconnect to the server. The attachment Screenshot-8a.png shows the display KVpnc uses to describe this when it happens.

/var/log/syslog shows it happening twice here:```
Jun 10 08:47:19 RyCycle avahi-daemon[797]: Withdrawing workstation service for tun0.
Jun 10 08:47:19 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 10 08:47:21 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 10 08:47:21 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Jun 10 08:51:32 RyCycle avahi-daemon[797]: Withdrawing workstation service for tun0.
Jun 10 08:51:32 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 10 08:51:34 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 10 08:51:34 RyCycle NetworkManager[795]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.

```Any suggestions you have are very much appreciated,
Dale E. Moore

---

### Post by DaleEMoore on 2011-06-13
nudge

---

### Post by DaleEMoore on 2011-06-17
Oops, my original subject should have said "minutes" instead of "seconds." This fixes that.

Also, after I've VPNed in for about 10 hours it stops reseting itself every 4 "minutes."

Maybe I should just leave it on always.

---

### Post by DaleEMoore on 2011-06-23
It settles down after a while.

I left it connected for 24 hours and when I came back to it, it had stopped reseting itself every 4 minutes.

---

### Post by LordMael on 2011-07-19
I ended up uninstalling vpnc and kvpnc, then re-installing kvpnc followed by vpnc.  Rebooted and everything has been stable since.  Not sure why it worked that way but it's working for me now.

-LM

---

### Post by DaleEMoore on 2011-09-12
I wiped out that machine and installed openSUSE 11.4. I've been using KVpnc on openSUSE for a few months and never once had this problem.

I wiped out that machine and installed Ubuntu 11.10 beta 1 2 days ago. The same problem exists here.

---

### Post by DaleEMoore on 2011-09-13
I guess this [https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/849090](https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/849090) is the next step in escalating this issue.

---

