---
title: "How do I name the computers on my lan?"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by s|k on 2006-05-16
My router software shows them as 'unknown.' Is that a DHCP setting I need to change? One computer is Ubuntu Dapper, the other Ubuntu Breezy Server, and the other one is Slackware. 

Thanks!

---

### Post by Dr. Nick on 2006-05-16
[quote=s|k]My router software shows them as 'unknown.' Is that a DHCP setting I need to change? One computer is Ubuntu Dapper, the other Ubuntu Breezy Server, and the other one is Slackware. 

Thanks![/quote]

Open the file /etc/hostname to change it. Gnome and KDE also have ways to graphically change teh hostname, most likely in a network control panel

---

### Post by nanotube on 2006-05-17
if you are talking about the name showing up in your router status, that is not part of the /etc/hostname stuff. that is part of the dhcp protocol, and you have to tell your dhclient to send the hostname to the router, when requesting an ip address. so what you need to do is edit the file /etc/dhcp3/dhclient.conf (as root, of course, so use sudo) and look for the line that looks like:
```
#send host-name "andare.fugue.com";
```
uncomment it, and put in whatever hostname you want dhclient to send to the router. so make the line look like, for example:
```
send host-name "myfunkycomputer";
```
and that should make it appear in the dhcp status in your router.

---

### Post by NeoGreen on 2006-05-26
Coool, it worked thanks.:)

---

### Post by isellapples on 2008-06-05
a semicolon!! thats why changing it wouldnt work, lol even though its been here for 2 years, its still helping :)

---

