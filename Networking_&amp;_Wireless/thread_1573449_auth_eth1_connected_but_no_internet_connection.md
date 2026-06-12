---
title: "auth eth1 connected but no internet connection"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by l0uismustdie on 2010-09-12
Hello.  I recently moved my HD from one machine to a new machine (Dell Dimension 2400 to Dell Dimension 3000).  Upon starting the new machine and booting Ubuntu 10.04 there was a connection made to auto eth1 (not auto eth0).  I am running a cable modem -> Belkin router -> Dell.  When I attempt to log onto the internet (or ssh into the Dell) there is no success.  Here are the output to some commands I ran in hopes they would help someone decipher what is going on.

```

xxx@xxx:cat /etc/network/interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
#iface eth0 inet static
#    address 192.168.2.3
#    netmask 255.255.255.0
#    gateway 98.218.244.1

``````

xxx@xxx: ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:20:1c:84:fa  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe1c:84fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84687 (84.6 KB)  TX bytes:36616 (36.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53801 (53.8 KB)  TX bytes:53801 (53.8 KB)

``````

xxx@xxx: sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 2536
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:13:20:1c:84:fa
Sending on   LPF/eth1/00:13:20:1c:84:fa
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.3 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 863152717 seconds.

``````

xxx@xxx: tail /etc/log/syslog
Sep 12 18:46:29 lorax kernel: [ 8980.249312] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=50360 DPT=53 LEN=52 
Sep 12 18:46:29 lorax kernel: [ 8980.249356] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=36979 DPT=53 LEN=52 
Sep 12 18:46:29 lorax kernel: [ 8980.250054] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=55097 DPT=53 LEN=45 
Sep 12 18:46:29 lorax kernel: [ 8980.250120] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=36346 DPT=53 LEN=45 
Sep 12 18:46:29 lorax kernel: [ 8980.250173] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=56800 DPT=53 LEN=52 
Sep 12 18:46:29 lorax kernel: [ 8980.250217] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=37735 DPT=53 LEN=52 
Sep 12 18:46:29 lorax kernel: [ 8980.250269] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=36818 DPT=53 LEN=45 
Sep 12 18:46:29 lorax kernel: [ 8980.250314] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=36917 DPT=53 LEN=45 
Sep 12 18:46:29 lorax kernel: [ 8980.250362] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=40152 DPT=53 LEN=52 
Sep 12 18:46:29 lorax kernel: [ 8980.250406] Shorewall:OUTPUT:REJECT:IN= OUT=eth1 SRC=192.168.2.3 DST=192.168.2.1 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=7374 DF PROTO=UDP SPT=36465 DPT=53 LEN=52 

```I have also tried resetting my router to the factory defaults because I thought perhaps it was tying 192.168.2.3 to the previous machines MAC address or something like this.

---

### Post by Iowan on 2010-09-12
When you moved the HD, it probably kept the interface info from the first install. You *should* be able to purge the old info from */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by l0uismustdie on 2010-09-13
Well I commented everything in that file out and did a networking restart but that didn't seem to have any effect.  I'm not sure what you mean by "purge" the information other than delete it and is that going to change anything if I just commented everything out?

---

### Post by Iowan on 2010-09-13
Deleting or commenting out *should* have the same effect...
Did the file contents change after you restarted?
If there was a definition for eth1, you might be able to make it eth0... but what you did *should* work... :confused:

---

### Post by l0uismustdie on 2010-09-13
Yeah so you were right.  I restarted the machine and the file was updated...originally I was just doing a networking restart.  Interesting though that it generated the same text that was already in the file.  Oh well, it works.  Thanks for your help.

---

