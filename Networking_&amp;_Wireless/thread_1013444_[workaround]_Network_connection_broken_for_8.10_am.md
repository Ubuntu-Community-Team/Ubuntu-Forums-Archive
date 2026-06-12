---
title: "[workaround]: Network connection broken for 8.10_amd64 with static configuration."
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by cdrigby on 2008-12-16
I'm posting this here in the hopes that it might help someone else who, like myself, needs to use a static ethernet configuration on a wired interface under 8.10. Motivations for this vary, but in my case this is my game server, it is behind a firewall, and I've always done this rather than figure out how to get the DHCP server of the firewall to assign the same ipv4 settings based on the MAC of this system's NIC. There is probably more than one way to skin this particular cat, but this is what worked for me.

This is launchpad bug #259214 ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214)). Another work-around is discussed there that involves steps taken under NetworkManager itself.

**Scenario:** Desktop host with two wired ethernet NICs, one of which (eth0) is physically connected and is assigned a static IP, netmask, default gateway and DNS servers during installation using the 8.10 alternate amd64 iso burned to CD-R. A previous installation of 8.04.1 on this same hardware did not have the problem described below.


**Problem:** At first boot into the new system, Network Manager shows the network to be "disconnected". Attempting to connect to web servers on the Internet using firefox 3.0.4 gives a "Page Load Error" with the error message "Address Not Found".

Ifconfig and route -a show that the interface is configured and the default route is active. ping via IP address to the default gateway works.

Name server information is missing from /etc/resolv.conf.

**My Solution:** Enter name server information into /etc/resolv.conf manually, or install package resolvconf. 

Regards and thanks to the developers of Debian, GNOME and Ubuntu for all the hard work,
C David Rigby

---

