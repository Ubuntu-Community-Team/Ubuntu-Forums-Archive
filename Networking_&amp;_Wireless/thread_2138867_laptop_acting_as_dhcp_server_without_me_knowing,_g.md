---
title: "laptop acting as dhcp server without me knowing, got me in some trouble."
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by benj23673 on 2013-04-25
[COLOR=#000000]Let me tell you the ITdesk at my university was angry I was messing up all the wireless network traffic during finals week at the library. [/COLOR][COLOR=#000000]They said I was DCHPing on their network, and my computer was giving out IP addresses, they wouldn't explain anything else to me? They commented out dnsmasq in network manager and said that was the issue? [/COLOR][COLOR=#000000]I have ubuntu 12.10 but I am using wicd and I have purged network manager because they said that was part of the issue. I have a Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter.[/COLOR][COLOR=#000000] If anyone has some more insight on this issue I would love to know more about what was going on and how/why a university's wireless network couldn't stop this?[/COLOR]

---

### Post by tgalati4 on 2013-04-25
I'm running Linux Mint 14 Mate (based on 12.10) and I don't have dnsmasq installed.  But:

tgalati4@Mint14-Extensa ~ $ apt-cache search dnsmasq
dnsmasq-base - Small caching DNS proxy and DHCP/TFTP server
dnsmasq-utils - Utilities for manipulating DHCP leases
dnsmasq - Small caching DNS proxy and DHCP/TFTP server

So it is possible that you were handing out DHCP addresses over your wireless connection.  And that would create a problem.  I haven't used dnsmasq, so I can't comment on how it works.  But network-manager has dnsmasq-base as a dependency and wicd does not.  Depending on how dnsmasq works, it might appear to be interfering with DHCP--or--more likely, the busy network was causing dnsmasq to go crazy and your University's IT department discovered that your Linux machine was the foreign invader.  I'm sorry that I can't provide any more insight than that.

---

### Post by benj23673 on 2013-04-25
How can such a large scale wireless network let something like this go on?

---

### Post by cmacia06 on 2013-04-25
Usually university networks are password protected or require a log in so that a random person cant just log on and host things like that. The university almost always has a rule against hosting a server on their network so they assume that their students/teachers wont interfere.

---

### Post by lykwydchykyn on 2013-04-25
As I explained in the other thread, Ubuntu has dnsmasq installed by default as a DNS resolver (I said cacher in that thread, but that's maybe not so accurate).  As I understand it, only a small part of dnsmasq is actually installed, however the full dnsmasq package is capable of doing dhcp (it's often used forDNS/DHCP services on small office/home LANs).

Unless you were tinkering with dnsmasq at some point, I don't see how it suddenly could have turned into a DHCP server.  Even if you install the full dnsmasq package, I'm fairly certain DHCP is turned off by default.  Is there an /etc/dnsmasq.conf file on your system?

---

