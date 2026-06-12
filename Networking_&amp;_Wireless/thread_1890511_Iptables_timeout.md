---
title: "Iptables timeout"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by sjoeff on 2011-12-03
Hi all,
 
I have 2 firewalls, one with iptables ubuntu 10.10 and another with ubuntu 11.10. 
 
Both are in different locations. 
When I am using the same IPtables configuration on both locations. The ubuntu server 11.10 is causing timeouts for the nat clients. This only happens when downloading big files or streaming 1080p on youtube. 
 
I have searched on google and found something about a bug with tcp timouts when upgrading iptables.
Here: [[FONT=Tahoma]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/791512[/FONT]]("https://mail.eehm.nl/OWA/redir.aspx?C=8bf62a71f2f04f83970606de91c35f5c&URL=https%3a%2f%2fbugs.launchpad.net%2fubuntu%2f%2bsource%2flinux%2f%2bbug%2f791512")
Maybe this is the problem? 
 
It is very annoying when downloading a large iso boom after a while timeout and then you need to restart the download.

---

