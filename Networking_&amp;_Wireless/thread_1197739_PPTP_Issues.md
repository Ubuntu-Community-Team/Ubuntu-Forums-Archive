---
title: "PPTP Issues"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by I[AM]SMRT on 2009-06-26
To connect to my school's wireless I need to setup a pptp connection. I followed the tutorial here:

[http://dotcommie.net/lugsb/PPTP/](http://dotcommie.net/lugsb/PPTP/)

But it's not actually making the connection, here's the pon debug:

```
brian@brian-laptop:~$ pon sunysb debug dump logfd 2 nodetach
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sunysb)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
name brlin		# (from /etc/ppp/peers/sunysb)
remotename PPTP		# (from /etc/ppp/peers/sunysb)
10		# (from /etc/ppp/peers/sunysb)
		# (from /etc/ppp/options.pptp)
pty pptp pptp.airnet.stonybrook.edu --nolaunchpppd		# (from /etc/ppp/peers/sunysb)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam tunnel		# (from /etc/ppp/peers/sunysb)
proxyarp		# (from /etc/ppp/options)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe-128		# (from /etc/ppp/peers/sunysb)
noipx		# (from /etc/ppp/options)
speed 10 not supported
using channel 21
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25217), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 22
Using interface ppp0
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Connect: ppp0 <--> /dev/pts/5
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25227), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 23
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25237), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 24
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25245), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 25
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25257), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 26
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25267), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 27
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25277), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
using channel 28
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25287), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 29
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25297), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 30
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25307), status = 0x1
Modem hangup
Connection terminated.
```

What am I doing wrong?

-SMRT

---

### Post by Hclover on 2009-08-31
hey did you get this to work? 

I go to stony brook and I got it to work via the nm-applet pptp package at the nm-applet go to vpn connections > configure vpn> add> calle it Airnet or whatever you want

the gate way is pptp.airnet.stonybrook.edu

turn off all authentication cept mschapv2 use point to point encryption 128bit, turn off bsd and deflate, leave everything everything else on. 

works for me as of first day of classes

---

### Post by Brausen on 2009-08-31
I had the same problem here!

In **Network manager** I make VPN works, but I don't want use GUI. 
Someone have any idea?

---

### Post by Hclover on 2009-09-01
I havent gotten this to work myself but I found this

[http://client.blog.stonybrook.edu/2008/11/14/connecting-to-airnet-using-ubuntu-linux/](http://client.blog.stonybrook.edu/2008/11/14/connecting-to-airnet-using-ubuntu-linux/)

What is wrong with using the GUI?

---

### Post by Brausen on 2009-09-01
It was the steps I followed when I tried make VNC work, but it doesn't work to me. 

Nothing wrong with GUI, it's just a choice. I don't like to depend on it.

---

### Post by Brausen on 2009-09-01
It was the steps I followed when I tried make VNC work, but it doesn't work to me. 

Nothing wrong with GUI, it's just a choice. I don't like to depend on it.

---

