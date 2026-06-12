---
title: "aa1 ethernet not working?"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by katoiam on 2009-10-23
Hi im new to linux and ubuntu,
        I have a Acer Aspire One I have installed UNR, I have been using it for about a month and have had no problems with my wifi. How ever I have just returned to my folks place and they have no wifi, I tried to use there ethernet cable to get the internet connection and it wont work!!! Please can some one help me?
thank you 
kate

---

### Post by katoiam on 2009-10-23
can any one help me, or has any one had a similar problem?
:guitar:

---

### Post by Sylslay on 2009-10-23
try run command in terminal
sudo ifup wlan0 // for wifi
sudo ifdown / ifup eth0 // for cable connection

sudo ifconfig , see names for network boards. like , eth0, wlan0, ra0,,,ra1

, I don't know what went wrong, but it's working. Apparently I had to add it as a wireless interface edit in /etc/network/interfaces :

Code:

auto ra0
iface ra0 inet dhcp
wireless-essid "home"
wireless-key "wep"

or 

auto wlan0
iface wlan0 inet dhcp
wireless-essid home
wireless-key 

Grapic way: 

nm-applets

---

### Post by katoiam on 2009-10-23
i am a bit confused as to what you suggesting! are you saying input:
sudo ifdown / ifup eth0
or
sudo ifdown eth0  
and then: 
sudo ifup eth0

thanx for replying

---

### Post by katoiam on 2009-10-28
so.....it doesnt seem to work the command:
sudo ifdown eth0 it replies:
ifdown: eth0 not configured
then when i do :
sudo ifup eth0 it replies:
ignoring unknown interface eth0=eth0

---

### Post by katoiam on 2009-10-30
bump
can any one help? please

---

