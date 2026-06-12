---
title: "Help seting up DHCP server, Bridging, NAS and Samba"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Red Kelly on 2011-01-28
Hello I have been trying for the last few weeks to set up my network but don't see to be getting anywhere. 
This is what I'd like:
[IMG]http://img638.imageshack.us/img638/3821/networklayout.jpg[/IMG]
I can get Internet on the server but cant work out how to bridge the connection and setup a dhcp server out of eth1. I have installed dhcp3-server and bridge-utils but can't seem to configure them right.

The modem uses IP 10.0.0.1 and gateway 10.0.0.138 I'd like to leave the modem settings alone if possible.

I don't care what the network IP addresses are but I thought it might be easier to see the difference if they were 192.168.0.0

I am using 10.10 64bit desktop edition for the server/desktop

The laptop has Ubuntu 10.10 and win7 duel boot (Not really worried about getting windows working)
HTPC is XBMC Freak on an Asrock ion 330.
The desktop is broken at the moment. (ram packed it in) will be running a version of ubuntu at some stage (need funds for more ram).

Any help would be greatly appreciated. I know there are lots of tutorials out there I just can't find one that explains what I wont to do in easy to understand terms and is up-to-date.

---

### Post by NeoGreen on 2011-01-29
Here's a really good tutorial you can use to help you:  [dhcp-server-in-ubuntu-server]("http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html")

---

### Post by Red Kelly on 2011-01-29
thanks neogreen now it is giving out ip addresses. just need to find out how to share internet connection and files.

Found another problem tho when both connections are connected, the internet drops out and as soon as I disable eth1 (home network side) it comes back. I hope this will be fixed with internet sharing. 
I have found [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") tutorial for it will report back once done.

---

### Post by Red Kelly on 2011-01-29
OK going backwards now. It stopped giving out ip addresses. Got to find out how to undo what I just did.

---

