---
title: "Internet problem on Ubuntu"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by mailord on 2009-05-21
Hello all,
 
i have a problem with my internet. Ubuntu can connect with my router. ( i have wireless). So.. He connect but i cant do anything with it. I cant do things on firefox or anything. I have a connection but i cant do anything with it....Knows anybady what it can be?
 
,Mailord

---

### Post by x22 on 2009-05-21
welcome to the forum

here's some stuff to try:

ping google.com--if nothing, you have no connection

dhclient <interface>--should get an IP address; if not

ifconfig <interface> up--bring up the interface

what I use as initialization script is this:

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0

---

### Post by superprash2003 on 2009-05-21
in your terminal type ifconfig and post ouptput.. also post output of iwconfig

---

