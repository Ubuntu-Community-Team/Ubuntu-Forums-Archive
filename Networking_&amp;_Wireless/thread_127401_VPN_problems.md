---
title: "VPN problems"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by Kashirigi on 2006-02-08
Hi everyone,

I'm pretty new to Linux, but so far everything has gone relatively smoothly except for creating a VPN connection to work. It's a MS VPN, so I've installed pptp-linux, pppd, pptpconfig, etc.

Regardless of what I try, I'm unable to get a functioning tunnel.

Details for what I'm trying to do exactly are here:
[http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html](http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html)

Here's the log from my attempted connection:
pptpconfig: debug information dump begins
pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.2 2004/06/19 08:57:15
# pppd --version
pppd version 2.4.3
# uname -a
Linux arbalest 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686 GNU/Linux
# grep mppe /proc/modules
# modinfo ppp_mppe
Array
(
    [name] => vpn.ubc.ca
    [server] => vpn.ubc.ca
    [domain] => 
    [username] => Supersekrit
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_interface_only
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 1
    [nomppe-128] => 
    [refuse-eap] => 
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.1.0      0.0.0.0         255.255.255.128 U     0      0        0 wlan0
0.0.0.0         172.16.1.1      0.0.0.0         UG    0      0        0 wlan0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/vpn.ubc.ca)
updetach		# (from command line)
logfd 1		# (from command line)
linkname vpn.ubc.ca		# (from /etc/ppp/peers/vpn.ubc.ca)
dump		# (from /etc/ppp/peers/vpn.ubc.ca)
noauth		# (from /etc/ppp/peers/vpn.ubc.ca)
name Supersekrit	# (from /etc/ppp/peers/vpn.ubc.ca)
remotename vpn.ubc.ca		# (from /etc/ppp/peers/vpn.ubc.ca)
		# (from /etc/ppp/options)
pty pptp vpn.ubc.ca --nolaunchpppd 		# (from /etc/ppp/peers/vpn.ubc.ca)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam vpn.ubc.ca		# (from /etc/ppp/peers/vpn.ubc.ca)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/vpn.ubc.ca)
		# (from /etc/ppp/peers/vpn.ubc.ca)
nomppe-40		# (from /etc/ppp/peers/vpn.ubc.ca)
noipx		# (from /etc/ppp/options)
using channel 6
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/8
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x88bc2146> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
using channel 7
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/9
Waiting for 2 child processes...
  script pptp vpn.ubc.ca --nolaunchpppd , pid 10436
  script pptp vpn.ubc.ca --nolaunchpppd , pid 10420
Script pptp vpn.ubc.ca --nolaunchpppd  finished (pid 10420), status = 0x0
sending SIGTERM to process 10436
tcflush failed: Bad file descriptor
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.1.0      0.0.0.0         255.255.255.128 U     0      0        0 wlan0
0.0.0.0         172.16.1.1      0.0.0.0         UG    0      0        0 wlan0
pptpconfig: pppd process terminated by signal 10 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.1.0      0.0.0.0         255.255.255.128 U     0      0        0 wlan0
0.0.0.0         172.16.1.1      0.0.0.0         UG    0      0        0 wlan0


I would appreciate any help  you can give.

Thanks.

---

### Post by hajk on 2006-02-09
You say that you "installed pptp-linux,.." -- did you get those straight from SourceForge (as the UBC instructions tell you to do), or did you install the Ubuntu packages "pptp-linux" and "pptpd"? Going the SourceForge route is asking for trouble, in my opinion.

---

### Post by mips on 2006-02-09
[http://www.ubuntuforums.org/showthread.php?t=111796](http://www.ubuntuforums.org/showthread.php?t=111796)

Maybe contact Bone Down as I know he got his working with the help of one of the pptp developers.

He needed a extra script or something like that.

---

### Post by Kashirigi on 2006-02-09
[QUOTE=hajk]You say that you "installed pptp-linux,.." -- did you get those straight from SourceForge (as the UBC instructions tell you to do), or did you install the Ubuntu packages "pptp-linux" and "pptpd"? Going the SourceForge route is asking for trouble, in my opinion.[/QUOTE]

I installed the Ubuntu packages, as that seemed to make more sense. I upgraded pptpconfig to the sourceforge most current version last night, though.

Not that it helped.

---

### Post by Kashirigi on 2006-02-10
I'd like to thank everybody who helped in this thread; I've solved the problem.

It was, in fact, a firewall configuration problem. Switching from Firestarter to Guarddog solved all of my problems. I feel certain there's a way to configure the settings in Firestarter, but I'm not so attached that I can't switch.. .

Again, thanks for your help.

---

