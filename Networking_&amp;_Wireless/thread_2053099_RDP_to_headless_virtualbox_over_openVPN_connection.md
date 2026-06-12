---
title: "RDP to headless virtualbox over openVPN connection."
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by mythms on 2012-09-04
I have Windows XP Pro running in a headless virtualbox on Ubuntu 12.04.  This virtual machine is accessible via rdp from my office LAN (10.10.10.0) at 10.10.10.49:3389.  

At home, my network is 192.168.2.0.  On this network I have Slackware(10?) box.  I have a vpn established between 10.10.10.49 (server) and 192.168.2.18 (client) and am able to ssh from client to server.

I would like to RDP connect from a third machine(192.168.2.103,winxp) on my home network to the headless virtualbox (10.10.10.49) on my office network using the  10.10.10.49<->192.168.2.18 vpn connection.  

I understand that I could make a vpn client connection from 192.168.2.103 and accomplish this but I don't want to do it that way.  I set up the 10.10.10.49<->192.168.2.18 vpn connection for the purpose of making rsync backups.  This connection will be left up all of the time.  Besides, there are several other nodes on the 192.168.2.0 side that I might want to rdp into the 10.10.10.49 virtual machine from.  

Can anyone direct me to a simple way to accomplishing this routing and have it come up automatically after reboot?

Thanks in advance.

---

