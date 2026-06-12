---
title: "Network-Manager Problem DHCP Lease (wrong dhclient usage?)"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Muschl on 2010-02-24
if the network (lan or wlan) link comes ready the network manager obtains no dhcp ip address:

hostname removed from log:
```

Feb 24 19:49:49  NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Feb 24 19:49:49  NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Feb 24 19:49:49  NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 24 19:49:49  NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 24 19:49:49  NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Feb 24 19:49:49  NetworkManager: Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 24 19:49:49  NetworkManager: <info>  dhclient started with pid 21139
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Feb 24 19:49:49  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb 24 19:49:49  dhclient: Internet Systems Consortium DHCP Client V3.1.2
Feb 24 19:49:49  dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb 24 19:49:49  dhclient: All rights reserved.
Feb 24 19:49:49  dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb 24 19:49:49  dhclient: Usage: dhclient [-1dqrx] [-nw] [-p <port>] [-s server]
Feb 24 19:49:49  dhclient:                 [-cf config-file] [-lf lease-file][-pf pid-file] [-e VAR=val]
Feb 24 19:49:49  dhclient:                 [-sf script-file] [interface]

```

if i run the dhclient without options it becomes a dhcp lease address:

```

:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 20927
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:1b:77:04:8a:7c
Sending on   LPF/wlan0/00:1b:77:04:8a:7c
Listening on LPF/eth0/00:16:d3:b2:78:a3
Sending on   LPF/eth0/00:16:d3:b2:78:a3
Listening on LPF/vboxnet0/0a:00:27:00:00:00
Sending on   LPF/vboxnet0/0a:00:27:00:00:00
Sending on   Socket/fallback
DHCPREQUEST of 192.168.178.40 on wlan0 to 255.255.255.255 port 67
send_packet: Network is down
receive_packet failed on wlan0: Network is down
DHCPREQUEST of 192.168.178.47 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 7
DHCPACK of 192.168.178.47 from 192.168.178.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.178.47 -- renewal in 379059 seconds.


```

---

### Post by rockorequin on 2010-02-24
I'm getting the same thing after an update of network-manager to 0.8-0ubuntu4~nmt4~karmic.

Which version of network-manager are you using?

The problem is that nm is running dhclient3 with (eg):

/sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-d3d99611-207b-4eb8-95d7-2f2ecc7ede1c-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

and dhclient doesn't like the "-4" option.

---

### Post by alexhemp on 2010-02-25
Same problem!

All of symtoms are same!

dhcp3-client is incompatible with network-manager 0.8

---

### Post by rockorequin on 2010-02-25
I was using the wrong PPA for network-manager. See [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394/comments/71](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394/comments/71)

I've installed NM 0.8 from that PPA ([https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)) and now it is working fine.

---

### Post by Muschl on 2010-02-26
thx rockorequin,

your solution fixed my problem to.

---

### Post by Majino on 2010-02-26
got the same problem... could someone tells me how to remove this buggy version of network manager and install the good one? :D thanks a lot!

---

### Post by Majino on 2010-02-26
> **Majino said:**
> got the same problem... could someone tells me how to remove this buggy version of network manager and install the good one? :D thanks a lot!

ok i managed this... but... which version of nm do you guys have?? i'm with 0.7.998 ... is the latest?? :D thanks!

---

### Post by mtrudel on 2010-02-26
The incompatibility between 0.8 (actually, the current latest Git snapshot from upstream) and the current dhclient is indeed an issue with the current state of the NM trunk PPA. For those wondering, it's to attempt to improve support for IPv6. Thanks for reporting this again!

Note that the trunk PPA is used to run daily builds of NetworkManager against Git, and thus such issues may arise from time to time -- the trunk PPA is intended to help with testing new stuff of fixes that we get from upstream.

I'm going to try and keep the other PPA ([http://launchpad.net/~network-manager/+archive/ppa](http://launchpad.net/~network-manager/+archive/ppa)) up to date with "known-good" versions of recent builds of NetworkManager.

