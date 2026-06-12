---
title: "DHCP problem"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by kschenke on 2009-02-17
Hello,

after reading the web I now try the forum:
I had dhcp running on my machine but now it is failing. Here all I have as background info:

/etc/dhcp
```
INTERFACES=eth0
```

/etc/dhcp3-server
```
INTERFACES=eth0
```

/etc/dhcp3/dhcpd.conf
```

subnet 192.168.123.0 netmask 255.255.255.0 {
	option domain-name "my-test-domain.com";
	range 192.168.123.201 192.168.123.220;
	default-lease-time 86400;
	max-lease-time 86400;
	option routers 192.168.123.254;
	option ip-forwarding off;
	option broadcast-address 192.168.123.255;
	option subnet-mask 255.255.255.0;
	option ntp-servers ntps1-0.cs.tu-berlin.de;
	option domain-name-servers 192.168.123.4;
	option netbios-name-servers 192.168.123.4;        
	}

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.123.4
netmask 255.255.255.0
gateway 192.168.123.254
network 192.168.123.0

auto eth0

```

When I start I get the error in /var/log/syslog:
```

No subnet declaration for eth0 (192.168.123.4).
** Ignoring requests on eth0.  If this is not what
you want, please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface eth0 is attached. **

```

What is wrong - who can see what I can't see ?
thanks

---

### Post by Iowan on 2009-02-17
My DHCP server does not have the files */etc/dhcp* or */etc/dhcp3-server*. My subnet declaration is similar - but I don't have the second ```
option subnet-mask 255.255.255.0;
``` 

Is this on a server machine - or does it use Network Manager - which seems to have problems with static addresses (unless something has changed recently)?

---

### Post by jonobr on 2009-02-17
could you post results to ifconfig

It may be just that your eth0 is down

---

### Post by kschenke on 2009-02-18
Hello, thanks for the comments, here my ifconfig:
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:1D:09:23:6A:C2
          inet Adresse:192.168.123.4  Bcast:192.168.123.255  Maske:255.255.255.0
          inet6 Adresse: fe80::21d:9ff:fe23:6ac2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453146 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:251745165 (240.0 MB)  TX bytes:72776834 (69.4 MB)
          Interrupt:17

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416693 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:125773460 (119.9 MB)  TX bytes:125773460 (119.9 MB)

```

---

### Post by kschenke on 2009-02-18
> **Iowan said:**
> 
Is this on a server machine - or does it use Network Manager - which seems to have problems with static addresses (unless something has changed recently)?

How can I answer this ?

---

### Post by jonobr on 2009-02-19
Hello


I cut and paste your dhcpd.conf statements and placed them into my conf file.
I removed all of my declarations or commented them out.
I started dhcp3

```
sudo /etc/init.d/dhcp3-server start
```

and it started no problem.....


Heres the dhcp.conf file I used, You will see the comment where I added in your declarations, and you will see I changed IP addresses a bit to match my network config


```

/etc/dhcp3$ cat dhcpd.conf 
ddns-updates off;
option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;
#option subnet-mask 255.255.255.0;
#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.101.0.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.



#Heres where I added in your declerations




subnet 10.10.0.0 netmask 255.255.0.0 {
        option domain-name "my-test-domain.com";
        range 10.10.10.50 10.10.10.55;
        default-lease-time 86400;
        max-lease-time 86400;
        option routers 10.10.10.250;
        option ip-forwarding off;
        option broadcast-address 10.10.255.255;
        option subnet-mask 255.255.0.0;
        option ntp-servers ntps1-0.cs.tu-berlin.de;
        option domain-name-servers 192.168.123.4;
        option netbios-name-servers 192.168.123.4;
        }


#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host mc1 {
# hardware ethernet 00:40:9E:01:04:32;
#fixed-address 10.101.0.11;
#filename "pxelinux.0";
#  server-name 10.101.0.14;
#}

#host mc2 {
#  hardware ethernet 00:40:9E:01:04:33;
#  fixed-address 10.101.0.12;
#  filename "pxelinux.0";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}



```

---

### Post by kschenke on 2009-02-19
Sorry, but it do not work: I copied the above dhcp.conf, replaced some IPs and I got a "fail". Here my used version:

```

ddns-updates off;
option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;
#option subnet-mask 255.255.255.0;
#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.101.0.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.



#Heres where I added in your declerations




subnet 192.168.123.0 netmask 255.255.255.0 {
        option domain-name "my-test-domain.com";
        range 192.168.123.100 192.168.123.200;
        default-lease-time 86400;
        max-lease-time 86400;
        option routers 10.10.10.250;
        option ip-forwarding off;
        option broadcast-address 192.168.123.255;
        option subnet-mask 255.255.255.0;
        option ntp-servers ntps1-0.cs.tu-berlin.de;
        option domain-name-servers 192.168.123.4;
        option netbios-name-servers 192.168.123.4;
        }


#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host mc1 {
# hardware ethernet 00:40:9E:01:04:32;
#fixed-address 10.101.0.11;
#filename "pxelinux.0";
#  server-name 10.101.0.14;
#}

#host mc2 {
#  hardware ethernet 00:40:9E:01:04:33;
#  fixed-address 10.101.0.12;
#  filename "pxelinux.0";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```

