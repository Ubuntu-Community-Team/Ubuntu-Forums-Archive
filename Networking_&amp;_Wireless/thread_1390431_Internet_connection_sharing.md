---
title: "Internet connection sharing"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by hansonlee on 2010-01-25
I am setting up a network such that the ubuntu (9.04) box is the gateway for the local network consisting of 4 xp machines.

The two network cards are setup properly (static ip's) and I can connect to the internet and ping all the 4 xp machines. All xp machines are able to ping the ubuntu box as well. However, when I used firestarter and click on the internet connection sharing, I was still unable to connect to internet from any of the xp machines. I tried editing iptables following this [post]("http://ubuntuforums.org/showthread.php?t=91370") but that didn't work, either. I am not very fluent with Linux so I am not sure where to start debugging. 

The local network configuration of the ubuntu is: 
IP: 192.168.0.1
Mask: 255.255.255.0
Gateway: 192.168.0.1

For the xp machines, they are:
IP: 192.168.0.2~5
Mask: 255.255.255.0
Gateway: 192.168.0.1
DNS: 192.168.0.1

Thanks for any help!

---

### Post by Iowan on 2010-01-25
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for Internet/connection sharing.

---

