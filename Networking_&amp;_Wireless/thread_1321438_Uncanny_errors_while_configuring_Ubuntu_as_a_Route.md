---
title: "Uncanny errors while configuring Ubuntu as a Router"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Shaketbaby on 2009-11-10
Recently, I am trying to set up a router box using Ubuntu. I am totally a newbie to Linux and thanks for
the great work done by the Linux/Debian/Ubuntu community, I managed to install the system without much trouble. But I also ran into some issues that has bugged me for the last few days.
 
Here's the relative hardware and software env:
CPU: Atom N270
OS: Ubuntu 9.10 - using linux-i386-2.6.31-14 kernel
WirelessCard: Atheros AR5418 802.11abgn, driver is ath9k
Hostapd + mac80211, the wireless interface is wlan0 and is not included in a bridge.
DNS server is dnsmasq.
Client is two Windows 7, one with Intel 5100 AGN and the other is ThinkPad X200 with a 802.11b/g card using Atheros chip.
I configured the hostapd with 802.11n support, using wpa-psk authentication, pretty much just followed 
this page [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)
Ok, here's the problem:
At first, the client can connect to AP smoothly, can ping AP, but after a few minutes, unable to ping AP any more. Or if manually disconnect wireless connection and reconnect, can connect to AP but can't get IP from DHCP. Looking at the syslog, dnsmasq has recieved the DHCPDISCOVER sent from client and replied with DHCPOFFER, but the client keeps sending DHCPDISCOVER, seems like it can't receive the DHCPOFFER message. When I restart hostapd, everything becomes fine. And if I disconnect then problem comes again.
 
Does anyone know the reasons?
Thanks a lot!

---

### Post by acranox on 2010-03-22
I've got the same problem.  Did you ever figure it out?  I've got almost the same hardware too.

---

