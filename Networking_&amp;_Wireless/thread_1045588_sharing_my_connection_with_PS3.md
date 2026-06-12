---
title: "sharing my connection with PS3"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by C J on 2009-01-20
i have seen the light recently and installed ubuntu on my pc

but i want to delete windows for good hope ull guys will help me with this.

here is the situation

on my main system i have 2 NIC's which are properly installed.
eth0 is my onboard nic and the 1 that is connected to the internet

eth1 is a pci nic and is connected with my PS3 

this is all connected with wire

in XP it works so i assume there is no mistake in the setup.

thanx in advance..

---

### Post by Iowan on 2009-01-20
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page should be a good place to start.

---

### Post by C J on 2009-01-22
thanx for the respond.

but that didnt sort it our for me...

isnt there a user friendly way to do this using the 'edit connections' trough the connection symbol on the upper panel?

---

### Post by superprash2003 on 2009-01-22
firestarter has an ICS feature

---

### Post by C J on 2009-01-24
thanx for ur post

some how i cant get firestarter running(pressing the play button)

its says my eth1 isnt active

but it runs if i default all nic settings but cant share internet connection with it.

can some1 tell me if its possible  with the build in network manager??

after a while trying different settings i managed to receive an IP but at the internet connection test is gives a DNS error(i use the openDNS adresses, 208.67.222.222, 208.67.220.220) even though iv inputed the same DNS adresses in both my PC n PS3

any suggestions?

---

### Post by C J on 2009-01-28
bump

anyone??

---

### Post by Iowan on 2009-01-28
> **C J said:**
> 
can some1 tell me if its possible  with the build in network manager?? Not easily - Network Manager seems to control only one interface at a time.  One option mentioned was to remove NM, re-install the old manager (gnome-network-admin?), and use /etc/network/interfaces as before.

---

### Post by C J on 2009-01-31
what should i be typing in the network/interface??

both of my network cards?

can u show me an example (with dns and all)

thanx

---

### Post by C J on 2009-01-31
uugh this makes me sick iv been so busy trying to fix this issue and i 'accidentaly' came accross a site which explained so damn easy...

[http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml](http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml)


i finaly have my connection thanx guys!!

and goodbye windows!

---

