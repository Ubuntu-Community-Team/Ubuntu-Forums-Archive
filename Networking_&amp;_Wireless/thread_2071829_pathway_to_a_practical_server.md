---
title: "pathway to a practical server?"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-10-16
10.04 server LTS 64 bit.
Having some problems getting the LAN on the internet, probably incorrect forwarding. I'll make a thread for that. I'd like some help choosing which packages to use to get me where I need to go. 
internet--adsl modem/router--eth0(dhcp)--server--eth1(static)--switch--clients (LAN)
The big picture: 3 classes of users to give different access:net admin, teachers and staff, students. Services: dhcp for LAN, samba file server, potential email server to support potential website, dns cache, ssh access, a reasonable level of security for both the server and the windows clients. Client machines will have anti-virus installed, but some filtering for the student users will be needed. 
Package candidates: dhcp3, ufw, bidnd9, dnsmasq, isc dhclient. SSH server, LAMP, DNS server, email server, and Samba server packages installed with core o/s. Webmin? The idea kind of makes me nervous...There will be only windows clients to support.
Biggest concern is at the level of port forwarding , dhcp, dns cache, and firewall. Several of the packages installed have overlapping, perhaps conflicting purposes. Don't want to get past that level to find that something is ok initially won't work well with the next level packages (like Samba). Just want to not shoot myself in the foot (again). Of course, being a novice, ease of configuration reduces the chance for (more) errors.
BTW I realize that some of the desired services (email, website, ssh remote access) will require services to deal with the lack of a static ip (no-ip or whatever), so will happen at a later date. Just want to keep that door open for now.
Not seeking specific configuration of packages here, just guidance on package selection/integration.--Thanks

---

