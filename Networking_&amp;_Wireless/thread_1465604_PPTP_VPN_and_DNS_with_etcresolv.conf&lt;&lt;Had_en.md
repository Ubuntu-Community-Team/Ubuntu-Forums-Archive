---
title: "PPTP VPN and DNS with /etc/resolv.conf&lt;&lt;Had enough already!"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by davavanstone on 2010-04-29
Hi
No doubt many of you will have seen threads similar if not the same as this, involving DNS server addresses in resolv.conf changing upon PPTP connection (as it should).

I have a server running karmic desktop specifically designed for usenet downloading with sabnzbd+ and hosting samba shares for Revos with boxee. The problem i have is that i have recently changed my ISP service to an unlimited plan but it heavily caps usenet but leaves VPN at line speed. 

My immediate decision was to route all server traffic through a PPTP VPN using the Giganews VPN vyprvpn.  The service is great for about 5 mins before everything grinds to a halt.  Every site i try to connect to, firefox says "looking up..." my news accounts wont connect and any query over my lan is drastically delayed. VNC takes about 12 seconds before a response with a password prompt yet with without a VPN connection it is near instantaneous.

The installation is a fresh install with only sabnzbd, SSH server and PPTP VPN for network manager installed.

Ive spent hours looking on forums and it seems a very common problem, something to do with network manager updating resolv.conf with the new DNS addresses. 

Setup info.

Ubuntu karmic desktop 64bit kernel 2.6.31-20-generic
Linksys WAG320n with latest firmware
VYPRVPN supplied with giganews (eu1.giganews.com) amsterdam

Ive tried allsorts to get it sorted but all with no avail, hopefully someone would be able to help me, is there any way to force it to use the DNS server addresses supplied with my ISP?

Regards

Dave

---

### Post by davavanstone on 2010-04-30
bump

---

### Post by davavanstone on 2010-05-02
anyone?

---

### Post by davavanstone on 2010-05-13
Seems to be a problem no one can sort, ive searched everywhere, have done a clean wipe and an upgrade to lucid and everything is the same...no dns resolving after vpn connection

---

### Post by jaraco on 2010-07-28
I'm very new to PPTP in ubuntu, but i found in 10.04, I had to *add* the 'usepeerdns' option to my VPN config before it would alter /etc/resolv.conf. Do you have that option in you config? Consider removing it and see if that solves your problem.

---

### Post by davavanstone on 2010-07-28
brilliant, thanx for that, ive moved away from needing a vpn for the minute, but will refer back to this if all changes

Dave

---

