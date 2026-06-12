---
title: "Having problem to setup pptp server on ubuntu 10.04"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by sunnycorner on 2012-09-24
hello everyone! this is my first post in the forum!!! yay!!

So I am a network engineer having quite limited experience with Ubuntu. I have been following up the the online instruction to setup pptp server 
[http://blog.riobard.com/2011/11/12/pptp-vpn-on-ubuntu](http://blog.riobard.com/2011/11/12/pptp-vpn-on-ubuntu)
but without much luck to get it to work.  My server is a vm running a apple xserve behind a Cisco firewall, I made sure tcp 1723 and GRE are opened for the box.
Below is the syslog output, looks like I always got stuck at 

**GRE: Bad checksum from pppd.**

[I]Sep 24 13:21:53 ubuntu pptpd[1231]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Sep 24 13:21:53 ubuntu pptpd[1231]: CTRL: Reaping child PPP[1232]
Sep 24 13:21:53 ubuntu pptpd[1231]: CTRL: Client 166.137.85.165 control connection finished
Sep 24 13:22:41 ubuntu pptpd[1276]: MGR: connections limit (100) reached, extra IP addresses ignored
Sep 24 13:22:41 ubuntu pptpd[1277]: MGR: Manager process started
Sep 24 13:22:41 ubuntu pptpd[1277]: MGR: Maximum of 100 connections available
Sep 24 13:22:50 ubuntu pptpd[1278]: CTRL: Client 166.137.85.165 control connection started
Sep 24 13:22:51 ubuntu pptpd[1278]: CTRL: Starting call (launching pppd, opening GRE)
Sep 24 13:22:51 ubuntu pppd[1279]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Sep 24 13:22:51 ubuntu pppd[1279]: pppd 2.4.5 started by root, uid 0
Sep 24 13:22:51 ubuntu pppd[1279]: Using interface ppp0
Sep 24 13:22:51 ubuntu pppd[1279]: Connect: ppp0 <--> /dev/pts/1
Sep 24 13:22:51 ubuntu pptpd[1278]: GRE: Bad checksum from pppd.
Sep 24 13:23:21 ubuntu pppd[1279]: LCP: timeout sending Config-Requests
Sep 24 13:23:21 ubuntu pppd[1279]: Connection terminated.
Sep 24 13:23:21 ubuntu pppd[1279]: Modem hangup
Sep 24 13:23:21 ubuntu pppd[1279]: Exit.
Sep 24 13:23:21 ubuntu pptpd[1278]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Sep 24 13:23:21 ubuntu pptpd[1278]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Sep 24 13:23:21 ubuntu pptpd[1278]: CTRL: Reaping child PPP[1279]
Sep 24 13:23:21 ubuntu pptpd[1278]: CTRL: Client 166.137.85.165 control connection finished[/I]

---

