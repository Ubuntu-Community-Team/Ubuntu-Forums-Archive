---
title: "pptpd masquerading"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by NGnewb on 2011-04-11
I'll preface this post with, "yes, I'm a linux newbie"
I've been trying to get my VPN working the way I want, but to no avail, I cannot seem to get the masquerading to work. I can connect to my VPN server from outside the network and access my shared drives and ping other computers on the LAN, but I can't get anything outside the LAN. I have the client set to pull all traffic through VPN, and the same configuration works fine on the same server while it's booted into Windows Server 2003, but I'm trying to get away from Windows for multiple reasons. I'm sure there's some simple step I'm missing here. I followed this tutorial: [http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html") Is there something else that needs to be done with iptables? I tried adding my gateway as DNS, and my ISP's DNS to the 'pptpd-options' file, but no dice. I can ping google.com for instance from the server, but not over the VPN connection, not even with google's IP address. I get nothing outside of the LAN.

Current setup is single NIC (is this the problem?) I'm running Ubuntu Server 10.04 basic system, and all that's running on the server is pptpd, and openssh. Do I need bind running on it? I don't think it matters but just in case, the Client computer is a MacBook Pro running OSX 10.6 (Snow Leopard). 

Any help would be greatly appreciated.

---

