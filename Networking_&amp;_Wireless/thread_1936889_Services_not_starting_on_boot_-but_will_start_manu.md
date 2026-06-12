---
title: "Services not starting on boot -but will start manually"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by masuch on 2012-03-06
Hi,

Three days ago I have got into problem that some services did not start after boot/login. It was working for long time before. I have read a lot of posts and forums what helped to somebody but unfortunatelly none of them worked for me.

I would like to ask if can anybody who has oneric or later ubuntu desktop linux version with networking or network-manager services installed and does not have this problem could send me results of this commands:

chkconfig --list | grep -i netw
more /var/lib/NetworkManager/NetworkManager.state
sudo service networking status
sudo service network-manager status
runlevel

# --- my looks like:
	# network-interface         0:off  1:off  2:off  3:off  4:off  5:off  6:off
	# network-interface-security  0:off  1:off  2:off  3:off  4:off  5:off  6:off
	# network-manager           0:off  1:off  2:off  3:off  4:off  5:off  6:off
	# networking                0:on   1:off  2:off  3:off  4:off  5:off  6:off

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

networking stop/waiting
network-manager start/running, process 1998


Thank You,
Kind Regards,
Martin

---

### Post by masuch on 2012-03-12
Could please anyone share information of following commands or is it confidential information ?

chkconfig --list | grep -i netw
more /var/lib/NetworkManager/NetworkManager.state
sudo service networking status
sudo service network-manager status
runlevel

Thank You,
Kind Regards,
Martin

---

