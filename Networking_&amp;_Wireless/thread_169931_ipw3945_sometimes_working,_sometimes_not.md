---
title: "ipw3945 sometimes working, sometimes not"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by apairon on 2006-05-03
Hello,

I have the notebook Sony Vaio SZ1VP with an Intel Pro/Wireless 3945. I use Dapper Drake Beta with a self compiled 2.6.16.11 kernel with

ieee80211 version 1.1.13 and ipw3945 version 1.0.2 with current microcode and daemon.

I am able to connect to a belkin ap with 54Mbit and it works perfectly. But connecting to a fritz!box wlan 7170 does not work. Using network-manager does not work at all. If I try to configure via iwconfig, i am able to set essid and wep key, but the connection ist lost after about 4 or 5 seconds and the LED is flashing (as it occures while scanning).

Looking into dmesg or syslog shows

ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

every 4 or 5 seconds. These seconds are not enough to get an ip via dhclient, but setting an IP manually. If the IP is set, I am able to ping another computer, but after these secconds the connection is lost and the LED is flashing.

I also tested with the WLAN-Router T-Sinus 130 DSL (11Mbit).
Connecting to that router is also very bad. network-manager does not work at all. Sometimes I'm able to connect if dbus and network-manager is shutdown and configuring via iwconfig. 
Dhclient sometimes gets an DHCPOFFER but thats all. The IP is not set. Setting the IP manually works, but I only get about 30% of all pings to another computer.
dmesg does not show anything.

All 3 routers or ap's have the same settings: 128bit WEB, MAC-filter has my MAC, DHCP.
Also disabling WEP has the same effect.

Why is the belkin working perfectly while the other 2 don't work.
Another notebook with an ipw2200 is working with all 3 ap's.


I hope anybody can help me. I searched google a thousend times with no results concerning my problem.

Thank you for your help

---

### Post by andydread on 2006-10-10
I have the same exact intermittent problem.

I have downloaded the latest version of the ipw driver 1.1.0 from 
ipw3945.sourceforge.net  and compiled.  This helped a little.  
I can connect with network manager more frequently now but still
sometimes i spend a whole hour trying to connect.  
Sometimes I am connected and leave the laptop for a few hours and come
back and its not connected and refuses to reconnect until  
several reboots.  this is really crazy because I have no problem with
this card connecting to the linksys in windows XP.
My router is a linksys wrt54gL with latest firmware configured for wep.

---

