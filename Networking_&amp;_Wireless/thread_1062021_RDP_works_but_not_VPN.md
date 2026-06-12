---
title: "RDP works but not VPN"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by warped6 on 2009-02-06
I decided to try and fix a network problem that has been bugging me for awhile.

I'm running Ubuntu 8.10 with all the latest fixes. Trying to connect to a Windows 2003 server.

I CAN do a remote desktop connection to it just fine. And it is running the VPN software.

I tried setting up the connection through NM using just the defaults. No luck. I get a "terminating on signal 15" error in my log.

Next I turned on "Use point-to-point" and went into gconf-editor and added "refuse-eap=yes" to the connection. (These steps solved a problem I was having with a different VPN connection.)

Still no love.

Here is the output from tail -f /var/log/messages

Feb  6 10:55:30 epicscience-mike pppd[12729]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Feb  6 10:55:30 epicscience-mike pppd[12729]: pppd 2.4.4 started by root, uid 0
Feb  6 10:55:30 epicscience-mike pppd[12729]: Using interface ppp0
Feb  6 10:55:30 epicscience-mike pppd[12729]: Connect: ppp0 <--> /dev/pts/3
Feb  6 10:56:10 epicscience-mike pppd[12729]: Terminating on signal 15
Feb  6 10:56:10 epicscience-mike pppd[12729]: Child process /usr/sbin/pptp xxxx.xxxxxxxxx.com --nolaunchpppd --logstring nm-pptp-service-12726 (pid 12730) terminated with signal 15
Feb  6 10:56:10 epicscience-mike pppd[12729]: Modem hangup
Feb  6 10:56:10 epicscience-mike pppd[12729]: Connection terminated.
Feb  6 10:56:10 epicscience-mike pppd[12729]: Exit.

I took out the actual addie I'm connecting to.

Any suggestions?

TIA

---

