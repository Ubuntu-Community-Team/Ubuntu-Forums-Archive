---
title: "Karmic server, wvdial and 3G USB modem: no default route"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by frankvw on 2010-02-28
Hi everyone,

In an attempt to get something that, well, you know, just works... I migrated a laptop to Karmic server today. Which works fine, except for one thing: when I use wvdial and a Huawei E160g USB modem to connect to the Internet (which is the only option out here in the sticks where I live) no default gateway is set. When I add one manually everything is fine, except that the default gateway keeps disappearing after a while (at irregular intervals, as far as I can see). Nothing appears in *any* logfile that even mentions the default route, let alone a reason for its magical vanishing trick.

My wvdial.conf is fairly pedestrian:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem = /dev/ttyUSB0
Modem Type = USB Modem
Baud = 460800
ISDN = 0
Phone = *99#
New PPPD = yes
Stupid Mode = yes
Username = user
Password = pass
```

After wvdial connects, pppd tells me that it

```
"Could not determine remote IP address: defaulting to 10.64.64.64
```

Which is fine - it always has for as long as I can remember and it has never been a problem.

So not being able to get onto the Internet for lack of a default gateway, I add one manually:

```
sudo route add default gw 10.64.64.64
```

and then everything works perfectly - until the default gateway just disappears and I have to set it manually again!

What's going on here? I'm stumped. And the mighty Googlebrain doesn't seem to know, either.

How do I get wvdial & friends to set the correct default route upon connecting? Given the fact that without a default route a PPP connection to a remote network is little use, I would expect this to be a standard feature and not something that I'd have to script a work-around for myself. But then, I have been wrong before. :-)

Secondly, and more importantly, *why does my default route keep disappearing without a trace*?

Any and all suggestions to point me into the right direction would be greatly appreciated!

// Frank

---

### Post by Skinner_au on 2010-03-30
Did you ever discover a solution to this? I'm about to setup an E160g on an Ubuntu Server install (or perhaps a similar X-less distro) and would love to know of any pitfalls. The USB modem will be the default gateway on this machine also.

Thanks

Sk

---

### Post by Nisal on 2010-03-30
well im also having unsloved problems with HSDPA.. and wating for 10.04 stable to upgrade coz i saw that one developer had said they had fixed mobile broadband issues in 10.04

---

### Post by frankvw on 2010-03-30
> **Skinner_au said:**
> Did you ever discover a solution to this? I'm about to setup an E160g on an Ubuntu Server install (or perhaps a similar X-less distro) and would love to know of any pitfalls. The USB modem will be the default gateway on this machine also.

Yes, I did. It turned out that the problem originated between the keyboard and the chair. :-)

In the hope that it might be useful to you (seeing as you're about the do what I've done already) and for what it's worth, I include the relevant entries in my sysadmin logbook here. Share and enjoy. ;) The solution to the problem that I originally experienced (disappearing default route) can be found under "Trouble" in the first entry below.

```

Date:	28 February 2010

What: 	Installed wvdial

Why:	To provide 3G connectivity via USB modem

How:	Installed wvdial plus dependencies from packages. Ran wvdialconf to
	create the following /etc/wvdial.conf:

		[Dialer Defaults]
		Init1 = ATZ
		Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
		Modem = /dev/ttyUSB0
		Modem Type = USB Modem
		Baud = 460800
		ISDN = 0
		Phone = *99#
		New PPPD = yes
		Stupid Mode = yes
		Username = user
		Password = pass

		[Dialer pin]
		;Init1 = AT+CPIN=1234

	(Note that the dialer PIN is not being used at present. This directive
	has been included as a means of documentation for future reference.)

	Then it turned out that wvdial overwrites /etc/resolv.conf. Normally
	this is desirable behavior, but in this case a local DNS runs on the
	same host which is authorative for the local network, and forwards
	other DNS queries to the ISP's external DNS'es. This requires that
	/etc/resolv.conf refer to localhost.

	Adding the option

		Auto DNS = no

	to /etc/wvdial.conf and removing the option 'usepeerdns' from
	/etc/ppp/peers/wvdial solved this problem.

Trouble: During the installation of Ubuntu Karmic server, an IP address of
	192.168.4.100 had been assigned to eth0, with the same IP address
	(192.168.4.100) as the default gateway for the time being. When
	wvdial spawned pppd, this default gateway was not overwritten but
	left in place, and no default gateway to ppp0 was set. Manually
	entering a default gateway to ppp0 with the command

	sudo route add default gw 10.64.64.64

	worked, but only temporarily, until the previous situation
	reasserted itself. Removing the default gateway from eth0 by
	means of editing /etc/network/interfaces solved the problem.

	There is also a conflict with bind9 on the same host as an
	authorative name server for the inner network.

Notes:	The standard out-of-the-box wvdial operation creates a resolv.conf
	file that overwrites a previous one, which means that localhost
	will not use a local instance of bind to resolve local hostnames.
	This will have to be looked into at a future date. 

```

```

Date:	1 March 2010

What: 	Set up Internet connection sharing and firewall

Why:	After migration of system to Karmic Server a proper internet feed
	with adequate security has to be provided to the local network,
	which was one of the main reasons for said migration.