/ Matt

---

### Post by webheadjunky on 2010-02-27
Hi there
I have no wired or wireless access on my laptop following recent nm update
Currently posting this via my desktop
Grateful if someone could tell me how to fix network manager issue if I can't download new files
Cheers
Raaj

---

### Post by rockorequin on 2010-02-27
If network manager isn't getting a connection, you should still be able to connect on one of your network interfaces by manually running the command:

 sudo dhclient

or, if you now the interface name, eg eth0:

 sudo dhclient eth0

---

### Post by webheadjunky on 2010-02-28
Great Stuff!
Working again
Thanks very much!
:p

---

### Post by hfdragon on 2010-03-04
thanks mtrudel !
I switched ppa and forced a downgrade, and now it's ok again :))) :KS

---

### Post by LukeKendall on 2010-05-19
I've just setup a new machine, in an unusual way (to avoid having to reinstall hundreds of packages and configure all the mail and samba and print etc. etc. again), by doing something risky:

1) Install a barebones Ubuntu 9.10 from CD
2) Copy *all* files from old PC also running 9.10 to the new
   (yes, even all of / including /etc!)
3) Fixed /etc/fstab and grub config and /etc/hosts to use the
   new hard drive arrangements and local IP addresses
4) Eventually got ethernet working, after realising eth0's name
   had changed to eth1 on the new PC

Then things get weird.  I read all the NetworkManager ubuntu documentation, but there was precious little in there to actually work out what it's doing under the hood and therefore diagnose what's wrong.  After a lot of effort I could get NM to try to connect and after about 40 seconds, fail.  It seemed to take the time that it took dhclient to fail if I ran it manually from the command line, like so::

```

    # dhclient
    Internet Systems Consortium DHCP Client V3.1.2
    Copyright 2004-2008 Internet Systems Consortium.
    All rights reserved.
    For info, please visit http://www.isc.org/sw/dhcp/

    Listening on LPF/eth1/e0:cb:4e:51:ff:23
    Sending on   LPF/eth1/e0:cb:4e:51:ff:23
    Sending on   Socket/fallback
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
    No DHCPOFFERS received.
    No working leases in persistent database - sleeping.

```
Note that the network would work fine if I ran these commands as root:

```

# ifconfig eth1 inet 192.168.1.102 netmask 255.255.255.0 broadcast 192.168.1.255
# route add default gw 192.168.1.1

```

I purged my old NM packages, and reinstalled the ones from the  PPA ppa:network-manager/trunk. What happens for me now is that NM tries to connect, and just sits there forever trying, according to the status bar.

On the plus side, if I run dhclient manually now, it instantly gets a correct lease and the network is up.

Because I can't find a way to discover what NM is actually doing when it tries to connect (if I try running it from the command line with debug enabled, it just complains that NM is already running), I've decided the package jut isn't worth the trouble, and will just change /etc/network/interfaces to run dhcpc itself, and tell NM that it should manage nothing.

I've done lots of googling to try to fix the problem, and NM just seems too much a black box, not diagnosable, so I'm scrapping it.

From the logs on my firewall/router, it looks like NM links to it on port 137 (so I assume it's asking for a DHCP lease), but it never seems to get one.  Whereas now if I run dhclient manually, I do get one. 

For what it's worth, here are my /etc/network/interfaces file before I got rid of NM:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Try adding this:
# The primary network interface
auto eth1

```

/etc/NetworkManager/nm-system-settings.conf before I changed the managed to false:

```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```
luke

---

### Post by Phezz on 2010-06-01
I'm having a strange problem - seems related -

I have two interfaces - eth0 and eth1.  

Both DHCP - addresses only.  
eth0 is set for local route only.
eth1 will use the routes given by DHCP (default)

eth0 works fine - but eth1 never succeeds at dhcp.  I see a request go out in wireshark with my MAC address, but network manager declares failure.

dhclient eth1 works like a charm

eth0 uses DHCP (to a different server on a different network) no problems

---

