---
title: "Change hosts file by network connection?"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by embolalia1187 on 2010-08-18
Is it possible to have different /etc/hosts file for different network connections without having to go in and change it every time?

The why: I have dyndns and port forwarding to get to my desktop. My laptop is sometimes on the same network, and sometimes not. Also, sometimes the dyndns doesn't update properly, or the outside connection is down, but I want to get to my desktop (and I'm too lazy to walk up the stairs). I'd like to be able to keep one set of bookmarks, ssh command aliases, etc. that would always get to it the fastest and most reliable way possible.

Is this possible?

---

### Post by embolalia1187 on 2010-08-19
Bamp. Found this: [http://www.sysadminsjourney.com/content/2008/12/18/use-networkmanager-launch-scripts-based-network-location]("http://www.sysadminsjourney.com/content/2008/12/18/use-networkmanager-launch-scripts-based-network-location")
So I need to place a script in /etc/NetworkManager/dispatcher.d that will figure out if I'm at home (or another network where I would know the desktop's IP), and change the hosts file accordingly.
Some semi-pseudocode:
```
if [ OnHomeNetwork ]; then
	#Use special host file
	echo "mydomain.homelinux.org	192.168.1.200" > /etc/hosts
else
	#Use the normal host file
	cp /etc/hosts.bak /etc/hosts
fi
```
So now the question is, how do I make the shell script know that I'm on my home network?

---

### Post by embolalia1187 on 2010-08-19
I got it! Solution below. It isn't perfect; if I'm ever in range of my home network and not connected to it (probably not going to happen), it'll give me a bad host. But other than that, this should work:

```
wifi=`iwlist wlan0 scan|grep SSID`
if [[ $wifi == *MiWiFi* ]]
then
	#Use special host file
	echo "mydomain.homelinux.org    192.168.1.200" >> /etc/hosts
else
	#Use the normal host file
	cp /etc/hosts.bak /etc/hosts
fi
```
Just replace MiWiFi with my wireless network SSID, and replace mydomain.homelinux.org with my hostname, then put it in /etc/NetworkManager/dispatcher.d and I'm good! I'm hoping the NetworkManager scripts run as root, otherwise it won't work...

---

