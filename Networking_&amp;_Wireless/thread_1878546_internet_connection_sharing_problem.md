---
title: "internet connection sharing problem"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2011-11-10
I am trying to set up internet connection sharing using Network Manager (GUI) according to this page:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

My laptop connects to the internet via a wireless card.  I am trying to use a crossover cable to use my laptop as a gateway for an older desktop.  My two computers can talk to each other, but the connection to the internet is not working.  The laptop seems to try and use the wired connection to reach the internet if the cable is plugged in (even though I selected eth0 to be shared with other computers in the gui).  I have rebooted multiple times since selecting eth0 as shared.

If I unplug the ethernet cable, my connection to the internet through wlan0 seems to work again.  

I believe I have firehol set up correctly to route network requests from eth0 to wlan0.  Here is my firehol.conf:


# Require release 5 of FireHOL configuration directives
version 5

#iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

#transparent_squid 8080 "root root"
transparent_squid 8080 "proxy root"

# A space separated list of all the IPs on the internet, I trust
#office="my-office-pc.example.com"

# The IP address of this Linux and LAN for the rest of the world
public_ip="192.168.1.69"


# My LAN. Everything is allowed here.
## interface usb0 lan
## 	policy accept	# The default is 'drop'.

interface "usb0 eth0" lan
	policy accept	# The default is 'drop'.


# Make sure the traffic coming in, comes from valid Internet IPs,
# and that is targeting my public IP
#interface wlan0+ internet src not "$UNROUTABLE_IPS" dst "$public_ip"
interface wlan0+ internet
	# Protect me from various kinds of attacks.
	protection strong

	# Public servers.
	server smtp accept
	#server http accept
	#server ftp  accept
	#server ssh  accept src "$office"

	# Make sure idents do not timeout.
	server ident reject with tcp-reset

	# This is also a workstation.
	client all accept
	client samba accept
	#client all accept dst us.archive.ubuntu.com
	#client all accept dst [www.fastlane.nsf.gov](www.fastlane.nsf.gov)
	#client all accept dst [www.nsf.gov](www.nsf.gov)
	#client all accept dst meetings.nsf.gov
	client http accept
	client https accept
	client ssh accept
	client dns accept
	client rdp accept
	client ping accept

	#home Linux server (am2): "00:23:69:df:8f:29"
	#hpdv4 laptop: "78:e4:00:bd:ce:96"
	#dell core2 duo laptop wireless: "00:19:d2:bb:c7:b8"
	#basement windows dell: "00:08:54:00:3F:2A"
	server ssh accept mac "00:19:d2:bb:c7:b8"
	#server nfs accept mac "00:19:d2:bb:c7:b8"
	server ping accept mac "00:19:d2:bb:c7:b8"
	#server http accept mac "00:19:d2:bb:c7:b8"
	server webcache accept mac "00:19:d2:bb:c7:b8"
	server samba accept mac "00:19:d2:bb:c7:b8"

	server ssh accept mac "00:08:54:00:3F:2A"
	server samba accept mac "00:08:54:00:3F:2A"
	server ping accept mac "00:08:54:00:3F:2A"


	#new basement dell
	server ssh accept mac "00:19:B9:25:FC:01"
	server samba accept mac "00:19:B9:25:FC:01"
	server ping accept mac "00:19:B9:25:FC:01"
	client samba accept mac "00:19:B9:25:FC:01"
	client all accept mac "00:19:B9:25:FC:01"

	server ssh accept mac "00:23:69:df:8f:29"
	server samba accept mac "00:23:69:df:8f:29"
	server ping accept mac "00:23:69:df:8f:29"
	client all accept mac "00:23:69:df:8f:29"




# Route the LAN requests to the internet.
#router lan2internet inface usb0 outface wlan0+
router lan2internet inface "usb0 eth0" outface wlan0+

	# Masquerading on outface.
	masquerade

	# Route all requests from inface to outface
	# and their replies back.
	route all accept


## # Route the LAN requests to the internet.
## router lan2internet inface eth0 outface wlan0+
##
## 	# Masquerading on outface.
## 	masquerade
##
## 	# Route all requests from inface to outface
## 	# and their replies back.
## 	route all accept


Is there something else I have to do to convince ubuntu to use wlan0 as the connection to the outside world?

Thanks,

Ryan

---

### Post by SilvaRizla on 2011-11-10
Seems good to me, I spent 3-4 days on the same problem and couldn't get it going.  I think this is a bug in 11.10 but it needs a lot more exposure

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/863906](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/863906)

Please report the bug as affecting yourself and hopefully something will get done

---