How:	Installed wvdial to provide ppp0 as the outside interface (see
	corresponding logbook entry on wvdial installation).

	Edited /etc/sysctl.conf to uncomment the line:

		#net.ipv4.ip_forward=1

	to enable IPv4 packet forwarding. Restarted networking. That did
	not very much (why??) so enabled forwarding manually with:

		echo 1 > /proc/sys/net/ipv4/ip_forward

	After the next reboot the edit of sysctl.conf appeared to be in
	effect, though, so manually enabling forwarding during normal
	operation is apparently not required.

	Enabled basic (VERY basic) NAT as follows:

		iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

	which works, after manually establishing a 3G connection on ppp0,
	but offers no security or automation at all.

	A firewall script was then cobbled together from several sources,
	including an old KissMyFirewall script (a project now defunct),
	some FireWallBuilder output, and suggestions obtained from the IT
	dept. of the Dutch ministry of Foreign Affairs. (Don't ask.)

	The finalized firewall script was installed as /etc/firewall.sh,
	chowned root:root and flagged 700, then invoked from /etc/rc.local.
	Crude but effective.

Trouble: Not really. IPtables can be a bit daunting at times - nothing that
	a bit of study won't fix. 

Notes:	The usual scripts to up and down networks seem to be somewhat broken
	in Karmic. Apparently they are now considered obsolete and superceded
	by the "upstart" process management daemon. As as result, the command

		service networking restart

	croaks with a broken (!) error message. However,

		/etc/init.d/networking restart still works. 

	Figuring this out took a while.

	Because now "ufw" is supposed to be the userland interface of
	choice for iptables, there is no /ec/init.d/iptables script
	anymore, just an /etc/init.d/ufw one. A dubious improvement IMO.


```

```

Date:	6 March 2010

What:	Setup of Squid as a transparent proxy

Why:	Proxy service without the need for any changes at the client end
	because bandwidth is at a premium (using 3G in South Africa sucks)

How:	Configure Squid in httpd accelerator mode (so as to accept non-proxy
	requests) and redirecting through-traffic on port 80 via squid on port
	8080. See www.debian-administration.org/articles/71 for a good
	manual.

	1. Edited /etc/squid/squid.conf as follows:

	# Squid normally listens to port 3128
	# http_port 3128

	# (But we use 8080 on localhost and eth0 only in transparent mode
	# FvW 2010-03-06)
	http_port 127.0.0.1:8080 transparent
	http_port 192.168.4.100:8080 transparent

	Find the following line:
		# Example rule allowing access from your local networks.
	and edit the examples as follows:

	#acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
	#acl localnet src 172.16.0.0/12 # RFC1918 possible internal network
	acl localnet src 192.168.4.0/24 # RFC1918 internal network

	Then scroll down, past the acl safe_ports list, to where it says:

	# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

	Edit that section as follows:

	http_access allow localnet
	http_access allow localhost


	While we're at it, add ad filtering in squid by installing AdZapper:

	apt-get install adzapper

	and then add the following line to your /etc/squid/squid.conf :

	redirect_program /usr/bin/adzapper.wrapper


	Finally, add the following line to the firewall script:

	  $IPTABLES -t nat -A PREROUTING -i $INNER_IF -p tcp --dport
	            -j REDIRECT --to-port 8080

	Restart firewall and squid.


Trouble: Not really. A lot of manuals are obsolete as of squid 2.6, and
	with post-2.6 versions some things have changed, which can easily
	lead to some confusion. Caveat sysadmin. :-)

Notes:	An earlier squid configuration as a transparent proxy on CentOS 4/5
	used a lot of directives which are now deprecated, or which have
	been included by default in the config file that comes with Ubuntu
	Karmic. So don't bother fiddling with the old config, it's a waste
	of time.


```

The IPtables firewall is a fairly conventional one, using eth0 as a fully trusted interface and ppp0 as its "outer world" interface, performing masquerading as necessary. I am NOT going to publish my firewall configuration for reasons that will be obvious to the educated. Building the firewall is left as an exercise for the reader. :)

I have been using the USB modem, wvdial, the IPtables firewall and a transparent squid proxy for weeks now without a single hiccup. Since 3G bandwidth is scarce and expensive in my neck of the woods, the 10-20% savings achieved with Squid make sense in my situation. Speaking of which: my internal LAN network address happens to be 192.168.4.0/24 as reflected in the above configuration.Your mileage may vary.

One final note on AdZapper: I notice it comes up with too many false positives. A legitimate image like "topbanner.jpg" on my own websites gets zapped. The rules in AdZapper are hardcoded in on of the Perl scripts, pretty stale (from 2008 or so) and not easy to maintain. I've discontinued using AdZapper for now until I either come up with a better rule set or find a better ad blocker for Squid.

Good luck!

// FvW

---

### Post by frankvw on 2010-03-30
> **Nisal said:**
> well im also having unsloved problems with HSDPA.. and wating for 10.04 stable to upgrade coz i saw that one developer had said they had fixed mobile broadband issues in 10.04

Before I installed Karmic Server, I ran Jaunty Desktop on the same system, using the same USB modem and the same wireless provider - in other words, all I did was migrate from Jaunty Desktop to Karmic Server. And that solved all the problems I had with wireless Internet via USB. Before the upgrade the modem would loose its connection with annoying regularity; it would stop routing data for no apparent reason, and sometimes the network manager would disappear entirely from the task bar. Now all I do is run wvdial and the firewall stuff etc. from scripts (the machine doesn't have an X desktop anymore) and all is well.

// FvW

---