Maybe this helps:
I started first with Webmin to manage the DHCP server
Than I used GDHCPD

Both did not help me here.

Is there an easy GUI interface for DHCP which may check deeper the system what may have failed?
Is there a deep debug mode when starting the DHCP server to see what is wrong ?

THANKS !

---

### Post by jonobr on 2009-02-19
The only other thing I would recommend is disable ipv6 if your not using it.
Im thinking that may be hosing it up on you.

Our configs are the same and our interfaces are provisioned like wise with the exception of IPV6.

Heres my ifconfig


```
eth0      Link encap:Ethernet  HWaddr 00:44:75:a3:89:99  
          inet addr:10.10.10.14  Bcast:10.10.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879092 errors:0 dropped:0 overruns:1 frame:0
          TX packets:522652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:679343070 (679.3 MB)  TX bytes:59135470 (59.1 MB)
          Interrupt:21 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

```
 Notice I removed all IPv6 (which improved my web performance)

---

### Post by jonobr on 2009-02-19
One other point,

I would stay away from a GUI for the moment,
your looking in the right places, (syslog and output errors from starting the processes) 

IMO, when you add a gui, in some cases your making things easier, however, you are adding a layer between you and the application.

That layer may suppress some clues which could help you figure the problem, or may report it in a way, that doesnt make sense.

Im not anti-gui, I just think your doing fine right now with how your investigating this

---

### Post by kschenke on 2009-02-19
> **jonobr said:**
> One other point,

I would stay away from a GUI for the moment,
your looking in the right places, (syslog and output errors from starting the processes) 

IMO, when you add a gui, in some cases your making things easier, however, you are adding a layer between you and the application.

That layer may suppress some clues which could help you figure the problem, or may report it in a way, that doesnt make sense.

Im not anti-gui, I just think your doing fine right now with how your investigating this

I agree. But I missed a debugging option in DHCPD to see, on which line or so the error occures. So sometimes GUI is written by an expert and write better results.

I checked this regarding IPv6: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by jonobr on 2009-02-19
When you disable ipv6 , this line should disappear from your ifconfig

```
inet6 Adresse: fe80::21d:9ff:fe23:6ac2/64 Gültigkeitsbereich:Verbindung

```

---

### Post by kschenke on 2009-02-20
I detected interesting things:

1) I started with an empty dhcpd.conf
2) I started GDHCPD and filled in what the tooltip/help suggested
3) I got this simple configuration to run (!!)
4) I checked the difference and found the line ```
interface eth0;
```
5) I added the line in my old dhcpd.conf 
6) I could start the old configuration with GDHCPD and other devices, network was running, leases were taken. But I did not find a way to start it while booting. I assume I started dhcpd
7) I could not start the "normal dhcpd3" system (not from Wemin or Boot-Up Manager) Even not when I tried to stop dhcpd from GDHCPD
Error messages from dhcpd3 were the same as before even when adding a line "interface eth0". So I was assuming: DHCPD3 can not bind to eth0 because DHCPD is already.

**Conclusion:**
[LIST]
[*]Could it ever be I have dhcpd and dhcpd3 in parallel installed ?
[*]Both using the same dhcpd.conf ?
[/LIST]

**Questions:**
[LIST]
[*]How do I check dhcpd or dhcpd3 installed ?
[*]How would I remove each of them (apt-get seems not to work for that) ?
[*]IS there a way to start dhcpd3 with GDHCPD ?
[/LIST]

thanks for having a thought on this

---

### Post by jonobr on 2009-02-20
This is just a guess, but if you two DHCP programs installed and using the same config in the same location, Im thinking if one is started by the system and then you go to start dhcp3-server, it bitches as the other one is already running.

Im thinking if you go to /etc/init.d after bootup and check the status of dhcpd
(sudo /etc/init.d/dhcpd status)
it will say started.

If you stop it (sudo /etc/init.d/dhcpd stop)

and then start (sudo /etc/init.d/dhcp3-server start)You may see that that is the problem.

To see whats installed , go to synaptic, and type in the search dhcp
you should see all matches displayed,

the ones with a green box are installed.

---

### Post by kschenke on 2009-02-21
Hello jonobr,

thanks for the ideas.
I tested it, dhcpd is not working or installed. But I found someting other special:

```

sudo /etc/init.d/dhcp3-server start

```
[COLOR="Red"]fails ![/COLOR]

```

sudo dhcpd3 -f -d eth0

```
[COLOR="Lime"]works !!![/COLOR] leases are taken !!!

So the configuration seems to be OK, there are two ways to start the server and both have a difference outside the config file.

What difference is it ?

---

### Post by kschenke on 2009-04-03
> **kschenke said:**
> 
...........
```

sudo /etc/init.d/dhcp3-server start

```
[COLOR="Red"]fails ![/COLOR]

```

sudo dhcpd3 -f -d eth0

```
[COLOR="Lime"]works !!![/COLOR] 
...........


Does anybody has an idea what is going on here ?

---

