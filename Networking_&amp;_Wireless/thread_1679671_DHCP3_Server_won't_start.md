---
title: "DHCP3 Server won't start"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by eaglecoth on 2011-02-01
[B]Hi,

I have followed the ubuntu guide for setting up a dhcp3-server server for my internal network,  I have installed dhcp3-server, configured it refuse to start, here are some background:

**This is my /etc/default/dhcp3-server:**

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

**This is from my ifconfig:**

eth1      Link encap:Ethernet  HWaddr 00:50:bf:db:49:16
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fedb:4916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42971806 errors:7 dropped:0 overruns:0 frame:0
          TX packets:33846980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3000265991 (3.0 GB)  TX bytes:1547648482 (1.5 GB)
          Interrupt:12 Base address:0xdc00

**This is my /etc/dhcp3/dhcpd.conf:**


# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 81.26.226.3, 81.26.226.2;
option domain-name "mydomain.com";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.40 192.168.0.90;
range 192.168.0.201 192.168.0.245;
}

**And below is a tail from the syslog when I try to start it:**

Feb  1 16:11:34 server dhcpd: Wrote 0 leases to leases file.
Feb  1 16:11:34 server dhcpd: Can't bind to dhcp address: Address already in use
Feb  1 16:11:34 server dhcpd: Please make sure there is no other dhcp server
Feb  1 16:11:34 server dhcpd: running and that there's no entry for dhcp or
Feb  1 16:11:34 server dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Feb  1 16:11:34 server dhcpd: are not running HP JetAdmin software, which
Feb  1 16:11:34 server dhcpd: includes a bootp server.


So my question is, how can I further trace the error?


Any help is apprichiated

/Eaglecoth

---

### Post by eaglecoth on 2011-02-01
**In addition to the above,  here is my /etc/inetd.conf:**


#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
swat            stream  tcp     nowait.400      root    /usr/sbin/tcpd  /usr/sbin/swat


I don't have any HP jetdirect software installed. And as far as I know there is no other DHCP server running (I have tried to let a client get ip from DHCP without success)

---

### Post by SeijiSensei on 2011-02-01
As the error says, dhcpd cannot bind to the port it uses (67).  

One possibility is that eth1 is not configured.  Is there an eth1?  Is it configured with a static address, etc.?

That would be my first guess, though I suppose it's possible that you tried starting dhcpd twice, and already have one instance running.  Try running "ps ax | grep dhcp" and see if anything turns up.

---

### Post by eaglecoth on 2011-02-01
**Here is the return of the ps run: **
ps ax | grep dhcp
 7654 pts/0    R+     0:00 grep --color=auto dhcp

i.e. no dhcpd running

**eth1 is configured and running:**


>ping 192.168.0.200
PING 192.168.0.200 (192.168.0.200) 56(84) bytes of data.
64 bytes from 192.168.0.200: icmp_seq=1 ttl=64 time=2.47 ms


**eth0 is also cofigured and connected the the net:**

>ping av.com
PING av.com (68.180.206.184) 56(84) bytes of data.
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=52 time=203 ms

---

### Post by eaglecoth on 2011-02-01
Hi,

Sorry I didn't reply your first question:

Yes both eth0 and eth1 are configured with static-addresses. Eth0 is internet connected and belongs to a different subnet, Eth1 is configured outside of the proposed range for the dhcpd

---

### Post by SeijiSensei on 2011-02-01
I haven't set up a dhcpd instance in a while now.  On my CentOS server here, running 3.0.5, I include the interface on the command line:

/usr/sbin/dhcpd eth1

to force it to listen on eth1.  I don't know how that fits with the INTERFACES directive, but you might give it a try.  I don't have an INTERFACES directive in my dhcpd.conf, though.

---

### Post by eaglecoth on 2011-02-01
Hi,

Manual start of the dhcpd3 yields the same error:

**>sudo /usr/sbin/dhcpd3 eth1**

Internet Systems Consortium DHCP Server V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 leases to leases file.
Listening on LPF/eth1/00:50:bf:db:49:16/192.168.0/24
Sending on   LPF/eth1/00:50:bf:db:49:16/192.168.0/24
Can't bind to dhcp address: Address already in use
Please make sure there is no other dhcp server
running and that there's no entry for dhcp or
bootp in /etc/inetd.conf.   Also make sure you
are not running HP JetAdmin software, which
includes a bootp server.

---

### Post by eaglecoth on 2011-02-01
Hi again,

So in order to isolate the problem,  could we now rule out that the configuration of the dhcpd3 server is correct and that the error must be something of the following:

1.  There is some dhcp-server running on the network (on another machine or device)

If this is the case, how could I locate it?

2. There is something on the ubuntu-machine blocking execution.

If this is the case, how could I locate such a process?

Is there anyway you can get more debugging info out of the dhcpd3 binary when it starts?



Thanks for your help

/Eaglecoth

---

### Post by eaglecoth on 2011-02-01
Hi,


If I disconnect all other machines from the 192.168.0.x network and try to restart the dhcpd3 server.  Then I should be able to rule out if it is a problem on the machine or if there is some external source disturbing right?



/Eaglecoth

---

### Post by SeijiSensei on 2011-02-01
Another machine running dhcp won't cause this error; dhcpd can't bind to the port on your machine itself.

Another way this error can occur is if you're running an iptables firewall and don't have ports 67 and 68 open at all.  If you are running iptables, make sure you have a pair of rules like this:

```

iptables -A INPUT -i eth1 -p tcp --dport 67:68 -j ACCEPT
iptables -A INPUT -i eth1 -p udp --dport 67:68 -j ACCEPT

```

These need to come before any default DENY or REJECT rules.  (If --dport doesn't work for udp, use --destination-port instead.)

---

### Post by eaglecoth on 2011-02-06
Hi,
 
 
I am using a ufw configuration,  how could I turn the iptables rules you've just posted above into ufw-lines?

Or is there a way to manually insert these rules into some file?
 
 
/Eaglecoth

---

### Post by SeijiSensei on 2011-02-07
Can't help there; I roll my own iptables rulesets.  You might want to consult [this](https://help.ubuntu.com/community/UFW#Enable%20and%20Disable).

---

