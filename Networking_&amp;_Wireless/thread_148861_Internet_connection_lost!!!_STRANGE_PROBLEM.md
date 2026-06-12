---
title: "Internet connection lost!!! STRANGE PROBLEM"
date: 2006-03-22
forum: Networking &amp; Wireless
---

### Post by glazzi on 2006-03-22
A few days ago I my connection stopped working... I connect to internet thru a cablemodem connected to my ethernet card in eth0 by DHCP, and I share it with other two computers by eth1 and 2...

When my pc boots, i get random ip from eth 0, 169.xxx.xxx.xxx, but if type "sudo dhclient eth0" i get IP, but still no connection and if try to ping any host, i get "operation not permitted", even with sudo...

Some other clues!... if i boot with debugger mode, i can ping internet directions and my router, but as soon as i boot, all is gone. I also noticed that when the system is starting, appears a message like this: Net.Ipv4.ip-forward caused and invalid argument...

well any advices are welcomed

---

### Post by jml on 2006-03-22
A little more information could help.  What version of Ubuntu are you using?  As to your setup.  Am I correct in assuming that your computer is directly connected to the cable modem through one ethernet card and the two other computers connect to the modem by connecting to your computer first through two other ethernet cards?  In other words do you have three ethernet cards (NICS) in your computer?

Just a few general suggestions.  If you haven't already done so, try power cycling your modem (unplug it from the mains for about ten seconds then plug it back in.)  Then see if the problem is corrected.  Second question, has anything changed in your system or the other computers between the time the system worked and when it stopped working?  A final suggestion.  If you have access to an inexpensive router like the Linksys BEFSR41, try connecting the modem to it, and then connect each computer to the router.  Thatway, your main computer does not have to remain on alll the time, the connection might be more stable, and the router does a pretty good job of being a simple hardware firewall.

Joe

---

### Post by glazzi on 2006-03-22
I am using 5.10, and you are assuming well, i have three ethernet cards in my pc. i cycled the modem several times and i also disconnected the other networks. I reboot several times also, and no, the problem is still there. And for the last suggestion, i live in Argentina, where computer stuff is really expensive, so i can't get a router easily...

if any other information can help, i will post it !!!

---

### Post by glazzi on 2006-03-23
Any ideas??? there is not a way to reset the net configuration to the first minute after installation??? i 'd be happy with that!

---

### Post by mips on 2006-03-23
Try disabling IPv6.
Try a static IP config.

Post all your config files here, interfaces/resolve.conf/dhcp etc.

---

