---
title: "Ad-Hoc Internet Connection Sharing in Ubuntu??"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by max.a.hartman on 2009-10-04
Hi guys! BRAND NEW to Ubuntu and first time posting on a forum in my life. I'm trying to do something using Ubuntu 9.04 that was relatively easy to do in windows XP...

I live in sort of a remote location and I don't have a wireless router. So, I have a wired internet connection to my desktop, which also has a wireless PCI adapter. I would like to have the Ubuntu desktop broadcast a wireless network which shares the wired connection. The wireless adapter works well in Ubuntu and can connect to other wireless networks, and my wired adapter works well also.

Every time I've tried to set up the ad-hoc, no other computers can connect to the new network Ubuntu creates. There are a lot of options to choose from when setting up the network, and I don't know what many of them mean. I've tried researching this topic here and elsewhere but I haven't found anything that helps. I've always thought I was pretty good with computers, but I can't even get the ad-hoc to work, let alone ICS! Any help would be super super appreciated.

Thanks!

---

### Post by Iowan on 2009-10-04
Have you seen [this]("https://help.ubuntu.com/community/WifiDocs/Adhoc") help page?

---

### Post by max.a.hartman on 2009-10-04
Yeah, that sort of locus of tutorials was some of the first stuff I looked at, especially the very detailed one at [http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html) . My computers still don't connect. Also, I have no idea what some of the things they talk about are, such as "the dnsmasq package".

Thanks!

---

### Post by Iowan on 2009-10-04
I use **dnsmasq** for my network DNS and DHCP server.  It has the added advantage of tying the two together, so clients tthat get DHCP address can be accessed by hostname - rather than just IP address. My network is wired, though... I haven't tried ad hoc wireless networking.

---

### Post by max.a.hartman on 2009-10-04
So, I don't know what **dnsmasq** is, let alone how to use it. I don't even know what a DNS server is. I know that a DHCP server assigns IP addresses to other computers on the network... However, I don't think I want the ubuntu machine doing that because the IP adresses need to be assigned by the wired router behind the ubuntu machine, right?? I also don't know what you mean by "hostname".

Any help would be greatly appreciated.

Thanks!

---

### Post by sloggerkhan on 2009-10-04
And ad-hoc wireless network is easy to create. If you edit connections in your network manager applet, you can create a wireless ad-hoc network shared to other computers through the gui.

---

### Post by nishant.singh28 on 2009-11-09
and what if the other device is a smartphone...i mean if i want to share my lan based net connection with my friend's sony P1i phone via wifi????

---

### Post by sloggerkhan on 2009-11-09
Wifi is wifi.

---

### Post by nishant.singh28 on 2009-11-09
> **sloggerkhan said:**
> Wifi is wifi.
Thanks for the correction sir...noow once we are all set, what if I want to share an internet connection over "wireless" with my friend's sony p!i? I do not intend to use iwconfig as I want to have a clean option to switch between normal WiFi and the adhoc connectioon. The net connection to be shared is a college lan based one with a fixed ip and other settings,. Isn't there an easy way to do it like in Windows(don't think I'm gonna switch back to Vista for that :D) ?

---

### Post by sloggerkhan on 2009-11-10
right click on the connection manager > edit connections
wireless network > add >(mode  ad hoc, and IPV4 shared to other computers), tweak as needed.

---

### Post by nishant.singh28 on 2009-11-10
> **sloggerkhan said:**
> right click on the connection manager > edit connections
wireless network > add >(mode  ad hoc, and IPV4 shared to other computers), tweak as needed.
The other guy is unable to connect to the internet. The problem is I can't find a way to bridge the connections(net tutorials and how-to's don't work). Also, once disconnected, the adhoc network is not in the list of available Wireless Networks. And I don't want to keep my adapter in adhoc mode permanently

---

### Post by sloggerkhan on 2009-11-11
there are a lot of techniques and tutorials.

I don't have the hardware setup at the moment to trouble shoot a connection sharing issue.

---

