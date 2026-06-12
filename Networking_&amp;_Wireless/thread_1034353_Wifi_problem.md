---
title: "Wifi problem"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by kawakaze on 2009-01-08
Hi guys, im not sure to put this in the new user or in here. Im having major headaches getting my wifi up and running.

The problem started with my laptop wifi card having a closed source driver. I noticed ubuntu users on the debian forum didnt have this problem. So I switched to ubuntu to try it out. The network card is now working so far as I can see. It lists my wifi router as well as two of my neighbours routers too.

When I try to connect to my own router it gives back no response. I've even tried unsecuring the router and connecting without a password. The neighbours routers however prompt a request for a key. When I look in the network icon in the top right of the desktop the signal strength bars of my neighbours routers are moving, where my routers signal bar isnt

My router also refuse to support any hardware such as a linksys router i tried to use with it. My isp for some reason disabled this, and the router they sent me is garbage with about a 2metre range. II thought this had something to do with it. But my desktop runs OpenSuse and XP, I've had no trouble at all with that, but that has a normal wifi card with an open source driver.

If you noticed, ive gone through many many linux distros in the past few weeks. Its better than windows in my opinion, but I've yet to find a  distro that was 100% trouble free :D

Ill try to give as much information about the hardware now--

Laptop Acer 5220
Sitecom BCM9311MCG mini wlan 
(lspci lists it as 04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01))
Davolink router DV201AM 

claudia@claudia-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-01-08
post output of iwlist scanning

---

